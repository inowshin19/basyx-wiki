
[Back: System Components](system_components.md) | [Next: Recursive Validation](recursive_validation.md) | [Back to Getting Started](../getting_started/getting_started.md)

#  Validation Logic

The Test Orchestrator validates submodels in three main steps:

---

## 1. Event-Driven Submodel Processing

The `MqttSubscriber` listens for submodel creation, update, and deletion events:

```java
client.subscribe(TOPIC_NEW);
client.subscribe(TOPIC_UPDATE);
client.subscribe(TOPIC_DELETE);
```

**On creation/update:**
- Deserializes the submodel
- Checks the AASX version
- Validates presence of `SemanticId`

**On deletion:**
- Cleans up related test results in the repository

---

## 2. Validation Logic

### 🔁 Validation Sequence

The validation process is illustrated in the sequence diagram below, showing the interactions between the Submodel Repository, Deserializer, Comparator, Recursion Function, SMEComparator, and MQTT/Web UI interface.

![Validation Sequence](./images/ValidationSequence.png)

---

###  Deserialization

Parses all input submodels and templates using IDTA-compatible JSON:

```java
Environment inputEnv = Deserializer.deserializejsonFile(jsonString);
```

---

###  Comparison Logic

Each input submodel is compared to schema submodels by matching `SemanticId`:

```java
ComparisonResult result = Comparator.compare(schemaSubmodel, inputSubmodel);
```

---

###  Recursive Validation

Main logic for comparing submodel elements recursively:

```java
RecursionFunc.compareSubmodelElements(
    schemaSubmodel.getSubmodelElements(),
    inputSubmodel.getSubmodelElements(),
    result
);
```
This function:
- Checks multiplicity (One, ZeroToOne, etc.)
- Verifies qualifiers (required/optional)
- Compares type, value, and semanticId
- Recurses into nested `SubmodelElementCollection`s


Recursive validation ensures structural and semantic correctness of nested SubmodelElementCollections.

- Validates multiplicity constraints (`One`, `ZeroToOne`, `OneToMany`, `ZeroToMany`).
- Checks qualifiers (required vs optional).
- Matches `SemanticId`, `idShort`, type, and value.
- Recurses into nested collections until the full hierarchy is validated.
---

###  Multiplicity Check Example

```java
if ("One".equals(multiplicity)) {
    SMEComparator.checkMultiplicityOne(schemaElement, inputElementMap, result);
}
```

All four multiplicity types are supported:
- `One`
- `ZeroToOne`
- `OneToMany`
- `ZeroToMany`

---

## 3. Test Results & Reporting

All validation results are written as Submodels in the repository:

```java
ResultSubmodelFactory.addResultToSubmodel(comparisonResult, inputSubmodel);
```

**Example JSON output:**

```json
{
  "ComparedSubmodelId": "...",
  "SemanticId": "...",
  "Errors": "...",
  "Warnings": "...",
  "Differences": "...",
  "Infos": "..."
}
```

---

##  Handling Edge Cases

### Unsupported AASX Versions

```java
ResultSubmodelFactory.addUnsupportedVersionResult(rawJson);
```

### Missing SemanticId

```java
if (submodel.getSemanticId() == null) {
    ResultSubmodelFactory.addUnsuccessfulResultToSubmodel(submodel);
    return;
}
```

---

##  Full Comparison Function Example

```java
public static ComparisonResult compare(Submodel schemaSubmodel, Submodel inputSubmodel) {
    ComparisonResult result = new ComparisonResult();
    RecursionFunc.compareSubmodelElements(
        schemaSubmodel.getSubmodelElements(),
        inputSubmodel.getSubmodelElements(),
        result
    );
    return result;
}
```

---

##  Handling New Submodel Event

```java
private void processSubmodel(String submodelJson) {
    if (!isAASXv3Format(submodelJson)) {
        ResultSubmodelFactory.addUnsupportedVersionResult(submodelJson);
        return;
    }

    Submodel submodel = deserializer.read(submodelJson, Submodel.class);

    if (submodel.getSemanticId() == null) {
        ResultSubmodelFactory.addUnsuccessfulResultToSubmodel(submodel);
        return;
    }

    SubmodelFactory.processReceivedSubmodel(submodel);
}
```

---

[Back: System Components](system_components.md)  | [Back to Getting Started](../getting_started/getting_started.md)
