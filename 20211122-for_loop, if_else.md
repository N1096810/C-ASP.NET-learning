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

## 2.if_else
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp2
{
    /// <summary>
    /// 使用物件/副程式來寫判斷式，更簡潔好懂且好修改
    /// 3歲以下不收錢
    /// 60歲以上女性收3元
    /// 70歲以上男性收5元
    /// 其餘收15元
    /// </summary>
    internal class Program
    {
      
        static void Main(string[] args)
        {
            Customer customer = new Customer();
            customer.Gender = true;
            customer.Age = 70;

            int result;
            
            if (customer.IsOldMan() == true)
            {
                result = 5;
            }
            else if (customer.IsOldWoman() == true)
            {
                result = 3;
            }
            else if (customer.IsChild() == true)
            {
                result = 0;
            }
            else
            {
                result = 15;
            }
            Console.WriteLine(result);//5
        }
    }

    public class Customer
    {
        public bool Gender { get; set; }
        public int Age { get; set; }


        public bool IsOldMan()
        {
            if ((Gender == true) && (Age >= 70))
            {
                return true;
            }
            else 
            { 
                return false; 
            }
        }

        public bool IsOldWoman()
        {
            if ((Gender == false) && (Age >= 60))
            {
                return true;
            }
            else
            {
                return false;
            }
        }

        public bool IsChild()
        {
            if (Age <= 3)
            {
                return true;
            }
            else
            {
                return false;
            }
        }
    }
}

```
