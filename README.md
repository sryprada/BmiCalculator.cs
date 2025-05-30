# BmiCalculator.cs
using System;

namespace ExceptionHandlingDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Enter your weight in kilograms: ");
            string weightInput = Console.ReadLine();

            Console.Write("Enter your height in meters: ");
            string heightInput = Console.ReadLine();

            CalculateBMI(weightInput, heightInput);
        }

        static void CalculateBMI(string weightStr, string heightStr)
        {
            try
            {
                double weight = Convert.ToDouble(weightStr);
                double height = Convert.ToDouble(heightStr);

                if (height <= 0)
                {
                    throw new DivideByZeroException("Height must be greater than zero.");
                }

                double bmi = weight / (height * height);

                Console.WriteLine($"Your BMI is {bmi:F2}");
            }
            catch (FormatException)
            {
                Console.WriteLine("Error: Please enter numeric values only.");
            }
            catch (DivideByZeroException ex)
            {
                Console.WriteLine($"Error: {ex.Message}");
            }
            catch (OverflowException)
            {
                Console.WriteLine("Error: The number you entered is too large or too small.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.Message}");
            }
        }
    }
}


Correct one

using System;

namespace ExceptionHandlingDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Enter your weight in kilograms: ");
            string weightInput = Console.ReadLine();

            Console.Write("Enter your height in meters: ");
            string heightInput = Console.ReadLine();

            CalculateBMI(weightInput, heightInput);
        }

        static void CalculateBMI(string weightStr, string heightStr)
        {
            try
            {
                int weight = Convert.ToInt32(weightStr);
                int height = Convert.ToInt32(heightStr);

                if (height <= 0)
                {
                    throw new DivideByZeroException("DivideByZeroException: Height must be greater than zero.");
                }

                int bmi = weight / (height * height);

                Console.WriteLine($"Your BMI is {bmi:F2}");
            }
            catch (FormatException ex)
            {
                Console.WriteLine($"Error: {ex.Message}");
                Console.WriteLine("Format Exception Error: Please enter numeric values only.");
            }
            catch (DivideByZeroException ex)
            {
                Console.WriteLine($"Error: {ex.Message}");
            }
            catch (OverflowException)
            {
                Console.WriteLine("OverflowException Error: The number you entered is too large or too small.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.Message}");
            }
        }
    }
}
