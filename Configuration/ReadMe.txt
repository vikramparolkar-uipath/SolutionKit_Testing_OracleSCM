ORCHESTRATOR SET-UP
1) Create Asset (Type: Credential) named 'Oracle SCM Credentials'. The persona needed in this automation is the Production Supervisor.
	Username: JENNA.SANCHEZ / Password: x6^Nrd9% 
	Note: The password changes frequently, reach out to @Vikram Parolkar for the latest (if needed)
2) Create Asset (Type: Text) named 'Oracle SCM URL'. This URL changes frequently, but you can try this: https://login-eseu-saasfademo1.ds-fa.oraclepdemos.com/oam/server/obrareq.cgi?encquery%3DG0Fj3HcRtPnDM9sIG7UY3VBVBywNiS4pZgE76CXUiiCjkC2dq23%2F9IJF88RanUse%2BqkwojVecWT9wsl%2F9RjytuHnnynQAwLc6idSrjOtcdeqm7J35pVSYkdUiXLSxAUjXk8023QG9oPZX921jPUsTQcVrc8gOerPhl1wUGAFow2dSk35suXpbr4nDc1D5yoEl%2FovpGX%2FcIkSdrGPqo6SuizNifYNuH4ZfUXycP%2B21MDrLjTmDzgV8XsDRqNE%2Bj%2BLmjLBY62KgKjVjcNs3JszAiEaL5Pf1C5rE6aVgcNqw7%2BK7eLvlN91GkFEanoJYH0BPBSeZjmIQ70Y1oTO4IRXB7pjMIrNTqGCd1reozzgL2NV8NJAXRex8dlRlwAOxmyMqhe6HdHzgM2RTMVp9c%2FCfs8aSLMgvyQlOCt1JqtCVk0p4cItqBr2kfe8r0pW%2FQto%20agentid%3DOraFusionApp_11AG%20ver%3D1%20crmethod%3D2%26cksum%3Dc4bdcec14075e5f51f069fca548052ff9efdeb43&ECID-Context=1.0066EIEN28XD%5EaTMyAnZ6G009Dyq0000GL%3BkXjE
3) Create Asset (Type: Text) named 'Oracle SCM Order Number'. Value is 'WO-002-1063'

DATA SERVICE SET-UP
1) Import 'Data Service Schema for Oracle SCM Solution Kit.json' into UiPath Data Service
2) Make sure to select both the Entity ("Oracle SCM - Work Order Data") and Choice Set ("Oracle SCM - Order Types")
3) Add the following data:
		- Order Type: Nonstandard
		- Item: AS47011
		- Transform Item: <leave blank>
		- Quantity: 3
		- Work Order Number: <leave blank> or WO-002-1062 (if sample needed)

STUDIO CONFIGURATION
Update default value of 'in_OrchestratorFolderPath' to the orchestrator folder where you defined Assets for the following workflows:
> Oracle_SCM_Login.xaml
> Oracle_SCM_Search_WorkOrder.xaml
> TC_CreateNonStandardError.xaml
> TC_CreateTransformWorkOrder.xaml

DATA DRIVEN TEST SET-UP
1) Confirm that "TC_CreateNonStandardOrder.xaml" has linked test data. Right-click the workflow and Update Test Data/ Add Test Data.
2) Linked Test Data should be the Data Service entity 'OracleSCMWorkOrderData'
3) Click the Filter icon and set the filter to be 'OrderType' filed = 0