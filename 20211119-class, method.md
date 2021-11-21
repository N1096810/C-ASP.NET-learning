## Keywords
* class
* objective
* member
* static 
<hr>

## 1. objective, class, member
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
            Console.WriteLine(order1.OrderTime);//11/21/2021 12:00:00 AM
            int order1Price = AutoCount.GetSum(order1.Quantity, order1.UnitPrice);
            //Because "GetSum" was writtened within the class "AutoCount", so GetSum() should be called as above.
            Console.WriteLine(order1Price);//50
            Console.WriteLine(AutoCount.GetSum(order1.Quantity, order1.UnitPrice));//50

            //Second way to create an object
            var order2 = new Order();//command "var" will auto distinguish the type of a variable.
            order2.ID = 002;
            order2.Quantity = 5;
            order2.OrderTime = DateTime.Now;
            order2.UnitPrice = 7;
            int order2Price = AutoCount.GetSum(order2.Quantity, order2.UnitPrice);
            Console.WriteLine(order2Price);//35
            Console.WriteLine(AutoCount.GetSum(order2.Quantity, order2.UnitPrice));//35

            //static method 可以直接寫類別名稱之後就叫用
            Console.WriteLine(AutoCount.GetSum(7, 8));
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
```
* 副程式(標準措詞是 method - 方法)必須放在類別裡面
* public 表示外界可以叫用
* int 表示這支副程式會傳回一個值, 型別(Type) 是 int(整數)
* CalcSubTotal(中文意思是計算小計) 是副程式名稱, 命名規則與類別相同, 第一個字大寫, 不可以用數字開頭
* 緊接著是一對小括號, 如果呼叫這副程式時需要一併傳入必要資訊(在這裡傳入的是商品單價, 數量)
* 小括號裡的稱為 Parameter(參數), 副程式的參數可以是零個, 一個,或多個參數, 建議最多不要超過三個參數, 比較不會造成叫用時的困擾
* 小括號之後要接一對大括號, 這點與類別是相同的, 大括號裡面可以寫程式
* 這支副程式要傳回整數, 寫法是用了 return , 如果副程式沒有需要傳回值, 可以不寫 return
```
![C# method()](https://user-images.githubusercontent.com/72750077/142757995-d9da80b4-127a-47e6-a61b-eb485425b2cd.png)

## 3. method - return string
```C# =
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
            Member member = new Member();
            string fullName = member.GetFullName("Allen", "Kuo");
            Console.WriteLine(fullName);// Allen Kuo
            string name2 = member.GetFullName("Barry","");
            Console.WriteLine(name2);// Barry

        }
    }

    class Member
    {
        /// <summary>
        /// 傳回會員全名,若兩個參數都有值,用空白區隔; 若只有一個參數有值,直接傳回; 如果都沒值,傳回空字串
        /// </summary>
        /// <param name="firstName">名</param>
        /// <param name="lastName">姓</param>
        /// <returns></returns>
        public string GetFullName(string firstName, string lastName)
        {
            string result = string.Empty;
            if (string.IsNullOrEmpty(firstName) == false)
            {
                result = result + firstName + " ";
            }

            if (string.IsNullOrEmpty(lastName) == false)
            {
                result = result + lastName;
            }

            return result.Trim();
        }
    }
}
```
```
* 要供外界叫用, 所以寫了 public
* 要傳回字串型別, 所以寫了 string
* GetFullName是method(方法, 初學時, 經常先稱它是副程式)的名稱
* 緊接著是一對小括號
* 小括號裡的 Parameter(參數), 這裡設計了二個參數, 分別是名(firstName), 姓(lastName)
* 小括號之後要接一對大括號, 這點與類別是相同的, 大括號裡面可以寫程式
* 這支副程式要傳回字串, 寫法是用了 return , 如果副程式沒有需要傳回值, 可以不寫 return
* 如果只有傳入 firstName時, result 最後會多一個空白, 所以在 return 時叫用了 Trim(), 將字串左右空白刪除(其實只要刪右側即可), 但其實使用者的* firstName也許不小心也打了空白, 所以就用了 Trim()
* 先把method 宣告好, 再在 method 上打三條斜線, 就會自動寫好綠色的註解, 接著再填入註解即可
```

## 4. method - return void
```C# =
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
            ConsoleDrawer drawer = new ConsoleDrawer();
            drawer.DrawLine(new string('*', 1));//*
            drawer.DrawLine(new string('*', 2));//**
            drawer.DrawLine(new string('*', 3));//***
            drawer.DrawLine(new string('*', 4));//****
            drawer.DrawLine(new string('*', 5));//*****
        }
    }

    class ConsoleDrawer
    {
        public void DrawLine(string message)
        {
            if (string.IsNullOrEmpty(message) == true)
            {
                return; // 如果沒有傳入參數沒有值, 就不做任何動作
            }

            Console.WriteLine(message);
        }
    }

}
```
```
* 要供外界叫用, 所以寫了 public
* 沒有要傳回資訊, 所以寫了 void
* DrawLine 是 method(方法)的名稱
* 緊接著是一對小括號
* 小括號裡的 Parameter(參數), 這裡設計了一個參數, 是希望呈現出來的訊息
* 小括號之後要接一對大括號, 這點與類別是相同的, 大括號裡面可以寫程式
* 這支副程式沒有要傳回任何資訊, 所以沒有一定要寫return , 但範例裡有寫檢查, 如果傳入 message 參數是 null or 空字串, 就直接 return (直接結束, 接下去的程式碼就不會被執行), 程式執行到 method 最後一行會自動結束, 所以不必在最後一行還特別再寫一次 return
* 撰寫副程式時, 通常都要在一開始先檢查傳入參數值是否合理, 如果不合理, 就提早結束; 這類檢查程式碼不可省, 也算是防呆, 用比較專業的術語, 稱為 * contract(合約, 約束), 必需先檢查是否符合 contract , 程式再繼續執行下去
```

## 5. set put parameters
```C# =
        /// <summary>
        /// 刪除某一個檔案
        /// </summary>
        /// <param name="path">要刪除檔案的完整路徑</param>
        public void DeleteFile(string path) { }

        /// <summary>
        /// 計算5%螢業稅, 若有小數點, 四捨五入
        /// </summary>
        /// <param name="price">未稅金額</param>
        /// <returns></returns>
        public int CalcTax(int price) { }

        /// <summary>
        /// 將圖片按比例縮小到指定尺寸
        /// </summary>
        /// <param name="originalImagePath">原始圖片的完整路徑</param>
        /// <param name="newWidth">縮圖之後的圖寬最大允許值</param>
        /// <param name="newHeight">縮圖之後的圖高最大允許值</param>
        public void ResizeImage(string originalImagePath, int newWidth, int newHeight) { }
```

## 6. Static method(靜態方法)
```C# =
namespace ConsoleApp2
{
    class Program
    {
        static void Main(string[] args)
        {
            ImageHelper helper = new ImageHelper();
            helper.DoA();

            ImageHelper.DoB()
        }
    }

    class ImageHelper
    {
        public void DoA()
        { }

        public static void DoB()
        { }
    }
}
```
```
如果在宣告時 method(方法) 時加上 "static" , 表示它是 static method(靜態方法), 初學者經常分不清它有什麼差別, 有什麼作用, 何時要用或不用 static

請參考以下程式以及叫用的方式
* DoA() 不是 static , 所以必需先建立一個 ImageHelper 型別的物件, 再叫用它
* DoB() 是 static 的, 叫用方式是直接寫類別名稱之後就叫用

差別的確是有的, 不過會在很久以後, 教到物件導向時再一起說明, 目前只需要了解有沒有加 static 時, 差別會在叫用方式即可
實務上, 大部份都是沒有 static , 少部份是 static , 二者差別有多少, 我沒有仔細統計, 也不可能有精確數值, 不過我個人的經驗裡, 比例差不多 50 : 1 吧, 大剖份不是static, 少部份是 static
```


## 7. method - design patterns
### 功能要單一
```
每一支副程式的功能愈單一, 日後會被重覆叫用的機會就愈高, 例如:
您想將一張大圖按比例縮小, 並將它複製到其他一個或多個資枓夾, 最好就拆解成兩支副程式
* 能按比例將大圖縮成小圖並存檔
* 能將指定檔案(不限於圖檔)複製到一或多個資料夾

您想寫一支新增新註冊會員的功能, 可以拆解成
* 驗證各欄位值是否正確地填寫
* 驗證會員帳號是否已被別人使用
* 建立一筆新會員記錄
* 寄發Email(例如新會員的通知信或確認信)

功能單一, 也會更方便進行單元測試

有人覺得副程式切得愈多支, 日後要查看程式碼會愈複雜, 因為要在多支副程式裡游走, 但其實不然, 例如上方的例子, 若針對新會員註刪, 不需要發 Email 了, 相信您一定可以在極短時間就把這一行刪除; 又例如有人忘了填Email ,但居然也能成功建立會員, 顯然是驗證的副程式有問題, 您很快就能到該副程式去檢查
```
### 命名要貼切
```
只要副程式的功能愈單一, 您就愈有機會給它一個確切的名稱, 相反地, 如果副程式裡的功能很多, 命名就有困難, 或者會導致名稱需要很長才能描述清楚
```
## TBD
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {

            //Program2 order = new Program2();
            //int unitPrice = 1000, qty = 2;
            //int subTotal = order.CalcSubTotal(unitPrice, qty);
            Program2 order = new Program2 { UnitPrice = 500, Qty = 5 };
            int subTotal = order.CalcSubTotal();
            Console.WriteLine("小計是 " + subTotal);//小計是 2000
            Console.WriteLine("小計是 " + Program2.CST2(75, 10));//小計是 750
        }
    }

    class Program2
    {
        public int UnitPrice { get; set; }
        public int Qty { get; set; }
        public int CalcSubTotal()
        {
            int result = UnitPrice * Qty;
            return result;
        }

        public static int CST2(int unitPrice, int qty)
        {
            int result2 = unitPrice * qty;
            return result2;
        }
    }
}
```

<hr>

## References
[05 - CS03.04 類別、方法入門](https://www.evernote.com/shard/s530/client/snv?noteGuid=73f5da69-cb21-e8f4-bc57-4ca56aac82e5&noteKey=954235f55ede87aa146cf27c6b52baf5&sn=https%3A%2F%2Fwww.evernote.com%2Fshard%2Fs530%2Fsh%2F73f5da69-cb21-e8f4-bc57-4ca56aac82e5%2F954235f55ede87aa146cf27c6b52baf5&title=05%2B-%2BCS03.04%2B%25E9%25A1%259E%25E5%2588%25A5%25E3%2580%2581%25E6%2596%25B9%25E6%25B3%2595%25E5%2585%25A5%25E9%2596%2580)
