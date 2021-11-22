## Keywords
* Number Swap & Console.WriteLine(no1, no2)
* string.IsNullOrEmpty(value) vs string.IsNullOrWhitespace(value)
* Escape Characters
* trim
* Substring
* Contains(), ToLower(), ToUpper()
* Length
* StartsWith(String), EndsWith(String)
* .IndexOf(), .LastIndexOf(), .IndexOfAny()
* String interpolation(字串插值)
<hr>

## 1.Number Swap & Console.WriteLine(no1, no2)
```C# =
            //Number Swap & Console.WriteLine(no1, no2)
            int a = 10;
            int b = 3;
            int temp = a;
            a = b;
            b = temp;
            Console.WriteLine((a, b).ToString()); // (3, 10)
            
            //Q.寫程式, 計算並顯示 120 除以 7 的商數, 餘數, 各是多少
            int value1 = 120;
            int quotient1 = value1 / 7;
            int remainder1 = value1 % 7;
            Console.WriteLine((quotient1, remainder1).ToString());//(17, 1)
            
            //Q.計算 9 與 202 分別是奇數或是偶數?
                        int value2 = 9;
            int value3 = 202;
            //is 9 even?
            if (value2 % 2 == 0)
            {
                Console.WriteLine(value2 + " is Even.");
            }
            else 
            {
                Console.WriteLine(value2 + " is Odd.");
            };//9 is Odd.

            //is 202 even?
            if (value3 % 2 == 0)
            {
                Console.WriteLine(value3 + " is Even.");
            }
            else
            {
                Console.WriteLine(value3 + " is Odd.");
            };//202 is Even.
```

## 2.string.IsNullOrEmpty(value) vs string.IsNullOrWhitespace(value)
```C# =
            string value1 = "";
            string value2 = null;
            string value3 = "123";
            string value4 = "    ";

            bool result = string.IsNullOrEmpty(value1);
            Console.WriteLine(result);//True
            result = String.IsNullOrEmpty(value2);
            Console.WriteLine(result);//True
            result = String.IsNullOrEmpty(value3);
            Console.WriteLine(result);//False
            result = String.IsNullOrEmpty(value4);
            Console.WriteLine(result);//False
            result = String.IsNullOrWhiteSpace(value4);
            Console.WriteLine(result);//True
```

## 3.Escape Characters => \" \\ \t \r \a @
```C# =
            //Escape Character => \"
            string test = "I am \"SuperMan\" ! ";
            Console.WriteLine(test);//I am "SuperMan" !

            //Escape Character => \\ @
            //No space allowed between @ and "
            string path = "c:\\temp\\a.doc";
            Console.WriteLine(path); //c:\temp\a.doc

            string path2 = @"c:\temp\a.doc";
            Console.WriteLine(path2);//c:\temp\a.doc

            //Escape Character => \t 水平方向tab
            string sentence = "I am \t superman";
            Console.WriteLine(sentence);//I am          superman

            //Escape Character => \r 回到最前方 \n 換行 @
            //No space allowed between @ and "
            string listItems = "item1 \n\ritem2 \n\ritem3";
            Console.WriteLine(listItems);
            /*
            item1
            item2
            item3
            */

            string listItems2 = @"item1
            item2
            item3";
            Console.WriteLine(listItems2);
            // Bad !!!! 字前面會多很多tab
            /*
            item1
                    item2
                    item3
             */

            string listItems3 = @"item1
item2
item3";
            Console.WriteLine(listItems3);
            /*
            item1
            item2
            item3
            */

            string query = @"select *
from Member
where Age > 20
Order By desc";
            Console.WriteLine(query);
            /*
            select *
            from Member
            where Age > 20
            Order By desc
            */
            
            //Q.
            /*
            宣告字串變數, 包含以下值, 並用 Console.WriteLine() 將它忠實地呈現在畫面上
            我是一個"好學生", 會乖乘練習寫作業
            */
            string sentence2 = @"我是一個""好學生"", 會乖乘練習寫作業";//pay attention to @" "" ";
            Console.WriteLine(sentence2);//我是一個"好學生", 會乖乘練習寫作業
            
            //Q.
                        string sentence4 = @"<select>
    <option value=""1"">台北</option>
    <option value=""2"">台中</option>
</select>";
            Console.WriteLine(sentence4);
            /*
            <select>
                <option value="1">台北</option>
                <option value="2">台中</option>
            </select>
            */
         
```

## 4.trim
```C# =
            //trim
            //Delete spaces in front of/behind a sentence
            string sentence = "   This is a book.   ";
            Console.WriteLine(sentence);//"   This is a book.   ";

            string trimLeft = sentence.TrimStart();
            Console.WriteLine(trimLeft);//"This is a book. "

            string trimRight = sentence.TrimEnd();
            Console.WriteLine(trimRight);//" This is a book."

            string trimBothLeftAndEnd = sentence.Trim();
            Console.WriteLine(trimBothLeftAndEnd);//"This is a book."

            string test = null;//!!!!!!!!!!!!!!!!!!!!!!!!!!!
            Console.WriteLine(test);//Object reference not set to an instance of an object.

```

