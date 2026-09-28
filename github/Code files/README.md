# Code Files — Standard Laptop Procurement Automation

## About this folder

This project was implemented entirely on the **ServiceNow platform** using
**Flow Designer**, which is a low-code/no-code visual automation tool. The
automation logic (trigger + action + field mappings) was built by configuring
options in the Flow Designer UI — it was not written as a traditional
programming-language codebase (no JavaScript, Python, or similar application
source files were created for this project).

Because of this, there is no conventional `src/`, `package.json`, or compiled
application code to include here. Instead, this folder contains a structured
**configuration reference** for the flow that was built, which serves as the
closest equivalent to source code for a Flow Designer solution — it fully
describes the trigger, the action, and every field mapping used, so that the
flow could be reproduced or reviewed without needing direct access to the
ServiceNow instance.

## What to look at instead

| If you want to see... | Look here |
|---|---|
| The exact flow configuration (trigger, action, field values) | `flow_configuration_reference.md` (this folder) |
| Step-by-step build instructions with screenshots | `Phase wise Documents/Phase_1_Flow_Creation.pdf` |
| How the flow was attached to the catalog item | `Phase wise Documents/Phase_2_Flow_Assignment.pdf` |
| End-to-end testing and validation | `Phase wise Documents/Phase_3_Service_Catalog_Test_and_Validation.pdf` |
| Project background, problem statement, objective | `Project_Overview.docx` (repository root) |

## Platform and components used

- ServiceNow Flow Designer
- Service Catalog
- Requested Items
- Approvals
- Catalog Tasks
- Maintain Items / Process Engine configuration

No other frameworks, languages, APIs, or databases were used in this project.
