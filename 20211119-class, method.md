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

## 2. method - return int
```c# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp2
{
    class Program
    {
        static void Main(string[] args)
        {
            Order order = new Order();
            int unitPrice = 1000, qty = 2;
            int subTotal = order.CalcSubTotal(unitPrice, qty);
            Console.WriteLine("小計是 " + subTotal);//小計是 2000
        }
    }

    class Order
    {
        public int CalcSubTotal(int unitPrice, int qty)
        {
            int result = unitPrice * qty;
            return result;
        }
    }
}
```
<hr>
* 副程式(標準措詞是 method - 方法)必須放在類別裡面
* public 表示外界可以叫用
* int 表示這支副程式會傳回一個值, 型別(Type) 是 int(整數)
* CalcSubTotal(中文意思是計算小計) 是副程式名稱, 命名規則與類別相同, 第一個字大寫, 不可以用數字開頭
* 緊接著是一對小括號, 如果呼叫這副程式時需要一併傳入必要資訊(在這裡傳入的是商品單價, 數量)
* 小括號裡的稱為 Parameter(參數), 副程式的參數可以是零個, 一個,或多個參數, 建議最多不要超過三個參數, 比較不會造成叫用時的困擾
* 小括號之後要接一對大括號, 這點與類別是相同的, 大括號裡面可以寫程式
* 這支副程式要傳回整數, 寫法是用了 return , 如果副程式沒有需要傳回值, 可以不寫 return
![C# method()](https://user-images.githubusercontent.com/72750077/142757995-d9da80b4-127a-47e6-a61b-eb485425b2cd.png)

