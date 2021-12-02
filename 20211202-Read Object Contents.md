## Print out all properties of objects
```C# =
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
        /// Select > used to change type
        /// </summary>
        /// <param name="args"></param>
        //static void Main(string[] args)
        //{
        //    IEnumerable<int> items = Enumerable.Range(0, 10);

        //    //IEnumerable<string> result = items.Select(x => "No." + x.ToString("000"));//No.000
        //    IEnumerable<string> result = items.Select(x => $"No.{x:00}");//No.00
        //    foreach (var item in result)
        //    {
        //        Console.WriteLine(item);
        //    }
        //}

        static void Main(string[] args)
        {
            IEnumerable<int> items = Enumerable.Range(0, 10);
            var query = items
                        .Where(x => x % 4 == 0)
                        .Select(x => new Country { Id = x, Name = "This is City No." + x });

            foreach (var item in query)
            {
                Console.WriteLine($"ID = {item.Id}, {item.Name}");//method 1
                Console.WriteLine(item.ToString());//method 2
                Console.WriteLine(item.ThisIsATest());//method 3
                Console.WriteLine("***");
                /*
                ID = 0, This is City No.0
                ID: 0, Name: This is City No.0
                ID: 0, Name: This is City No.0
                ***
                ID = 4, This is City No.4
                ID: 4, Name: This is City No.4
                ID: 4, Name: This is City No.4
                ***
                ID = 8, This is City No.8
                ID: 8, Name: This is City No.8
                ID: 8, Name: This is City No.8
                ***
                */
            }
        }

        public class Country
        {
            public int Id { get; set; }
            public string Name { get; set; }

            public override string ToString()//Use "Override" to amend the contents of the original "ToString()" method.
            {
                return $"ID: {Id}, Name: {Name}";
            }

            public string ThisIsATest()
            {
                return $"ID: {Id}, Name: {Name}";
            }
        }
    }
}
```
