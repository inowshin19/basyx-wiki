[Back to Overview](index.md) | [Next: System Components](system_components.md)

## Testing Options

You can directly start using test orchestrator and validate your submodel(s). For doing that, navigate to [Test Orchestrator Example](https://github.com/eclipse-basyx/basyx-applications/tree/main/test-orchestrator/example).

### 1. Test by Uploading Files

#### Standard Submodel Validation
Upload a valid AAS or submodel JSON file via the web interface.
The system will automatically validate all submodels contained in the uploaded AAS. 

![Test_Orchestrator_Upload](./images/Test_Orchestrator_Upload.png)


#### Custom Submodel Validation
For validating custom created submodels that are different than the standardized submodels from [IDTA](https://smt-repo.admin-shell-io.com/), the user needs to keep the json file of the submodel in the folder `external-schemas`. When a file is uploaded, the reference submodel against which the uploaded submodel will be tested are serached from the IDTA submodel. If the Semantic ID of the uploaded submodel does not match any standardized submodels from IDTA then this `external-schemas` folder is searched to find the reference custom submodel. 

![external-schema](./images/external-schema.PNG)


### 2. Test Using JSON Input

#### Standard Submodel Validation

- To validate your submodel against an IDTA-registered standard, provide the JSON input of the AAS or standalone submodel in the aasFile field.

#### Custom Submodel Validation
To validate against a custom reference:

- Copy and paste your submodel in JSON format in the aasFile field.
- Copy and paste the reference submodel JSON in the customAASFile field.
- Click the Execute button.

![Json Test](./Test_Orchestrator_JSON.PNG)

---

### 3. Test Using API Links

#### Standard Submodel Validation
- Provide the API endpoint of your AAS or standalone submodel in the inputAASLink field.

#### Custom Submodel Validation
- Provide the API URL of the submodel you want to test in the inputAASLink field.
- Provide the API URL of the reference submodel in the customAASLink field.
- Click the Execute button.


![Test_Orchestrator_API](./images/Test_Orchestrator_API.png)


All the test results are visualized in the [Test Orchestrator Module](results_visualization.md).
[Back to Overview](index.md) | [Next: System Components](../system_components.md)