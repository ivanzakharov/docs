---
layout: docs
title: 'Code execution sequence using Chain-of-Commands and EventHandlers'
group: examples
subgroup: code-execution-sequence
redirect_from:
  - "/examples/"
toc: true
---

Take into account code execution sequence (1,2,3,4) for the following code:

```
[ExtensionOf(tableStr(ProjTable))]
final class ProjTable_PRJ_Extension 
{
    public void update(boolean _skipSyncTrigger, boolean _skipReservationUpdate)
    {
        // 1
        // do something ..

        next update(_skipSyncTrigger, _skipReservationUpdate);

        // 4
        // do something ..
    }

    [DataEventHandler(tableStr(ProjTable), DataEventType::Updating)]
    public static void ProjTable_onUpdating(Common sender, DataEventArgs e)
    {
        // 2
        // do something ..
    }
    
    [DataEventHandler(tableStr(ProjTable), DataEventType::Updated)]
    public static void ProjTable_onUpdated(Common sender, DataEventArgs e)
    {
        // 3
        // do something ..
    }
}
```
