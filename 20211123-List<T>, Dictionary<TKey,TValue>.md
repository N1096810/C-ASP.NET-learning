## Keywords
* List<T>
* Dictionary<TKey,TValue>
<hr>

## 1. List of interger
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp4
{
    internal class List
    {
        /// <summary>
        /// List<type> = new List<type>();
        /// </summary>
        /// <param name="args"></param>
        static void Main(string[] args)
        {
            List<int> items = new List<int>();//List of interger

            items.Add(6);//(6)
            items.Add(2);//(6, 1)

            int count = items.Count;// count current items number
            Console.WriteLine(count);//2

            items.RemoveAt(0);// remove first items
            count = items.Count;
            Console.WriteLine(count);//1

            items.Clear();// clear all items
            count = items.Count;
            Console.WriteLine(count);//0

            items.Add(31);
            items.Add(445);
            items.Add(578);
            items.Insert(0, 100);//.Insert(position, value)
            count = items.Count;
            Console.WriteLine(count);//4

            bool has5 = items.Contains(31);
            Console.WriteLine(has5);//true

            foreach (int item in items)
            {
                Console.WriteLine(item);//100 31 445 578
            }
        }
    }
}
```

## 2. List of Objective
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp4
{
    internal class List
    {
        /// <summary>
        /// List<type> = new List<type>();
        /// </summary>
        /// <param name="args"></param>
        static void Main(string[] args)
        {
            List<Product> items2 = new List<Product>();
            items2.Add(new Product { Name = "A01", Price = 10, Qty = 2 });//Add a new objective
            items2.Add(new Product { Name = "A02", Price = 5, Qty = 3});

            foreach(Product abc in items2)//"abc" is a new objective with type "Product"
            {
                string message = $"Prod Name = {abc.Name}, Prod Price = {abc.Price}, Prod Qty = {abc.Qty}";
                Console.WriteLine(message);
                //Prod Name = A01, Prod Price = 10, Prod Qty = 2
                //Prod Name = A02, Prod Price = 5, Prod Qty = 3
            }
        }
    }

    public class Product
    {
        public string Name { get; set; }
        public int Price { get; set; }
        public int Qty { get; set; }
    }
}
```

## 2. Dictionary<TKey,TValue>
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    /// <summary>
    /// To Represents a collection of keys and values fast.
    /// </summary>
    internal class Dictionary
    {
        static void Main(string[] args)
        {
            Dictionary<int, string> cities = new Dictionary<int, string>();//only two inputs are allowed => (key, value)

            cities.Add(101, "Taipei");//(key, value)
            cities.Add(102, "Chiayi");
            cities.Add(103, "Hsinchu");
            cities.Add(104, "Taipei");
            Console.WriteLine(cities.Count());//count inventory numbers//4

            cities[103] = "Keelung";//overide a value

            bool contain105 = (cities.ContainsKey(105))? true : false;//keys are unique
            Console.WriteLine(contain105);//false

            foreach (int iAmthekey in cities.Keys)
            {
                string inputValue = cities[iAmthekey];
                Console.WriteLine($"key = {iAmthekey}, value = {inputValue}");
                //key = 101, value = Taipei
                //key = 102, value = Chiayi
                //key = 103, value = Keelung
                //key = 104, value = Taipei
                
            }

            bool containTaipeiCity = (cities.ContainsValue("Taipei")) ? true : false;//"values" can be duplicate, because many items might all contains value "Taipei" but with different "Key".
            Console.WriteLine(containTaipeiCity);//true
            foreach(int iAmthekey in cities.Keys)
            {
                string inputValue2 = cities[iAmthekey];
                if (containTaipeiCity == true)
                {
                    Console.WriteLine($"key = {iAmthekey}, value = {inputValue2 == "Taipei"}");
                    //key = 101, value = True
                    //key = 102, value = False
                    //key = 103, value = False
                    //key = 104, value = True
                }
            }

        }
    }
}

```

<hr>

## References
[C# Dictionary的用法](https://www.w3cschool.cn/csharp/csharp-86c42por.html#:~:text=C%23%20Dictionary%E7%9A%84%E7%94%A8%E6%B3%95.%20%E5%9C%A8C%23%E4%B8%AD%EF%BC%8CDictionary%E7%9A%84%E4%B8%BB%E8%A6%81%E7%94%A8%E9%80%94%E6%98%AF%E6%8F%90%E4%BE%9B%E5%BF%AB%E9%80%9F%E7%9A%84%E5%9F%BA%E4%BA%8E%E5%85%BC%E8%81%8C%E7%9A%84%E5%85%83%E7%B4%A0%E6%9F%A5%E6%89%BE%E3%80%82.%20Dictionary%E7%9A%84%E7%BB%93%E6%9E%84%E4%B8%80%E8%88%AC%E6%98%AF%E8%BF%99%E6%A0%B7%E7%9A%84%EF%BC%9ADictionary%3C,%5Bkey%5D%2C%20%5Bvalue%5D%3E%20%EF%BC%8C%E5%AE%83%E5%8C%85%E5%90%AB%E5%9C%A8System.Collections.Generic%E5%90%8D%E7%A9%BA%E9%97%B4%E4%B8%AD%E3%80%82.%20%E5%9C%A8%E4%BD%BF%E7%94%A8Dictionary%E5%89%8D%EF%BC%8C%E4%BD%A0%E5%BF%85%E9%A1%BB%E5%AF%B9%E5%AE%83%E7%9A%84%E9%94%AE%E7%B1%BB%E5%9E%8B%E5%92%8C%E5%80%BC%E7%B1%BB%E5%9E%8B%E8%BF%9B%E8%A1%8C%E5%A3%B0%E6%98%8E%E3%80%82.)<br>
[Dictionary<TKey,TValue> Class](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=net-6.0)<br>
