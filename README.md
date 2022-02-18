#vb.net
using System;
using System.Threading;
namespace ThreadPoolProg
{
    class ThreadPoolProg
    {
        public void TreadFun1(object obj)
        {
            int loop = 0;
            for (loop = 0; loop <= 4; loop++)
            {
                Console.WriteLine("Thread1 is executing");
            }
        }
        public void TreadFun2(object obj)
        {
            int loop = 0;
            for (loop = 0; loop <= 4; loop++)
            {
                Console.WriteLine("Thread2 is executing");
            }
        }
        public static void Main()
        {
            ThreadPoolProg TP = new ThreadPoolProg();
            for (int i = 0; i < 2; i++)
            {
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.TreadFun1));
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.TreadFun2));
            }
            Console.ReadKey();
        }
    }
    using System;
namespace Exercises
{
    class Fraction : IComparable
    {
        int z, n;
        public Fraction(int z, int n)
        {
            this.z = z;
            this.n = n;
        }
        public static Fraction operator +(Fraction a, Fraction b)
        {
            return new Fraction(a.z * b.n + a.n * b.z, a.n * b.n);
        }
        public static Fraction operator *(Fraction a, Fraction b)
        {
            return new Fraction(a.z * b.z, a.n * b.n);
        }
        public int CompareTo(object obj)
        {
            Fraction f = (Fraction)obj;
            if ((float)z / n < (float)f.z / f.n)
                return -1;
            else if ((float)z / n > (float)f.z / f.n)
                return 1;
            else
                return 0;
        }
        public override string ToString()
        {
            return z + "/" + n;
        }
    }
    class ICompInterface
    {
        public static void Main()
        {

        Fraction[] a = {
 new Fraction(5,2),
 new Fraction(29,6),
 new Fraction(4,5),
 new Fraction(10,8),
 new Fraction(34,7)
 };
            Array.Sort(a);
            Console.WriteLine("Implementing the IComparable Interface in " + "Displaying  Fractions : ");
            foreach (Fraction f in a)
            {
                Console.WriteLine(f + " ");
            }
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
using System;
using System.IO;
namespace FileRead
{
    class FileRead
    {
        public static void Main()
        {
            string fileName;
            while (true)
            {
                Console.WriteLine("\n.......MENU......\n");
                Console.WriteLine("\n1.create a file");
                Console.WriteLine("\n2.existing of the file");
                Console.WriteLine("\n3.read the content of the file");
                Console.WriteLine("\n4.exit");
                Console.WriteLine("\nEnter your choice:");
                int ch = int.Parse(Console.ReadLine());
                switch (ch)
                {
                    case 1 :
                        Console.WriteLine("\n enter the file name to create:");
                fileName = Console.ReadLine();
                Console.WriteLine("\n Write the content to the file:\n");
                string r = Console.ReadLine();
                using (StreamWriter fileStr = File.CreateText(fileName))
                {
                    fileStr.WriteLine(r);
                }
                Console.WriteLine("file is created.....");
                break; 
                case 2:
                    Console.Write("\n enter the file name:");
                fileName = Console.ReadLine();
                if (File.Exists(fileName))
                {
                    Console.WriteLine("file exists..");
                }
                else
                {
                    Console.WriteLine("file does not exits in the current directory!\n");
                }
                break;
                case 3 :
                     Console.WriteLine("enter the file name to read the contents:\n");
                fileName = Console.ReadLine();
                if (File.Exists(fileName))
                {
                    using (StreamReader sr = File.OpenText(fileName))
                    {
                        string s = " ";
                        Console.WriteLine("here is the content of the file\n");
                        while ((s = sr.ReadLine()) != null)
                        {
                            Console.WriteLine(s);
                        }
                        Console.WriteLine(" ");
                    }
                }
                else
                {
                    Console.WriteLine("file does not exists");
                }
                break;
              case 4 :
                     Console.WriteLine("\nexisting...");
                return;
                default :
                     Console.WriteLine("\n invalid choice");
                break;
            }
        }
    }
}
}



           
