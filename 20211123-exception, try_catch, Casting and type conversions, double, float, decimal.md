## Keywords
* throw new Exception()
* throw new ArgumentOutOfRangeException()
* try-catch
* Casting and type conversions
* double
* float
* demimal
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
    internal class Program
    {
        static void Main(string[] args)
        {
            ///Utilize "try{}catch(){}" to modify Exception messages.
            try
            {
               OrderService orderService = new OrderService();
                int result = orderService.CalculSubtotal(-10,5);
            }
            catch(Exception ex)//"Exception" is a kind of class, and "ex" is a variable.
            {
                Console.WriteLine("Sorry, we are having some issues here, and the reason is " + ex.Message); ;
            }
        }
    }

    class OrderService
    {
        public int CalculSubtotal(int price, int qty)
        {
            if (qty <= 0) throw new Exception("Quantity must be bigger than zero.");
            if (price <= 0) throw new Exception("Price must be higher than zero.");

            return price * qty;
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
<hr>

## Reference
[try-catch (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/try-catch)
[Casting and type conversions (C# Programming Guide)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
