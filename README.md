using System;
using System.Security.Cryptography.X509Certificates;

namespace ConsoleApp4
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int month;
            Random rnd = new Random();
            int[] pole = new int[10];
            for (int i = 0; i < 10; i++) {
                month = rnd.Next(1, 13);

                pole[i] = month;
                Console.WriteLine(month);
                
            }
            Console.WriteLine(Prumer(pole) );
            Console.WriteLine(Delen(pole));
            Console.WriteLine(Nejmen(pole));

            List<Uzivatel> uzivatels = new List<Uzivatel>();
            uzivatels.Add(Uzivatel.CreateUzivatel("aaaa", "asadasdsd"));
            uzivatels.Add(Uzivatel.CreateUzivatel("aaaa", "adaasdasd"));
            uzivatels.Add(Uzivatel.CreateUzivatel("aaaa", "asaasdasd"));
            uzivatels.Add(Uzivatel.CreateUzivatel("aaaa", "asdasdasdas"));
            uzivatels.Add(Uzivatel.CreateUzivatel("aaaa", "adasdasda"));
            uzivatels.Add(Uzivatel.CreateUzivatel("aaaa", "aasdasda"));

            uzivatels.Sort();
            foreach (Uzivatel uzivatel in uzivatels) 
            {
                Console.WriteLine(uzivatel.ToString());
            }



        }
        public static double Prumer(int[] pole)
        {
            int suma = 0;
            foreach (int x in pole) 
            {
                suma += x;
            }
            return (double)suma / pole.Length;
        }
        public static bool Delen(int[] pole)
        {
            int x = 0;
            for (int i = 0; i < 10; i++) {
                if (pole[i] % 90 == 0) return true;
            }
            return false;
            
        }
        public static int Nejmen(int[] pole)
        {
            int minint = pole[0];
            int maxint = pole[0];
            foreach (int value in pole)
            {
                if (value < minint) minint = value;
                if (value > maxint) maxint = value;
            }
            return minint;

        }
    }
}



using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp4
{
    internal class Uzivatel: IComparable<Uzivatel>
    {
        private string nickname;
        private string heslo;

        public int CompareTo(Uzivatel u)
        {
            if (u == null) return 1;
            return string.Compare(this.nickname, u.nickname);
        }

        private Uzivatel(string nickname, string heslo)
        {
            this.nickname = nickname;
            this.heslo = heslo;
        }

        public string Heslo { get => heslo; }
        public string Nickname { get => nickname; }

        public static Uzivatel CreateUzivatel(string nickname, string heslo)
        {
            if (nickname.Length < 3 || heslo.Length < 5)
            {
                throw new ArgumentException("Nevhodna");

            }
            return new Uzivatel(nickname, heslo);
        }
        public override string ToString()
        {
            return base.ToString();
        }

    }
}
