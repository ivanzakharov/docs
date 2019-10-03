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

- When a developer changes someone’s code, or relies on it, then in any case, he takes responsibility for the correct execution of the code.

- Each customization should be checked with another developer for BP. See [Code review](/development-process/code-review/)

- To run something in batch and if it will not be consumed externally (with web-service calls etc.), it is simplier to implement it using the RunBaseBatch framework rather than SysOperations.

## Reintenting the wheel

Sometimes Developers implement solutions that should be reworked from scratch after development is finished. To prevent this, following solutions should signal to do additional checking from Technical Architect.

- Using _container_-type fields in tables.

- Storing list of values (separated with comma, etc.) in a single field/variable.

- Using any multi-values types (like _container_, _List_, _Set_, etc.) in RunBase-framework classes.

## Application objects guidelines

[Tables](/development-guidelines/application-objects/tables/)

[Macros](/development-guidelines/application-objects/macros/)


## Financial dimensions

- No 'Custom dimensions' allowed for implementation project.<br/>Each using 'Custom dimension' should be replaced with backed entity (with separate setup form) and setup table.
  See example with [Dimension].

- Each financial dimension attribute should mapped with 'Dimension attribute type' (base enum) value and therefore used in the code.
  Dimension attribute type specified at initial setup for each financial dimension (dimension attribute) and can't be changed.

## Interfaces guidelines

- Any interface should use only external codes for each mapped table.

Example:

```
1. Get value '0001200' as ExtProductId from CSV-file or web-request
2. Get ExtCodeId from interface setup
3. Use ExtProductId and ExtCodeId to find external code value (int ExtCodeValueTable) related with product (EcoResProduct) record.
4. Use founded product record to further logic, otherwise display error: Product with external value '%ExtProductId%' for external code '%ExtCodeId%' not found.
```

- Any interface should execute same logic, that could be reproduced by the user preliminary. 

- Using standard or existing frameworks (_Data Management_ etc.) is in priority.
