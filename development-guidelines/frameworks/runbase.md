---
layout: docs
title: 'Development guidelines for RunBase framework'
group: development-guidelines
subgroup: frameworks
redirect_from:
  - "/development-guidelines/frameworks"
toc: true
---

Following rules are dedicated for implementing handlers using the RunBase-framework. 

## Parameters

- The parameter must be accompanied by a _parm_-method.

- The parameter must be accompanied by a displayed field. This will allow for user to see all running parameters in the Batch task form.

Examples:

```
ItemId itemId;
DialogField dialogItemId;
```

- The parameter should be extended from any primitive type, except _container_.<br/> Using of containers as the parameters is prohibited to use.<br/>Use _RecordReference_RU_ table to have filter query with specific records.

- Parameters validation (using _validate()_ method) must be also executed in run() method. 

Examples:

```
public void run()
{
    #OCCRetryCount

    setPrefix(TutorialRunBase_PRJ::description());

    if (! this.validate())
    {
        throw error("@SYS18447");
    }

    try
    {
        ttsbegin;

        ...

        ttscommit;
    }
    catch (Exception::Deadlock)
    {
        queryRun.reset();
        retry;
    }
    catch (Exception::UpdateConflict)
    {
        if (appl.ttsLevel() == 0)
        {
            if (xSession::currentRetryCount() >= #RetryNum)
            {
                throw Exception::UpdateConflictNotRecovered;
            }
            else
            {
                itemQueryRun.reset();
                retry;
            }
        }
        else
        {
            throw Exception::UpdateConflict;
        }
    }
}

```

## Naming conventions

See [Naming conventions for Variables](/naming-conventions/code-artifacts/variables/#runbase-extensions) for RunBase extensions.

See [Naming conventions for Methods](/naming-conventions/code-artifacts/methods/#runbase-extensions) for RunBase extensions.
