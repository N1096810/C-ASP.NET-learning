## Keywords
<ul>
<li>IEnumerable<int></li>
<li>Enumerable.Range(x, y)</li>
<li>Where</li>
<li>Select</li>
<li>OrderBy</li>
<li>ThenBy</li>
<li>ToArray</li>
<li>ToList</li>
<li>Aggregate((acc, next) => acc + ", " + next)</li>
<li>LINQ Query Syntax(LINQ查詢語法)</li>
<li>Change PageNumbers</li>
<li>Join</li>
<li>Empty, Append, Prepend</li>
</ul>
<hr/>

## 1. ToArray, ToList
```c# =
using ConsoleApp4.EFModels;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp4
{
    internal class Read
    {
        static void Main(string[] args)
        {
            EStoreDdContext db = new EStoreDdContext();//EF method
            var data = db.News;//to dump all data into "data"
            var filted = data.Where(x => x.Id <= 5);//Select
            var sorted = filted.OrderBy(x => x.Id);//Order
            foreach (var item in sorted)//Read all items
            {
                Console.WriteLine(item.Id);
            }
            Console.WriteLine("*****");

            IEnumerable<int> data2 = Enumerable.Range(1, 10);

            int[] result = data2.ToArray();//IEnumerable<int > to int[]
            foreach (var item in result)
            {
                Console.WriteLine(item);
            }
            Console.WriteLine("*****");

            List<int> result2 = data2.ToList();//IEnumerable<int > to List<int>
            foreach (var item in result2)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## 2. Where, Select
```c# =
using ConsoleApp4.EFModels;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp4
{
    internal class Program
    {
        /// <summary>
        /// Select => For Mappinp
        /// Where  => For Filtering
        /// </summary>
        static void Main(string[] args)
        {
            IEnumerable<int> items = Enumerable.Range(0, 10);
            //IEnumerable<string> result = items.Select(x => "No." + x.ToString("000"));//No.000
            IEnumerable<string> result = items.Select(x => $"No.{x:00}");//No.00
            foreach (var item in result)
            {
                Console.WriteLine(item);
                /*
                No.00
                No.01
                No.02
                No.03
                No.04
                No.05
                No.06
                No.07
                No.08
                No.09
                */
            }

            IEnumerable<int> items2 = Enumerable.Range(0, 10);
            var query = items2
                        .Where(x => x % 4 == 0)
                        .Select(x => new Country { Id = x, Name = "This is Country No." + x });

            foreach (var item in query)
            {
                Console.WriteLine(item.ToString());
                /*
                ID: 0, Name: This is Country No.0
                ID: 4, Name: This is Country No.4
                ID: 8, Name: This is Country No.8
                */
            }

            var query2 = items.Where(value => value % 3 == 0);//This row is as same as below comments.
            //var query2 = items.Where(IsMatch);
            //bool IsMatch(int value)
            //{
            //    if(value % 3 == 0)
            //    {
            //        return true;
            //    }
            //    else
            //    {
            //        return false;
            //    }
            //}
        }

        public class Country
        {
            public int Id { get; set; }
            public string Name { get; set; }

            public override string ToString()//Use "Override" to amend the contents of the original "ToString()" method.
            {
                return $"ID: {Id}, Name: {Name}";
            }
        }
    }
}
```

## 3. OrderBy, ThenBy
```c# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp5
{
    internal class Program
    {
        /// <summary>
        ///"ThenBy" should be placed after "OrderBy"
        /// </summary>
        static void Main(string[] args)
        {
            string[] source = new string[] { "ZBC", "A", "ABC", "ASDSADSDA", };
            var query = source.Select(x => x.Length);
            foreach (var item in query)
            {
                Console.WriteLine(item);//3, 1, 3, 9
            }

            var query2 = source.OrderBy(x => x.Length);
            foreach (var item in query2)
            {
                Console.WriteLine(item);
                /*
                A 
                ZBC
                ABC
                ASDSADSDA
                */
            }

            query2 = source
                    .OrderBy(x => x.Length)//order by length first
                    .ThenBy(x => x);//if two items have the same length, then to order by their first character
            foreach (var item in query2)
            {
                Console.WriteLine(item);
                /*
                A
                ABC
                ZBC
                ASDSADSDA
                */
            }
        }
    }
}

