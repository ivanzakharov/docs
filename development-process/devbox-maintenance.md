---
layout: docs
title: 'Devbox maintenance'
group: development-process
subgroup: devbox-maintenance
redirect_from:
  - "/development-process/"
toc: true
---

## Updating local devbox (VHD) to latest application or platform release

- Download latest update package from LCS

- Unblock downloaded zip (on file property page check _Unblock_ and click _Apply_) 

  You may also unblock all already unzipped files with running following in PowerShell with elevation:
  
  ```
  dir C:\Update -Recurse | Unblock-File
  ```

- Run Command Prompt as Administrator and change current folder. Further steps should also be executed in the PowerShell.

  ```
  C:
  cd C:\Update
  ```

- Run creating the runbook on current based on its topology. Put current date into runbook name.

  ```
  AXUpdateInstaller.exe generate -runbookid="Update20191104" -topologyfile="DefaultTopologyData.xml" -servicemodelfile="DefaultServiceModelData.xml" -runbookfile="Update20191104.xml"
  ```

- Import created runbook 

  ```
  AXUpdateInstaller.exe import -runbookfile=Update20191104.xml
  ```
  
- Execute imported runbook 

  ```
  AXUpdateInstaller.exe execute -runbookid=Update20191104
  ```
  
- To re-run steps use following command if needed:

  ```
  AXUpdateInstaller.exe execute -runbookid=Update20191104 -rerunstep=1
  ```
  
- To skip steps, use following:

  ```
  AXUpdateInstaller.exe execute -runbookid=Update20191104 -setstepcomplete=1
  ```

## Increasing the performance

### Decreasing the CPU workload

- Disable Windows Defender (!DO IT ON YOUR OWN RISK!)

  [Removing Windows Defender policies (Registry)](http://zakharov.com/development-process/defender-policies-remove.reg)
  
## Windows Activation issues





 
