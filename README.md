# hash-table-class-gopala01
hash-table-class-gopala01 created by GitHub Classroom
using System;

namespace hash_table_classGopala01
{
    class Hashing
    {
        public int[] Hashtable = new int[] { 12 };
        private int place = 0;
        public void Add()
        {
            Console.WriteLine("What value would you like to add?");
            int value = Convert.ToInt32(Console.ReadLine());
            place = value % 11;
            for (int i = 0; i < 12; i++)
            {
                if (Hashtable[place] != -1 && Hashtable[place] != -2)
                {
                    place = (place + 1) % 11;
                    i = i + 1;
                    if (i > 11)
                    {
                        Console.WriteLine("This cannot be done");
                    }
                }
                else if (Hashtable[place] == -1 || Hashtable[place] == -2)
                {
                    Hashtable[place] = value;
                }
            }
        }

        public void Search()
        {
            Console.WriteLine("What would you like to look for?");
            int item = Convert.ToInt32( Console.ReadLine());
            if (Hashtable[1] == item)
            {
                Console.WriteLine("Item " + item + "Found");
                Console.ReadLine();
            }
            else
            {
                place++;
                for (int place = 0; place < Hashtable.Length; place++)
                {
                    if (Hashtable[place] == item)
                    {
                        Console.WriteLine("item found in " + Hashtable[place]);
                        Console.ReadLine();
                    }
                }
            }

        }

        public void Delete()
        {
            Console.WriteLine("What would you like to delete?");
            int value = Convert.ToInt32(Console.ReadLine());
            place = value % 11;

            if (Hashtable[place] == value)
            {
                Hashtable[place] = -1;
            }
            else if (Hashtable[place] != value)
            {
                
                for (int i = place; i < Hashtable.Length; i++)
                {
                    i++;
                    place++;
                    if (Hashtable[place] == -1)
                    {
                        Console.WriteLine("Not found");
                    }
                }
            }
        }

        public void Show()
        {

            Console.WriteLine(Hashtable);
        }

    }

    
    class Program
    {
        
        static void Main(string[] args)
        {
            Hashing Hash1 = new Hashing();

            Console.WriteLine("What would you like to do?");
            Console.WriteLine("<1> Add");
            Console.WriteLine("<2> Search");
            Console.WriteLine("<3> Delete");
            Console.WriteLine("<4> Return all values");
            int choice = Convert.ToInt32(Console.ReadLine());

            if (choice == 1)
            {
                Hash1.Add();
            }
            else if (choice == 2)
            {
                Hash1.Search();
            }
            else if (choice == 3)
            {
                Hash1.Delete();
            }
            else if (choice == 4)
            {
                Hash1.Show();
            }
            
        }
    }

    
}