## 5. Substring
```C# =
            //Substring(start position, capture length)
            string newContent = "[健康]你不可不知的十大健康好習慣";
            string newCapture = newContent.Substring(0, 4);
            Console.WriteLine(newCapture);//[健康]

            string newCapture2 = newContent.Substring(999, 4);//Error => 長度超出字串長度  
```

## 6. Contains(), ToLower(), ToUpper()
```C# =
            //Must validate whether the values are "null" or not first before applying "ToLower() or ToUpper()"
            string account = "Barry";
            string pw = "barrypw123";
            bool containsAccount = pw.Contains(account.ToLower());
            Console.WriteLine(containsAccount); //true

            if (containsAccount == true)
            {
                Console.WriteLine("PW can't contain your account!");
            }
            else
            {
                Console.WriteLine("PW is accepted.");
            }//PW can't contain your account!
```

## 7.Length
```C# =
    internal class Program
    {
        static void Main(string[] args)
        {
            //length
            //length 是屬性，所以後面不用加()
            string pw = "absdferwlekrj";
            Console.WriteLine(pw.Length);//13

            Console.WriteLine(countLength("12346589798798465")); //密碼長度錯誤
        }

        public static string countLength(string i)
        {
            if ((i.Length < 5) || (i.Length > 10))
            {
                string alert = "密碼長度錯誤";
                return alert;
            }
            else
            {
                string alert2 = "密碼長度為" + i.Length;
                return alert2;
            };
        }
    }
```

## 8. StartsWith(String), EndsWith(String)
```C# =
            //.StartsWith(String)
            //Determines whether the beginning of this string instance matches the specified string.
            string url = "http://www.bing.com/";
            bool isHttps = url.StartsWith("https://");
            if (isHttps == false) 
            {
                Console.WriteLine("Your domain must starts with \"https://\", and please try again.");
            }//Your domain must starts with "https://", and please try again.

            //.EndsWith(String)
            //Determines whether the end of this string instance matches a specified string.
            bool isDotCom = url.EndsWith(".com");
            if (isDotCom == false) 
            {
                Console.WriteLine("Correct.");
            };//Correct.
```

## 9. .IndexOf(), .LastIndexOf(), .IndexOfAny()
```C# =
            //.IndexOf(), .LastIndexOf()
            /*
            Reports the zero-based index of the first occurrence of a specified Unicode character
            or string within this instance.
            The method returns -1 if the character or string is not found in this instance.
            
            .IndexOf() 會回傳第一個符合的位置，如果第一個字就符合，則傳回0；
            若完全不符合，則傳回-1。因此可利用程式判斷回傳值是否小於0以判斷該字串
            是否包含想找的char / string。

            .LastIndexOf()則是從尾往前找。

            */

            string sentence = "100025台北市中正區濟南路一段321號";
            int location = sentence.IndexOf("台北市");
            int location2 = sentence.IndexOf("新竹市");

            if ( location < 0) 
            { 
                Console.WriteLine("該地址位於台北市");
            }
            else
            {
                Console.WriteLine("該地址不在台北");
            }//該地址不在台北

            if (location2 < 0)
            {
                Console.WriteLine("該地址位於新竹市");
            }
            else
            {
                Console.WriteLine("該地址不在新竹市");
            }//該地址位於新竹市

            //.IndexOfAny()
            /*
            Reports the index of the first occurrence in this instance
            of any character in a specified array of Unicode characters.
            The method returns -1 if the characters in the array are not
            found in this instance.
            */

            string sentence2 = "This is a book.";
            int location3 = sentence.IndexOfAny(new char[] { 'a', 's' });//Watch out the '' vs ""

            if (location3 < 0) 
            {
              Console.WriteLine("There is no any \"a\" or \"s\" in the string.");
            }//There is no any "a" or "s" in the string.

```

## 10. String interpolation(字串插值)
```C# =
    internal class Program
    {
        static void Main(string[] args)
        {
            for (int firstNumber1 = 2; firstNumber1 <= 9; firstNumber1++)
            {
                /// Because method "SingleList" and " method "Main" are within in the same class "Program".
                /// So "SingleList" can be called directly.
                SingleList(firstNumber1);
                Console.WriteLine();
            }
        }

        static void SingleList(int firstNumber2)
        {
            for (int secondNumber = 1; secondNumber <= 9; secondNumber++)
            {
                //format 1
                string message = firstNumber2 + "*" + secondNumber + "=" + (firstNumber2 * secondNumber);
                Console.WriteLine(message);

                //format 2
                string template = "{0} 乘以 {1}, 答案是 {2}";
                string message2 = string.Format(template, firstNumber2, secondNumber, firstNumber2 * secondNumber);
                Console.WriteLine(message2);

                //format3 => String interpolation
                string message3 = $"{firstNumber2*secondNumber} = {firstNumber2} * {secondNumber}";
                Console.WriteLine(message3);
            };
        }
    }
```
