## 1. Interface
```C# =
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    internal class Interface
    {
        static void Main(string[] args)
        {
            Door door1 = new Door { Name = "FrontDoor"};
            Box box1 = new Box { Name = "Big box" };
            Console.WriteLine(NewMethod.OpenIt(door1));//FrontDoor is opened.
            Console.WriteLine(NewMethod.OpenIt(box1));// Big box is opened.

            PencilBox pencilBox1 = new PencilBox { Name = "My pencilbox", Contents = "two pens and one ruler" };
            Console.WriteLine(NewMethod.OpenIt(pencilBox1));//My pencilbox containing two pens and one ruler is opened.
        }


    }

    interface IOpenable
    {
        string Open();
    }

    class Door: IOpenable
    {
        public string Name { get; set; }
        public string Open()
        {
            return $"{Name} is opened.";
        }
    }

    class Box: IOpenable//Class "Box" can't inherit class "Door".
    {
        public string Name { get; set; }
        public string Open()
        {
            return $"{Name} is opened.";
        }
    }

    class PencilBox: Box, IOpenable// inherit (class), (interface)
    {
        public void Box(string contents)
        {
            this.Contents = contents;
        }
        public string Contents { get; set; }
        public string ShowContents()
        {
            return $"{Name} containing {Contents}";
        }
        public string Open()
        {
            return this.ShowContents() + $" is opened.";
        }

    }
    
    class NewMethod
    {
        public static string OpenIt(IOpenable obj)//An objective will be inputted.
        {
            return obj.Open();
        }
    }

}
```
