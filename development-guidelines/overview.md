---
layout: docs
title: 'Development guidelines'
group: development-guidelines
subgroup: overview
redirect_from:
  - "/development-guidelines/"
toc: true
---

## Basic guidelines

- To have only one model per implementation project. This will save you from unnecessary problems with model compatibility and dependencies in between.

- To have only one extension per application object. This will allow the developer to see and understand all customizations of the object.

- Do not have several developers on same one-box. Otherwise, you may face issues with source code controlling in Visual Studio.

- When a developer changes someone’s code, or relies on it in own code, then, in any case, he takes responsibility for the correct execution of the code.

- No basic/standard functionality can be limited with new customization/extension.

- Each extension/customization should be enframed with condition for checking if the new feature is enabled.

- Each customization should be checked with another developer for BP. See [Code review](/development-process/code-review/)

- To run something in batch and if it will not be consumed externally (with web-service calls etc.), it is simplier to implement it using the RunBaseBatch framework rather than SysOperations.

## Reintenting the wheel

Sometimes Developers implement solutions that should be reworked from scratch after development is finished. To prevent this, following solutions should signal to do additional checking from Technical Architect.

- Using _container_-type fields in tables.

- Storing list of values (separated with comma, etc.) in a single field/variable.

- Using any multi-value parameters (like _container_, _List_, _Set_, etc.) in RunBase-framework classes.

## Application objects guidelines

[Tables](/development-guidelines/application-objects/tables/)

[Macros](/development-guidelines/application-objects/macros/)


## Financial dimensions

- No 'Custom dimensions' allowed for implementation project.<br/>Each financial dimension should be implemented with own table (backed entity) and separate setup form.

- Each financial dimension attribute should mapped with 'Dimension attribute type' (base enum) value and therefore used in the code.
  Dimension attribute type is specified at creation of finencial dimension (_Dimension attribute_ table) and can't be changed.
  
## Comments

- As history of object changes is stored in source control system (repository), thus there is no strict rule to mark added code with additional comments (containing Work Item Id, Work Item name, Date and Developer alias etc.).

- It is prohibited to leave commented/not-executed code as well as previous version of the code.

- Developer could add comments which clarify code execution.
  
## UI guidelines

### Filtering and sorting

- By default, each field on the form should be available for filtering and sorting (if there is no explicit requrement to make it using _display_- or _edit_-methods)

- Unavailability of filtering/sorting for added field should be approved with Consultant.

### Column widths

- For any table/grid column should be able to change the width

### Fields moving

- For all fields in the tabular part of the form, the operation of moving to another place (changing the order of columns) should be available.

### Size/form position

- No operations that are directly related to changing the size and position of the forms should not change the size and position of the form.

- Form controls that allow their sizes to be changed must scale when the sizes of the forms change.

### Viewing details

- All fields with Foreigh Keys must allow to _View details_ (go to main table).

### Confirmation of irreversible actions

- Before performing all irreversible actions, it is required to ask the user for confirmation in the dialog.<br/>By default, the dialog should focus on the button that does not lead to irreversible actions.

### Interaction with user

- No basic UI functionality (filtering, sorting, exporting to Excel etc.) can be limited with new customization/extension.

- Any function of the should lead to some result. The result can be an any message of change in the interface (for example, opening a form). 

- It is forbidden to have any interaction with user, requires his answer, within the transaction.

- You should not use a chain of dialogs from several windows to confirm the action. If it is necessary to branch the algorithm, the choice of the branch of the algorithm should be indicated in the initial dialog box.


## External interfaces guidelines

- Any external interface should use only external codes for each mapped table.

Example:

```
1. Get value '0001200' as ExtProductId from CSV-file or web-request
2. Get ExtCodeId from interface setup
3. Use ExtProductId and ExtCodeId to find external code value (int ExtCodeValueTable) related with product (EcoResProduct) record.
4. Use founded product record to further logic, otherwise display error: Product with external value '%ExtProductId%' for external code '%ExtCodeId%' not found.
```

- Any external interface should execute same logic, that could be reproduced by the user preliminary. 
 
  - Thus, no external interface can auto-create setup or masterdata to complete. All setup must be done before running the interface.

- Using standard or existing frameworks (_Data Management_ etc.) is in priority.
