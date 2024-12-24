# sistem-laba
class Program
{
    static void Main(string[] args)
    {
        string filePath = @"C:\Users\mitya\OneDrive\Рабочий стол\2 курс\системка\zxy.txt"; // Путь к файлу

        try
        {
            string content; // Переменная для хранения содержимого файла
            using (StreamReader sr = new StreamReader(filePath)) // Чтение файла
            {
                content = sr.ReadToEnd();
            }
            
            int currentCount = 0; // Счетчик текущих 'X'
            int maxCount = 0; // Максимальное количество последовательности 'X'
            
            foreach (char c in content) // Перебор каждого символа в содержимом
            {
                if (c == 'X') // Если символ 'X'
                {
                    currentCount++; // Увеличиваем счетчик
                }
                else
                {
                    if (currentCount > maxCount) // Проверяем, больше ли текущий счетчик максимального
                    {
                        maxCount = currentCount; // Обновляем максимальное значение
                    }
                    currentCount = 0; // Сбрасываем текущий счетчик
                }
            }
            
            if (currentCount > maxCount) // Проверяем в конце строки
            {
                maxCount = currentCount; // Обновляем максимальное значение
            }

            Console.WriteLine($"Самая длинная последовательность 'X' = {maxCount}"); // Вывод результата
        }
        catch (Exception ex) // Обработка исключений
        {
            Console.WriteLine($"Ошибка при чтении файла: {ex.Message}"); // Вывод сообщения об ошибке
        }
    }
}
