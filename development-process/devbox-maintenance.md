---
layout: docs
title: 'Devbox maintenance'
group: development-process
subgroup: devbox-maintenance
redirect_from:
  - "/development-process/"
toc: true
---

## Updating to latest application or platform release

- Download latest update package from LCS

- Unblock downloaded zip (on file property page check _Unblock_ and click _Apply_) 

  You may also unblock all already unzipped files with running following in PowerShell with elevation:
  
  ```
  dir C:\Update -Recurse | Unblock-File
  ```

- Run PowerShell as Administrator and change current folder. Further steps should also be executed in the PowerShell.

  ```
  C:
  cd C:\Update
  ```

- Install or update [d365fo.tools](https://github.com/d365collaborative/d365fo.tools) module, accepting all required packages installing.
 
  ```Install-Module -Name d365fo.tools -Force```
  
  or
  
  ```Update-Module -Name d365fo.tools -Force```

- Run creating the runbook on current based on its topology. Put current date into runbook name.

  ```
  Invoke-D365SDPInstall -Path "C:\Update" -Command Generate -RunbookId 'Update20191104'
  ```

- Import created runbook 

  ```
  Invoke-D365SDPInstall -Path "C:\Update" -Command Import -RunbookId 'Update20191104'
  ```
  
- Execure imported runbook 

  ```
  Invoke-D365SDPInstall -Path "C:\Update" -Command Execute -RunbookId 'Update20191104'
  ```

## Increasing the performance

### Decreasing the CPU workload

- Disable Windows Defender (!DO IT ON YOUR OWN RISK!)

  [Removing Windows Defender policies (Registry)](http://zakharov.com/development-process/defender-policies-remove.reg)
  
## Windows Activation issues





 
