# LengthOf1s
using System;
using System.Text;
using System.IO;

namespace AlgorithmForTheTest
{
    class Program
    {
        static void Main(string[] args)
        {
            string str = string.Empty;
            using (StreamReader reader = new StreamReader("input.txt", Encoding.Default))
                str = reader.ReadToEnd();

            char[] array = new char[str.Length];
            array = str.ToCharArray();

            Console.WriteLine(str);
            Console.WriteLine(str.Length);


            int count = 0;
            int temp = 0;

            for (int i = 0; i < str.Length; i++)
            {
                if (array[i] == '1')
                {
                    count++;
                    if (i == str.Length - 1)
                        temp = count;
                }
                else
                {
                    if (count > temp)
                    {
                        temp = count;

                    }
                    count = 0;
                }
            }



            FileStream file1 = new FileStream("output.txt", FileMode.Create); // створюємо файловий потік
            StreamWriter writer = new StreamWriter(file1); // створюємо «потоковий письменник» і пов'язуємо його з файловим потоком
            writer.Write(temp); // записуємо в файл
            writer.Close(); // закриваємо потік. Чи не закривши потік, у файл нічого не запишеться
            Console.WriteLine(temp);


            Console.ReadKey();

        }
    }
}
