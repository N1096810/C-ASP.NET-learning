## Keywords
* Extension method
<hr>

## 1. Extension method
```C# = 
using NTUB.ClassLibrary1;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace NTUB.ConsoleApp1
{
    ///Extension Method
    ///Extension methods enable you to "add" methods to existing types without creating a new derived type,
    ///recompiling, or otherwise modifying the original type.
    internal class Program
    {
        static void Main(string[] args)
        {
            Member member1 = new Member();
            member1.ID = 101;
            member1.PhoneNumber = 0800000000;
            Console.WriteLine($"{member1.ID}, {member1.PhoneNumber}");

            Test test = new Test();
            test.Name = "asd";
            test.memberID = 123;

            test.Add("Hello");
            test.Delete(123);
            test.Insert(124);
            string result = result.StringHelper("");


        }
    }

    public class Test
    {
        public int memberID { get; set; }
        public string Name { get; set; }
        
        public void Add(string Name)
        {

        }
    }

    static class TestExtensions// Step 1. To create a "static class".
    {
        // Step 2. To create a "static method()"
        // Step 3. To add "this (class) (variable), input value" 
        public static void Delete(this Test objective, int memberID)
        {

        }

        public static void Insert(this Test objective2, int memberID)
        {

        }
    }

    static class StringExtensions
    {
        public static void StringHelper(this string stringHelper, int input)// An extension method to class "string"
        {

        }
    }
}

```
