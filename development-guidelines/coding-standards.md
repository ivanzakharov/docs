---
layout: docs
title: 'Development guidelines: Coding standards'
group: development-guidelines
subgroup: coding-standards
redirect_from:
  - "/development-guidelines/"
toc: true
---

This topic provides general coding principles for Dynamics 365 for Finance & Operations.

- Declare variables as locally as possible.

- Check the error conditions in the beginning; return/abort as early as possible.

- Have only one successful return point in the code (typically, the last statement), with the exception of switch cases, or when checking for start conditions.

- Keep the building blocks (methods) small and clear. A method should do a single, well-defined job. It should, therefore, be easy to name a method.

- Put braces around every block of statements, even if there is only one statement in the block.

- Put comments in your code, telling others what the code is supposed to do, and what the parameters are used for.

- Do not assign values to, or manipulate, actual parameters that are "supplied" by value. You should always be able to trust that the value of such a parameter is the one initially supplied. Treat such parameters as constants.

- Clean up your code; delete unused variables, methods and classes. Erase non-running (commented) code.

- Never let the user experience a runtime error. Take appropriate actions to either manage the situation programmatically or throw an error informing the user in the Infolog about the problem and what actions can be taken to fix the problem.

- Never make assignments to the "this" variable.

- Avoid dead code. (See [Dead Code Examples](/examples/dead-code.md))

- Reuse code. Avoid using the same lines of code in numerous places. Consider moving them to a method instead.

- Never use infolog.add directly. Use the indirection methods: error, warning, info and checkFailed.

- Design your application to avoid deadlocks.


## X++ Layout

-	Only one statement per line.

-	Break up complex expressions that are more than one line - make it visually clear.

- Do not exceed X++ code line with more than 140 characters, break it up to several lines.

- Use a single blank line to separate entities.

- Do not use parentheses around the _case_ constants. 

- Do not use parentheses around _where_ expressions.

- Add one space between _if_, _switch_, _for_, _while_ and the expressions starting parentheses. 

  Example:
  
  ```
  if (isCreditNote)
  {
     ... // do something
  }
  ```
  
- Add one space after not (!) operator. 

  Example:
  
  ```
  if (! isInvoiced)
  {
      while select forupdate salesTable
         where ! salesTable.ProjId
      {
         ... 
      }
  }
  ```
  
- Do not use space between function name and starting parentheses.

  Example:
  
  ```
  targetFile.write(wrkStr2);
  ```
  
- Do not use space in function call with empty parameters.

  Example:
  
  ```
  inventTable_ds.reread();
  ```
  
- Use braces around all code blocks, except for around _case_ clauses in a _switch_ statement. Use braces even if there is only one statement in the block.

  Example:
  
  ```
  if (! isProforma)
  {
      return;
  }
  ```
