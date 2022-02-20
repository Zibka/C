#include <iostream>
#include <random>





int main()
{
    // Генератор случайных чисел (такой же как rand())
    std::default_random_engine engine;
    engine.seed(42);
    // Распределение
    std::uniform_int_distribution<int> dist(1, 100);

    int n;
    std::cin >> n;
    // выделение памяти под массив размера n
    int *arr = new int[n];

    for(int i = 0; i < n; ++i)
    {
        // заполнение случайными значениями
        arr[i] = dist(engine);
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;

    // Алгоритм поиска значений максимума и минимума
    int min, max;
    max = min = arr[0];
    for(int i = 0; i < n; ++i)
    {
        if(arr[i] > max)
            max = arr[i];
        if(arr[i] < min)
            min = arr[i];
    }
    std::cout << "max = " << max << std::endl;
    std::cout << "min = " << min << std::endl;

    // Алгоритм поиска индексов максимума и минимума
    int max_i, min_i;
    max_i = min_i = 0;
    for(int i = 0; i < n; ++i)
    {
        if(arr[i] > arr[max_i])
            max_i = i;
        if(arr[i] < arr[min_i])
            min_i = i;
    }
    std::cout << "max_i = " << max_i << std::endl;
    std::cout << "min_i = " << min_i << std::endl;

    // Алгоритм реверсирования массива
    int tmp;
    for(int i = 0; i < n / 2; ++i)
    {
        tmp = arr[i];
        arr[i] = arr[n - i - 1];
        arr[n - i - 1] = tmp;
    }
    for(int i = 0; i < n; ++i)
        std::cout << arr[i] << " ";
    std::cout << std::endl;

    // Алгоритм удаления элемента из массива
    int k = max_i; // удалим максимальный элемент
    for(int i = k; i < n - 1; ++i)
        arr[i] = arr[i + 1];
    for(int i = 0; i < n - 1; ++i)
        std::cout << arr[i] << " ";
    std::cout << std::endl;

    // Алгоритм вставки элемента в массив
    k = n / 5;
    for(int i = n - 1; i > k; --i)
        arr[i] = arr[i - 1];
    arr[k] = 333;
    for(int i = 0; i < n; ++i)
        std::cout << arr[i] << " ";
    std::cout << std::endl;

    // Алгоритм сортировки пузырьком (bubble sort)
    for(int j = 0; j < n; ++j)
        for(int i = 0; i < n - 1; ++i)
            if(arr[i] > arr[i + 1])
            {
                tmp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = tmp;
            }
    for(int i = 0; i < n; ++i)
        std::cout << arr[i] << " ";
    std::cout << std::endl;

    delete[] arr;
    return 0;
}
