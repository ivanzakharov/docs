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


## Additional guidelines for application objects

[Tables](/development-guidelines/tables)
