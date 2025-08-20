[Back to Overview](index.md) | [Next: Recursive Validation](recursive_validation.md)

---

# System Components

The Test Orchestrator is composed of modular components, each handling a specific part of the validation pipeline.

## 🔑 Core Modules

- **Deserializer**  
  Parses JSON input and schema files into AAS model objects. Ensures version compatibility (AASX v3).

- **Comparator**  
  Selects the right schema via `SemanticId` and coordinates the validation process.

- **RecursionFunc**  
  Implements recursive validation of nested SubmodelElementCollections.

- **SMEComparator**  
  Applies multiplicity rules (`One`, `ZeroToOne`, `OneToMany`, `ZeroToMany`) and qualifier checks.

- **ComparisonResult**  
  Collects errors, warnings, differences, and info messages into a standardized format.

- **ResultSubmodelFactory**  
  Creates new result Submodels for reporting, including unsupported version or missing `SemanticId` cases.

---

## 🖼 Diagram

The figure below illustrates the orchestration of these components:

![System Architecture](../images/ClassDiagram.png)

---

[Back to Overview](index.md) | [Next: Recursive Validation](recursive_validation.md)
