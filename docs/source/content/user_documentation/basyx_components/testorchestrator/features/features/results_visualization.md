[Next: Extending Validation](features/extending.md) | [Back to Getting Started](../getting_started/getting_started.md)



# Results Visualization
---
## Viewing Results

- Through the **BaSyx Submodel Repository API**
- Via the **BaSyx Web UI**, where categorized results are displayed
- As downloadable JSON files for further processing

![Filtered Validation Result View](../images/filteredResults.png)
*Figure: Example filtered view of validation results in the BaSyx UI*

---

All validation results are persisted in dedicated Submodels:

- **TestResults** – for successful validations
- **UnsuccessfulTestResults** – for failed or incomplete validations

---
## Result Structure

Each result contains:

```json
{
  "ComparedSubmodelId": "...",
  "SemanticId": "...",
  "Errors": "...",
  "Warnings": "...",
  "Differences": "...",
  "Infos": "..."
}



 [Back to Getting Started](../getting_started/getting_started.md) | [Next: Extending Validation](features/extending.md)

