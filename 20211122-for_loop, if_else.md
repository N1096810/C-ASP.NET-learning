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

## 2. if_else - 1
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
    /// </summary>
    internal class Program
    {
      
        static void Main(string[] args)
        {
            int a = 4, b = 5, c = 6, d = 0;
            Member member = new Member();
            member.A = a;
            member.B = b;  
            member.C = c;
            member.D = d;

            if(member.IsValid())// = if(member.IsValid() == true)
            {
                Console.WriteLine("Situation 1");
            }
            else
            {
                Console.WriteLine("Situation 2");
            }
        }
    }

    public class Member
    {
        public int A { get; set; }
        public int B { get; set; }
        public int C { get; set; }
        public int D { get; set; }

        public bool IsValid()
        {
            return A > 0 && B > 0 && C >0 && D > 0;
        }
    }
}

```

## 3. if_else - 2
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

## 4. if_else 判斷順序
``` C# =
if() 條件式由左判斷到右
if (result1.Length > 5 && result1 != null)//若result1 = null, 則程式會出現錯誤
if (result1 != null && result1.Length > 5)//若result1 = null, 則if判斷式不成立
```
