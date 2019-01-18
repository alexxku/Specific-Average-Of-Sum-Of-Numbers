# Specific-Average-Of-Sum-Of-Numbers
Using C# console application, input the number of test with scores and average them.


using System;

namespace SpecificSumofNumAverage
{

    class Program
    {
        static void Main(string[] args)
        {
            //Label reference
            Start:

            //Variable Declarations
            int NumofScores;
            double totalSum, totalAverage;

            Console.Write("Enter the amount of test scores to be graded: ");
           
            //Tries user input
            try
            {
                NumofScores = Convert.ToInt32(Console.ReadLine());

            }
            //Catches exception error
            catch (Exception error)
            {
                Console.WriteLine($"\n{error.Message.ToString()}\n");
                //Goes to reference label
                goto Start;
            }

            //Assign and call method
            totalSum = sumValue(NumofScores);
            //Divide total sum with 10 to get average
            totalAverage = totalSum / NumofScores;
            Console.WriteLine($"\nTotal Value: {totalAverage}");
            //Average conditions to get letter grade
            letterGrade(totalAverage);
            Console.ReadLine();
        }




        //Add values 
        static double sumValue(int times)
        {
            //Variables declaration and assignment for sumValue()
            double sum;
            double total = 0;

            Console.WriteLine("\nEnter ten values from 0 to 100.");

            //Repeat value entry 10 times
            for (int count = 0; count < times; count++)
            {
                //Label reference
                Start:

                Console.Write($"\nNumber {count + 1}: ");

                //Exception handler. Going to try the following block of code.
                try
                {
                    //Ask user for input and convert to double
                    sum = Convert.ToDouble(Console.ReadLine());
                    //Sum assignment with user input and sum arguements.
                    sum = repeatV(sum, count);
                    //total assignment with increasing input sum for every loop
                    total += sum;
                }
                //Catches error
                catch (Exception error)
                {
                    Console.WriteLine($"\n{error.Message.ToString()}");

                    //Goes to reference label
                    goto Start;
                }
            }
            //Return total
            return total;
        }

        //Looping negative and large numbers with two parameters for sum and count
        static double repeatV(double x, int y)
        {
            //Loop conditions
            while (x < 0 || x > 100)
            {
                Console.WriteLine("\nInvalid Value.");
                Console.Write($"\nNumber {y + 1}: ");
                x = Convert.ToDouble(Console.ReadLine());
            }

            //Return x
            return x;
        }
    
        //Conditions for letter grade
        static void letterGrade(double average)
        {
            if (average < 60)
            {
                Console.WriteLine("\nGrade: F");
            }
            else if (average < 70)
            {
                Console.WriteLine("\nGrade: D");
            }
            else if (average < 80)
            {
                Console.WriteLine("\nGrade: C");
            }
            else if (average < 90)
            {
                Console.WriteLine("\nGrade: B");
            }
            else if (average <= 100)
            {
                Console.WriteLine("\nGrade: A");
            }

        }
    }
    
}
