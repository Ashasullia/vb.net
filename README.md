#vb.net<br>
using System;<br>
using System.Threading;<br>
namespace ThreadPoolProg<br>
{<br>
    class ThreadPoolProg<br>
    {<br>
        public void TreadFun1(object obj)<br>
        {<br>
            int loop = 0;v<br>
            for (loop = 0; loop <= 4; loop++)<br>
            {<br>
                Console.WriteLine("Thread1 is executing");<br>
            }<br>
        }<br>
        public void TreadFun2(object obj)<br>
        {<br>
            int loop = 0;<br>
            for (loop = 0; loop <= 4; loop++)<br>
            {<br>
                Console.WriteLine("Thread2 is executing");<br>
            }<br>
        }<br>
        public static void Main()<br>
        {<br>
            ThreadPoolProg TP = new ThreadPoolProg();<br>
            for (int i = 0; i < 2; i++)<br>
            {<br>
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.TreadFun1));<br>
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.TreadFun2));<br>
            }<br>
            Console.ReadKey();<br>
        }<br>
    }<br>
    
    
    using System;<br>
namespace Exercises<br>
{<br>
    class Fraction : IComparable<br>
    {int n,z;<br>
        public Fraction(int z, int n)<br>
        {<br>
            this.z = z;<br>
            this.n = n;<br>
        }<br>
        public static Fraction operator +(Fraction a, Fraction b)<br>
        {<br>
            return new Fraction(a.z * b.n + a.n * b.z, a.n * b.n);<br>
        }<br>
        public static Fraction operator *(Fraction a, Fraction b)<br>
        {<br>
            return new Fraction(a.z * b.z, a.n * b.n);<br>
        }<br>
        public int CompareTo(object obj)<br>
        {<br>
            Fraction f = (Fraction)obj;<br>
            if ((float)z / n < (float)f.z / f.n)<br>
                return -1;<br>
            else if ((float)z / n > (float)f.z / f.n)<br>
                return 1;<br>
            else<br>
                return 0;<br>
        }<br>
        public override string ToString()<br>
        {<br>
            return z + "/" + n;<br>
        }<br>
    }<br>
    class ICompInterface<br>
        public static void Main()<br>
       
    {
        public static void Main()<br>
        {<br>

        Fraction[] a = {<br>
 new Fraction(5,2),<br>
 new Fraction(29,6),<br>
 new Fraction(4,5),<br>
 new Fraction(10,8),<br>
 new Fraction(34,7)<br>
 };<br>
            Array.Sort(a);<br>
            Console.WriteLine("Implementing the IComparable Interface in " + "Displaying  Fractions : ");<br>
            foreach (Fraction f in a)<br>
            {<br>
                Console.WriteLine(f + " ");<br>
            }<br>
            Console.WriteLine();<br>
            Console.ReadLine();<br>
        }<br>
    }<br>
}<br>


using System;<br>
using System.IO;<br>
namespace FileRead<br>
{<br>
    class FileRead<br>
    {<br>
        public static void Main()<br>
        {<br>
            string fileName;<br>
            while (true)<br>
            {<br>
                Console.WriteLine("\n.......MENU......\n");<br>
                Console.WriteLine("\n1.create a file");<br>
                Console.WriteLine("\n2.existing of the file");<br>
                Console.WriteLine("\n3.read the content of the file");<br>
                Console.WriteLine("\n4.exit");<br>
                Console.WriteLine("\nEnter your choice:");<br>
                int ch = int.Parse(Console.ReadLine());<br>
                switch (ch)<br>
                {<br>
                    case 1 :<br>
                        Console.WriteLine("\n enter the file name to create:");<br>
                fileName = Console.ReadLine();<br>
                Console.WriteLine("\n Write the content to the file:\n");<br>
                string r = Console.ReadLine();<br>
                using (StreamWriter fileStr = File.CreateText(fileName))<br>
                {<br>
                    fileStr.WriteLine(r);<br>
                }<br>
                Console.WriteLine("file is created.....");<br>
                break; <br>
                case 2:<br>
                    Console.Write("\n enter the file name:");<br>
                fileName = Console.ReadLine();<br>
                if (File.Exists(fileName))<br>
                {<br>
                    Console.WriteLine("file exists..");<br>
                }<br>
                else<br>
                {<br>
                    Console.WriteLine("file does not exits in the current directory!\n");<br>
                }<br>
                break;<br>
                case 3 :<br>
                     Console.WriteLine("enter the file name to read the contents:\n");<br>
                fileName = Console.ReadLine();<br>
                if (File.Exists(fileName))<br>
                {<br>
                    using (StreamReader sr = File.OpenText(fileName))<br>
                    {<br>
                        string s = " ";<br>
                        Console.WriteLine("here is the content of the file\n");<br>
                        while ((s = sr.ReadLine()) != null)<br>
                        {<br>
                            Console.WriteLine(s);<br>
                        }<br><br>
                        Console.WriteLine(" ");<br>
                    }<br>
                }<br>
                else<br>
                {<br>
                    Console.WriteLine("file does not exists");<br>
                }<br>
                break;<br>
              case 4 :<br>
                     Console.WriteLine("\nexisting...");<br>
                return;<br>
                default :<br>
                     Console.WriteLine("\n invalid choice");<br>
                break;<br>
            }<br>
        }
    }<br>
}<br>
}<br>


using System;<br>
using System.IO;<br>
namespace file_read<br>
{<br>
    class file_read<br>
    {<br>
        public static void Main()<br>
        {<br>
            string file1;<br>
            string file2;<br>
            Console.WriteLine("enter the first file path:");<br>
            file1 = Console.ReadLine();<br>
            Console.WriteLine("enter the second file path:");<br>
            file2 = Console.ReadLine();<br>
            if (!File.Exists(file1))<br>
            {<br>
                Console.WriteLine("first file does not exists!");<br>
            }<br>
            else if (!File.Exists(file2))<br>
            {<br>
                Console.WriteLine("second file does not exists!");<br>
            }<br><br>
            else if (File.ReadAllText(file1) == File.ReadAllText(file2))<br>
            {<br>
                Console.WriteLine("both files contains the same");<br>
            
            }<br>
            else<br>
            }<br>
            {<br>
                Console.WriteLine(" contents of file are not same");<br>
            }<br>
        }<br>
    }<br>
}<br>


           
