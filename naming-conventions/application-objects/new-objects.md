---
layout: docs
title: 'Naming conventions for new application objects'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

New objects with following types are created with <b>_PRJ</b> suffix:
- Base Enums
- Extended Data Types
- [Tables](tables.md)
- Views
- Queries
- Data Entities
- Composite Data Entities
- Aggregate Data Entities
- Maps
- Table Collections
- Classes
- Macros
- Forms
- Tiles
- Menus
- Menu Items
- Analytics
  - Perspectives
    - Aggregate Dimensions
    - Aggregate Measurements
    - Calculated Measure Templates
    - Calculated Measure Period Templates
  - Key Performance Indicators (KPI)
- Reports 
  - Reports
  - Report Style Templates
  - Report DataSources
  - Report Images
- Business Process and Workflow
- Resources
- Configuration 
  - License Codes
  - Configuration Keys
  - Configuration Key Groups
- Security Roles
- Security Duties
- Security Privileges
- Security Policies
- Services
- Service Groups

Example:

```
BaseEnums\BankClientStreamType_PRJ
BaseEnums\DayNight_PRJ
BaseEnums\GanttBorderType_PRJ
ExtendedDataTypes\DirOrganizationRoles_PRJ
ExtendedDataTypes\ProjCategoryItemId_PRJ
ExtendedDataTypes\EcoResProductTypeCategoryId_PRJ
Tables\EcoResCategoryGroupsTable_PRJ
Tables\CustomerEntityStaging_PRJ
Tables\DispatchBoardProfile_PRJ
Views\WorkflowCommentList_PRJ
Views\PurchTableLastReqView_PRJ
Queries\ActivityListOpen_PRJ
Queries\AssetRecordList_PRJ
```