```

## 4. Aggregate((acc,next)=>acc+", "+next)
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp7
{
    internal class Aggregate
    {
        /// <summary>
        /// .Aggregate((acc,next)=>acc+", "+next)
        /// </summary>
        /// <param name="args"></param>
        static void Main(string[] args)
        {
            string[] items = { "A", "B", "C", "D", "E" };
            string result = items.Aggregate((acc, next) => acc + ", " + next);//this LINQ statement works as same as below foreach loop
            Console.WriteLine(result);
            //string result2 = string.Empty;
            //foreach(var item in items)
            //{
            //    result2 = result2 + ", " + item;
            //}
            //Console.WriteLine(result2);


        }
    }
}
```
## 5. LINQ Query Syntax(LINQ查詢語法) + Join
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace LINQ
{
    internal class Program
    {

        static void Main(string[] args)
        {
            List<Book> books = new List<Book>
            {
                new Book("ASP.NET立即上手", 1, 620),
                new Book("聖經", 4, 160),
                new Book("食譜", 2, 88),
                new Book("旅遊日誌", 3, 238),
                new Book("Javascript從入門到放棄", 1, 228),
                new Book("Willy在哪裡?", 3, 900)
            };

            List<Category> categories = new List<Category>
            {
                new Category{Id = 1, CategoryName ="程式"},
                new Category{Id = 2, CategoryName ="飲食"},
                new Category{Id = 3, CategoryName ="旅遊"},
                new Category{Id = 4, CategoryName ="宗教"}
            };

            //LINQ Query Syntax(LINQ查詢語法)
            var query = (from book in books
                         join category in categories on book.CategoryId equals category.Id
                         select new BookResult { Name = book.Name, CategoryName = category.CategoryName, Price = book.UnitPrice })
                         .ToList();
            foreach (var item in query)
            {
                Console.WriteLine(item);
                //書名: ASP.NET立即上手           , 價錢: 620             , 類別: 程式
                //書名: 聖經              , 價錢: 160             , 類別: 宗教
                //書名: 食譜              , 價錢: 88              , 類別: 飲食
                //書名: 旅遊日誌                  , 價錢: 238             , 類別: 旅遊
                //書名: Javascript從入門到放棄    , 價錢: 228             , 類別: 程式
                //書名: Willy在哪裡 ?              , 價錢: 900             , 類別: 旅遊
            }
        }
        class BookResult
        {
            public string Name { get; set; }
            public string CategoryName { get; set; }
            public int Price { get; set; }
            public override string ToString()
            {
                return $"書名: {Name,-15}\t, 價錢: {Price,-15}\t, 類別: {CategoryName}";//-15 > 空格寬度;\t >  水平方向tab
            }
        }
        class Book
        {
            public string Name { get; set; }
            public int CategoryId { get; set; }
            public int UnitPrice { get; set; }
            public Book(string name, int categoryId, int unirPrice)//建構子 > 驗證輸入的內容是否符合格式
            {
                this.Name = name;
                this.CategoryId = categoryId;
                this.UnitPrice = unirPrice;
            }
        }
        class Category
        {
            public int Id { get; set; }
            public string CategoryName { get; set; }
        }
    }
}
```
    
## 6. Change PageNumbers
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace LINQ
{
    internal class Program
    {
        /// <summary>
        /// Present PageNumbers
        /// </summary>
        static void Main(string[] args)
        {
            int pageNumber = 2;//"PageNumber == 1" means to present the first page
            int pageRows = 10;//This means how many data should be preasented on a page.

            int skipRows = (pageNumber - 1) * pageRows;//To measure how many data show on a page
            string[] items2 = { "A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z" };

            items2 = items2
                     .Skip(skipRows)
                     .Take(pageRows)
                     .ToArray();
            foreach (var item in items2)
            {
                Console.WriteLine(item);
                //K
                //L
                //M
                //N
                //O
                //P
                //Q
                //R
                //S
                //T
            }
        }
    }
}
```

## 7. Empty, Append, Prepend
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp5
{
    internal class Program
    {
        /// <summary>
        /// 為什麼要使用Enumerable.Empty<int>() 實作 IEnumerable<int>? 而不直接使用class繼承IEnumerable<T>?
        /// 因為寫程式要儘量針對interface實作，
        /// </summary>
        /// <param name="args"></param>
        static void Main(string[] args)
        {
            //Create and Search
            List<string> list = new List<string>();//We can create a new list<T> by "new List<T>()"
            //不管回傳值是array還是List，針對介面實作就好
            IEnumerable<int> items = Enumerable.Empty<int>();//But we can only create a new IEnumerable<T> obj by using "Enumerable.Empty<T>()"

            var service = new MemberService();
            IEnumerable<Member> result = service.Search("ABC");//return an empty collection instead of null

            //加一個會員在最後面
            Member m1 = new Member { Name = "Tom" };
            result.Append(m1);//這是不對的寫法，因為Append會回傳一個新的集合，而不是void
            var result2 = result.Append(m1);//這是對的寫法

            //加一個會員在最前面
            Member m2 = new Member { Name = "Amy" };
            result2.Prepend(m2);//這是錯的寫法
            result2 = result2.Prepend(m2);//This is bad, it might cause bugs when many programmes co-use
                                          //the same method but this program might suddently add one extra
                                          //object then causing unexpected bugs.
            var result3 = result2.Append(m2);//This is good.

            foreach (var item in result2)
            {
                Console.WriteLine(item.Name);
                //Amy
                //Tom
            }

        }
    }

    public class Member
    {
        public string Name { get; set; }
    }
    public class MemberService
    {
        public IEnumerable<Member> Search(string name)
        {
            //more code need to be created here
            //
            //
            return Enumerable.Empty<Member>();//better than return "null" to prevent potential errors
        }
    }
}
```

## 8. All, Any, Contains
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp6
{
    internal class Program
    {
        /// <summary>
        /// All:
        /// 1. All operator is used to check whether all elements in a sequence satisfy given condition or not.
        /// 2. Return True if sequence is blank.
        /// 
        /// Any Operator:
        /// 1. Any operator is used to check whether any single element in a sequence satisfy a given condition or not.
        /// 2. Return False if sequence is blank.
        /// </summary>
        /// <param name="args"></param>
        static void Main(string[] args)
        {
            //All, Any
            int[] items = { 1, 2, 35, 4, 5, 6, 7, 8 };
            bool result = items.All(x => x < 36);
            bool result2 = items.Any(x => x > 7);
            Console.WriteLine((result, result2));//(True, True)

            //Contains
            string[] items3 = { "ABC", "FAQ", "EFG" };
            bool result3 = items3.Contains("F");
            Console.WriteLine(result3);//False

            string[] result4 = items3.Where(x => x.Contains("F")).ToArray();
            foreach (var item in result4)
            {
                Console.WriteLine(item);//FAQ, EFG
            }
        }
    }
}

```
    
## TBD
```
//FirstOrDefault, LastOrDefault, SingleOrDefault
```
