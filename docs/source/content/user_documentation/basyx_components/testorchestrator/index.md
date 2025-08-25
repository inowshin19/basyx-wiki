<<<<<<< HEAD
# Test Orchestrator

Welcome to the documentation for the BaSyx Test Orchestrator.
This module provides automated validation for Asset Administration Shell (AAS) submodels.

- [Getting Started](getting_started.md)
- [Validation Logic](validation_logic.md)
- [Extending Validation](extending.md)
=======
# 📦 Test Orchestrator Documentation

<<<<<<< Updated upstream
Welcome to the documentation for the BaSyx Test Orchestrator.
This module provides automated validation for Asset Administration Shell (AAS) submodels.

- [Getting Started](./features/getting_started.md)
- [Example](./features/Example.md)
- [System Components](./features/concept/system_components.md)
- [Validation Logic](./features/concept/validation_logic.md)
- [Recursive Validation](./features/concept/recursive_validation.md)
- [Extending Validation](./features/feature/extending.md)
- [Results Visualization](./features/Visualization.md)
- [MongoDB Integration](./features/feature/mongodbintegration.md)
- Semantic Validation:
    - [ECLASS](./features/feature/SemanticValidation/ECLASS.md)
    - [Generative AI](./features/feature/SemanticValidation/GenerativeAI.md)
>>>>>>> testorchestrator-clean
- [References](#references)

See also: [BaSyx Submodel Repository](../submodel_repository/index.md)

<<<<<<< HEAD
=======
```{toctree}
:hidden:
:maxdepth: 1

features/getting_started
features/Example
features/concept/index
features/feature/index
```
>>>>>>> testorchestrator-clean
## Overview

The Test Orchestrator is a Spring Boot-based extension for validating Asset Administration Shell (AAS) submodels according to IDTA/Industry standards.

It provides:
- Automated structural and semantic validation
- Integration with MQTT for real-time submodel event monitoring
- Result reporting via standardized submodels
- Support for extensible schemas and rule sets
<<<<<<< HEAD

---

## Architecture

The Test Orchestrator integrates with the BaSyx Submodel Repository and listens for submodel creation, update, and deletion events via MQTT.
![Test Orchestrator Architecture](./images/archeticture.png)
---

## References
=======
=======
Welcome to the documentation for the **BaSyx Test Orchestrator**.  
This module provides automated structural and semantic validation for Asset Administration Shell (AAS) Submodels.
>>>>>>> Stashed changes

---

## 📖 Documentation Structure

### 🚀 1. [Getting Started](getting_started.md)
Learn how to install, configure, and launch the Test Orchestrator.

### 🧱 2. [System Components](system_components.md)
Overview of the architecture and the key components involved in the validation process.

### 🔁 3. [Validation Logic](validation_logic.md)
Explore the validation flow, including deserialization, recursive comparison, and rule application.

### 🔍 4. [Recursive Validation](recursive_validation.md)
Detailed explanation of how nested SubmodelElementCollections are handled.

### 📊 5. [Results Visualization](results_visualization.md)
Learn how validation results are generated, stored, and viewed via the BaSyx UI.

### 🧩 6. [Extending Validation](features/extending.md)
How to add new schema templates or implement custom validation logic.

### 💾 7. [MongoDB Integration](features/mongodbintegration.md)
Optional feature for storing validation logs and results in MongoDB.

<<<<<<< Updated upstream
The Test Orchestrator integrates with the BaSyx Submodel Repository and listens for submodel creation, update, and deletion events via MQTT.

```{figure} ./images/architecture.png
---
width: 100%
alt: architecture
name: architecture
---
```

=======
>>>>>>> Stashed changes
---

## 🔗 Related Modules

- [BaSyx Submodel Repository](../submodel_repository/index.md)
- [AAS Web UI](../web_ui/index.md)

---

## 📚 References
>>>>>>> testorchestrator-clean

- [IDTA Submodel Templates](https://github.com/admin-shell-io/submodel-templates)
- [Eclipse BaSyx Documentation](https://wiki.basyx.org/en/latest/)
- [AASX Package Explorer](https://github.com/admin-shell-io/aasx-package-explorer)

<<<<<<< HEAD
[Next: Getting Started](getting_started.md)
=======
---
>>>>>>> testorchestrator-clean
