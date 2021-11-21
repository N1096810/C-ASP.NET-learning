## Keywords
* class
* method
<hr>

## 1. Class & method
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp2
{
    /// <summary>
    /// Create new class, class & property & field names must begin with a CAPITAL character.
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

    internal class Program
    {
        static void Main(string[] args)
        {   
            //建立物件的第一種方法
            //因為已經建立的class Order, 所以現在Order變成一種可被宣告的type，類似int / string
            Order order1 = new Order {ID = 001, Quantity = 10, UnitPrice = 5,OrderTime=DateTime.Today};
            Console.WriteLine(order1.OrderTime);
            int order1Price = AutoCount.GetSum(order1.Quantity, order1.UnitPrice);
            //Because "GetSum" is writtened within the class "AutoCount",
            //so GetSum() should be called as above.
            Console.WriteLine(order1Price);//50
            Console.WriteLine(AutoCount.GetSum(order1.Quantity, order1.UnitPrice));//50

            //建立物件的第二種方法
            var order2 = new Order();//var 會自動根據"new Order()"去判斷"order2"的type
            order2.ID = 002;
            order2.Quantity = 5;
            order2.OrderTime = DateTime.Now;
            order2.UnitPrice = 3;
            int order2Price = AutoCount.GetSum(order2.Quantity, order2.UnitPrice);
            Console.WriteLine(order2Price);//15
            Console.WriteLine(AutoCount.GetSum(order2.Quantity, order2.UnitPrice));//15
            }
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
