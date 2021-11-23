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
