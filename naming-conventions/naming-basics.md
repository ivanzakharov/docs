---
layout: docs
title: Naming basics
group: naming-conventions
subgroup: naming-basics
toc: true
---

Naming conventions contribute to consistency and to making the application easier to understand.
## General Rules

  - All names must be in U.S. English.

  - The default rule is to use logical and descriptive names if no other specialized rules apply.

  - Identifier names have a limit of 81 characters.

  - Names in the Application Object Tree (AOT) and in X++ code must correspond to the names in the U.S. English user interface.

  - Names must be spelled correctly.

  - Names must be used consistently.

  - Each path in the AOT must be unique; nodes must not have identical names.

  - All texts that appear in the user interface must be defined by using a label. (This rule applies only if you want your solution certified as an international solution.)

  - Do not begin a name with "DEL\_" unless it is a table, extended data type or enum, and it is needed for data upgrade purposes. Names that use these prefixes cause a best practices error when you check the objects into the version control system.![Error icon](images/Aa872655.ErrorIcon(AX.60).gif "Error icon")

  - We do not support an EDT with the same name as a Table, EDT, Base Enum, or Class.
  
  - Hereafter <b>_PRJ</b> suffix used for all customization in specific model (see [Models naming](model-naming.md)).
  
  - All customizations should have project suffix (see  referred as <b>_PRJ</b>).
  
  - All customizations should be implemented in the single unified model (hereinafter referred as <i><b>Project</b> model</i>).
  
  - Present naming conventions guarantee to have only one extension for the object.
  

Rules are available about the following:

  - [Use of labels](best-practices-for-labels.md)

  - [Name structure](naming-conventions-name-structure.md)

  - [Upper and lower case](naming-conventions-use-of-uppercase-and-lowercase.md)

  - [Underscores](naming-conventions-underscores.md)

  - [Abbreviations](naming-conventions-abbreviations.md)

  - [Prefixes](naming-conventions-prefixes.md)

  - [Naming Convention: Automatically Generated Names](naming-convention-automatically-generated-names.md)

