## Keywords
* class
* objective
* member 
<hr>

## 1. TBD
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    /// <summary>
    /// Create new class, class & property & field names must begin with a CAPITAL character.
    /// DON'T create your class name beginning with a "Number" in case of bugs. Ex: 123Apple
    /// It's recommended to create only one "class" within one ".cs" file with the same name<br> for better readiness
    /// </summary>
    internal class Program
    {
        static void Main(string[] args)
        {
            ///<summary>
            ///A "class" is a design layout of an "object".
            ///A bike design layout can create multiple bikes, and each bikes is independent.
            ///I have a bike, and Tom has a bike, too. Ours bikes are same in color, wheels and height. But my bike won't become his bike.
            ///</summary>

            //First way to create an object
            //Because class "order" has been created, so "order" now becomes a kind of "type" that can be called<br> to create a new object, similar to"int" or "string".
            Order order1 = new Order { ID = 001, Quantity = 10, UnitPrice = 5, OrderTime = DateTime.Today };
            Console.WriteLine(order1.OrderTime);
            int order1Price = AutoCount.GetSum(order1.Quantity, order1.UnitPrice);
            //Because "GetSum" was writtened within the class "AutoCount", so GetSum() should be called as above.
            Console.WriteLine(order1Price);//50
            Console.WriteLine(AutoCount.GetSum(order1.Quantity, order1.UnitPrice));//50

            //Second way to create an object
            var order2 = new Order();//command "var" will auto distinguish the type of a variable.
            order2.ID = 002;
            order2.Quantity = 5;
            order2.OrderTime = DateTime.Now;
            order2.UnitPrice = 3;
            int order2Price = AutoCount.GetSum(order2.Quantity, order2.UnitPrice);
            Console.WriteLine(order2Price);//15
            Console.WriteLine(AutoCount.GetSum(order2.Quantity, order2.UnitPrice));//15
        }
    }

    /// <summary>
    /// A class can include multiple "Members", including field, property, method, or event...and so on.
    /// </summary>
    internal class Order
    {
        public int Name;//field
        public string Description { get; set; }//Property
        public int Quantity { get; set; }//Property
        public DateTime OrderTime { get; set; }//Property
        public int ID { get; set; }//Property
        public int UnitPrice { get; set; }
    }

    public class AutoCount
    {
        public static int GetSum(int unitAmount, int unitPrice)
        {
            int totalAmount = unitAmount * unitPrice;
            return totalAmount;
        }
    };
}
```
