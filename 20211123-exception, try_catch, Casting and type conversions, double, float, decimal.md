## Keywords
* throw new Exception()
* try-catch
* Casting and type conversions
* double
* float
* demimal
* Round
<hr>

## 1. throw new Exception() / try-catch
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    internal class Exception
    {
        static void Main(string[] args)
        {
            ///Utilize "try{}catch(){}" to modify Exception messages.
            try
            {
                OrderService orderService = new OrderService();
                int result = orderService.CalculSubtotal(10,8);
                Console.WriteLine(result);
                Console.WriteLine(orderService.DoA());
            }
            //"Catch" will only be executed when any errors happen."
            //"Exception" is a kind of class, and "ex" is a variable.
            catch (System.Exception ex)
            {
                Console.WriteLine($"Sorry, we are having some issues here, and the reason is " + ex.Message); ;
            }
        }
    }

    class OrderService
    {
        public int CalculSubtotal(int price, int qty)
        {
            if (qty <= 0) throw new System.Exception("Quantity must be bigger than zero.");
            if (price <= 0) throw new System.Exception($"{price} must be higher than zero.");
            //if (price <= 0) throw new Exception();

            return price * qty;
        }

        public int DoA()
        {
            throw new NotImplementedException();//Used as a temporary tag to reminder programmers of unfinished contents.
            
        }
    }
}

```

## 2. int.TryParse
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp2
{
    internal class Program
    {
        /// <summary>
        /// string to int => int.TryParse(no exception returned) / Convert.Int32(will have exception returned)
        /// </summary>
        static void Main(string[] args)
        {

            string value = "12sfdsdf3";
            Console.WriteLine(int.TryParse(value, out int number));//false
            bool isInt = int.TryParse(value, out number);
            if (isInt)
            {
                Console.WriteLine(number + 2);
            }
            else
            {
                Console.WriteLine("Input value can't be converted into integer.");//This one
            }

            string value2 = "10";
            Console.WriteLine(int.TryParse(value2, out int number2));//true
            bool isInt2 = int.TryParse(value2, out number2);

            if (isInt2)
            {
                Console.WriteLine(number2 + 2);//12
            }
            else
            {
                Console.WriteLine("Input value can't be converted into integer.");
            }


        }
    }
}

```

## 3. Round / Math.Round(_______, MidpointRounding.AwayFromZero);
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp2
{
    internal class Round
    {
        /// <summary>
        /// Round
        /// </summary>
        /// <param name="args"></param>
        static void Main(string[] args)
        {
            int tax = OrderService.PayTax(100);//5
            Console.WriteLine(tax);

            tax = OrderService.PayTax(119);//5.95 => 6
            Console.WriteLine(tax);

            tax = OrderService.PayTax(210);//10.5 => 11
            Console.WriteLine(tax);
        }
    }

    class OrderService
    {
        public static int PayTax(int price)
        {
            //The default parameter of "Math.Round" is "MidpointRounding.ToEven"(四捨六入五成雙)
            double tax = Math.Round(price * 0.05, MidpointRounding.AwayFromZero);
            return (int)tax;//(type) => force the varible to convert its type.

        }
    }
}

```

<hr>

## Reference
[try-catch (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/try-catch)
[Casting and type conversions (C# Programming Guide)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
