## Keywords

## 1. Entity Framework CRUD
```C# =
using ConsoleApp3.EFModels;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace EntityFrameworkExample
{

    /// <summary>
    /// Server Name: .\SQL2019;
    /// DB Name: eStore;
    /// Account: sa5;
    /// PW: sa5;
    /// 1. Create a new folder named"EFModels".
    /// 2. Select "ADO.NET Entity Data Model" and change the name to "(databaseName)dbContext"
    /// 3. Select "Code First from Database"
    /// 4. Rename connect string name in "Save connect settings in App.Config as"
    /// 5. Select "Plurize or singularize generated object names"
    /// </summary>
    internal class Program
    {
        static void Main(string[] args)
        {
            SimpleCreateNews("CCC", "DDD");
            SimpleUpdateNews(8, "ABC", "CBA");
            ReadAllNews();
            SimpleDeleteNews(5);
        }

        static void SimpleCreateNews(string title, string newsContent)//Create
        {
            DBContext db = new DBContext();//It is required to create a unique dbContext for every database.
  
            News entity = new News { Title = title, NewsContent = newsContent, CreatedTime = DateTime.Now};
            
            db.News.Add(entity);//Add new data
            db.SaveChanges();//.SaveChanges() is a must have.
        }

        static void SimpleUpdateNews(int newID, string title, string newsContent)//Update
        {
            DBContext db = new DBContext();//It is required to create a unique dbContext for every database.
            News entity = db.News.Find(newID);
            if (entity != null)
            {
                entity.Title = title;
                entity.NewsContent = newsContent;
                db.SaveChanges();//.SaveChanges() is a must have.
            }
            else
            {
                throw new Exception("This ID doesn't exixt!");
            };
        }

        static void SimpleDeleteNews(int newID)//Delete
        {
            DBContext db = new DBContext();
            News entity = db.News.Find(newID);
            if (entity == null) return;//If entity == null, then do nothing.
            db.News.Remove(entity);//If entity != null, then proceed.
            db.SaveChanges();//.SaveChanges() is a must have.
        }

        static void ReadAllNews()//Read
        {
            DBContext db = new DBContext();//AsNoTracking() > A bit improve its operating speed by disabling changes tracking
            //List<News> showMeAllNews = db.News.AsNoTracking().OrderByDescending(x => x.Id).ToList();//Order by Decending
            //List<News> showMeAllNews = db.News.AsNoTracking().OrderBy(x => x.Id).ToList();//Order by Ascending
            List<News> showMeAllNews = db.News.AsNoTracking().Where(x=>x.Id>3).OrderBy(x => x.Id).ToList();//List items when ID only > 3 and orde by Ascending

            foreach (News items in showMeAllNews)
            {
                string message = $"ID={items.Id}, NewTitle={items.Title}, Title={items.CreatedTime}";
                Console.WriteLine(message);
            }
        }
    }
}
```

## 2. EFModels
```C# =
//City.cs
namespace ConsoleApp3.EFModels
{
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;
    using System.Data.Entity.Spatial;

    public partial class City
    {
        public int Id { get; set; }

        [Required]
        [StringLength(10)]
        public string Name { get; set; }

        public int DisplayOrder { get; set; }
    }
}
```
```C# =
//DBContext.cs
using System;
using System.ComponentModel.DataAnnotations.Schema;
using System.Data.Entity;
using System.Linq;

namespace ConsoleApp3.EFModels
{
    public partial class DBContext : DbContext
    {
        public DBContext()
            : base("name=EStoreConnectStringNamedByMyself")
        {
        }

        public virtual DbSet<City> Cities { get; set; }
        public virtual DbSet<News> News { get; set; }

        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
        }
    }
}
```
```C# =
//News.cs
namespace ConsoleApp3.EFModels
{
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;
    using System.Data.Entity.Spatial;

    public partial class News
    {
        public int Id { get; set; }

        [Required]
        [StringLength(50)]
        public string Title { get; set; }

        [Required]
        public string NewsContent { get; set; }

        public DateTime CreatedTime { get; set; }
    }
}
```
