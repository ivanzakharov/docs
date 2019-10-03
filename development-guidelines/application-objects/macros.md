---
layout: docs
title: 'Development guidelines for macros'
group: development-guidelines
subgroup: application-objects
redirect_from:
  - "/development-guidelines/application-objects/"
toc: true
---

- Creating of macro is prohibited, use public variable with constant value.

  Example:

  ```
  class TutorialMacro
  {
      public const str InfoString = 'This is the info string'; 
  }


  class PRJ00001_TutorialConstUse  
  {
      public static void main(Args _args)
      { 
          info(TutorialClass::InfoString);
      }
  }

  ```

- No excessive macro/constants using

  Example (incorrect):
  
  ```
  class PRJ00001_TutorialExcessiveMacroUse  
  {
      public static void main(Args _args)
      { 
          #define.OneConst(1)
          #define.TenConst(10)
          
          for (i = #OneConst; i <= #TenConst; i++)
          {
          }
      }
  }
  ```
  
  Example (correct):
  
  ```
  class PRJ00001_TutorialExcessiveMacroUse  
  {
      public static void main(Args _args)
      { 
          for (i = 1; i <= 10; i++)
          {
          }
      }
  }
  ```

- No macro using in interfaces or import/export operations when data structure is fixed. Use literals instead to simplify the code. 

  Example:

  ```
  ...
  container c = file.read();
  str s1 = conpeek(1); // no macro use
  str s2 = conpeek(2); // no macro use
  int i = any2num(substr(s1, 2, 10)); // no macro use
  ...
  ```
