internal class Program
{
    const int multipleOfThisNumber = 21, minArrayLength = 1000, minValueInArray = 10000;
    private static void Main(string[] args)
    {
        int[] array = new int[minArrayLength];
        //array filling. 
        Random r = new();
        for (int i = 0; i < array.Length; i++)
            array[i] = r.Next(0, minValueInArray);

        //find value in array 
        int min = 0, MultipleThree = 0, MultipleSeven = 0, MultipleTwentyone = 1, result = 0;
        for (int i = 0; i < array.Length; i++)
            if (array[i] > min) min = array[i];

        foreach (int i in array)
        {
            if (i % multipleOfThisNumber == 0 && i > MultipleTwentyone) MultipleTwentyone = i;

            if (i % 3 == 0) MultipleThree = i;

            if (i % 7 == 0) MultipleSeven = i;

            result = MultipleThree * MultipleSeven;

            if (result == MultipleTwentyone) break;
        }

        //output found element 
        if (result == MultipleTwentyone && min == MultipleTwentyone)
            Console.WriteLine($"{min} - это число соответсвует условиям задачи." +
            $"\nОно кратно 21, а также является произведением двух других различных элементов последовательности." +
            $"\nЭто: {MultipleThree} и {MultipleSeven}");
        if (result != MultipleTwentyone)
            Console.WriteLine(-1);
    }
}
