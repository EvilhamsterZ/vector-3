# vector-3
## code
```
#include <iostream>
#include <vector>
#include <algorithm>
#include <fstream>

void func(std::vector <int>  &m2,int h) 
{    
    const int n=7921;
    std::vector <int> m1;
    std::vector <bool> m(n + 1, 1);
    
    std::cout << "Вывод простых чисел" << std::endl;
    for (int i = 2; i <= n; i++)
    {
        if (m[i] == true)
        {
            m1.push_back(i);

            for (int j = i * i; j <= n; j = j + i)
            {
                m[j] = false;
            }
        }
    }
    //std::cout << "Введите номера простых чисел для вывода" << std::endl;
    //for (int i = 0; i < h; i++)
    //{
    //    std::cin >> m2[i];
    //}
    //std::cout << "Вывод" << std::endl;
    std::ofstream fout("output.txt");
    fout <<"Вывод "<<h<<" простых чисел"<< std::endl;
    fout.close();
    for (int i = 0; i < h; i++)
    {
        std::cout << m1[i] << std::endl;
        std::ofstream fout("output.txt", std::ios_base::app);
        fout << m1[i] << std::endl;
        fout.close();
    }
}

int main()
{   
    setlocale(LC_ALL, "Rus");
    int h;
    std::cout << "Введите число запросов" << std::endl;
    std::cin >> h;
    std::vector <int> m2(h);
    func(m2,h);
    return (0);
}
```
