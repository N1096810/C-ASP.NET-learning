## Keywords
* for_loop
* switch
* if_else
* ?: operator(三元運算子)
<hr>

## 1.for_loop
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp2
{
    /// <summary>
    /// isOdd or not
    /// </summary>
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] items = { 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12 };

            for (int i = 0; i < items.Length; i++)
            {
                int currentValue = items[i];
                bool isOdd = currentValue % 2 == 1;
                if (isOdd)// = if (currentValue % 2 == 1 true)
                {
                    Console.WriteLine(currentValue);
                    break;//找到第一個就終止迴圈
                }
            }
        }
    }
}

```

## 2.Create the Environment
### 2.1.Create new project(with routing)
`ng new ngdemo`
`routing? > Yes`
`Check >　 app > app-routing.module.ts`

### 2.2.Create (type here)
`(type here)`
<br>
`(type here)`
<br>
`(type here)`
<hr>

## 3.app
### 3.1.TBD
```C# =
(type here)
```
### 3.2.app.component.ts
```C# =
(type here)
```

## 4.Reference
[Name](URL)
