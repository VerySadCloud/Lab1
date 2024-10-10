## Отчет по лабораторной работе № 1

#### № группы: `ПМ-2402`

#### Выполнил: `Протасова Екатерина Сергеевна`

#### Вариант: `19`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Входные и выходные данные](#2-входные-и-выходные-данные)
- [Выбор структуры данных](#3-выбор-структуры-данных)
- [Алгоритм](#4-алгоритм)
- [Программа](#5-программа)
- [Анализ правильности решения](#6-анализ-правильности-решения)

### 1. Постановка задачи

> На числовой прямой расположены 4 различные точки A, B, C, D (где A <
B < C < D), которые разбивают числовую прямую на 5 участков (1, 2, 3,
4, 5 слева направо). В какой из участков попадает точка X? Известно, что
X не равна ни одной из точек A, B, C, D. На вход программы подаются
целые числа X, A, B, C, D.

Данную задачу можно разделить на 3 подзадачи: проверка совпадения точки X с одной из границ, 
проверка корректности введенных границ участков и определение участка, в который попадает X

- Для 3 подзадачи нужно рассмотреть 5 случаев:
    1. `X < A`
    2. `A < X < B`
    3. `B < X < C`
    4. `C < X < D`
    5. `D < X`

### 2. Входные и выходные данные

#### Данные на вход

На вход программа должна получать 5 чисел, при этом, как указано в условии,
они все должны быть целыми. Введенные числа ограничены лишь выбранным в пункте 3 типом данных.

|               | Тип         | min значение    | max значение     |
|---------------|-------------|-----------------|------------------|
| A (Число 1)   | Целое число | -2<sup>31</sup> | 2<sup>31</sup>-1 |
| B (Число 2)   | Целое число | -2<sup>31</sup> | 2<sup>31</sup>-1 |
| C (Число 3)   | Целое число | -2<sup>31</sup> | 2<sup>31</sup>-1 |
| D (Число 4)   | Целое число | -2<sup>31</sup> | 2<sup>31</sup>-1 |
| X (Число 5)   | Целое число | -2<sup>31</sup> | 2<sup>31</sup>-1 |

#### Данные на выход

В качестве выходных данных в программе выступает строка типа String с указанным в ней
одним из пяти участков, которые определены в условии (пронумерованы слева направо от 1 до 5)

### 3. Выбор структуры данных

Программа получает 5 целых чисел. Поэтому для их хранения
можно выделить 5 переменных (`a`, `b`, `c`, `d` и `x`) типа `int`.

|             | название переменной | Тип (в Java) | 
|-------------|---------------------|--------------|
| A (Число 1) | `a`                 | `int`        |
| B (Число 2) | `b`                 | `int`        |
| C (Число 3) | `c`                 | `int`        |
| D (Число 4) | `d`                 | `int`        |
| X (Число 5) | `x`                 | `int`        | 

Для вывода результата необязательно его хранить в отдельной переменной.

### 4. Алгоритм

#### Алгоритм выполнения программы:

1. **Ввод данных:**  
   Программа считывает пять целых чисел, обозначенных как `a`, `b`, `c`, `d` и `x`.

2. **Проверка совпадения точки X с одной из границ:**  
   Программа сравнивает значения `x` и `a`, `b`, `c`, `d`. Если `x` равен одному из этих чисел, программа уведомит о нарушении 
   условий задания и предложит попробовать снова. В противном случае программа перейдет к следующему шагу.

3. **Проверка корректности введенных границ участков:**
    Программа сравнит выполнение условий задачи:
    - a < b
    - b < c
    - c < d
   
    В случае, если все три условия выполнены, программа перейдет к следующему шагу. В противном случае
    она уведомит о нарушении условий задания и предложит попробовать снова.

4. **Определение участка, в который попадает X:**  
   Программа сравнивает `x` поочередно с каждой границей:
   - Если `x` < `a`, то на экран выводится строка о том, что X принадлежит 1 участку, в противном случае программа переходит к следующему шагу
   - Если `x` < `b`, то на экран выводится строка о том, что X принадлежит 2 участку, в противном случае программа переходит к следующему шагу
   - Если `x` < `c`, то на экран выводится строка о том, что X принадлежит 3 участку, в противном случае программа переходит к следующему шагу
   - Если `x` < `d`, то на экран выводится строка о том, что X принадлежит 4 участку, в противном случае на экран выводится строка о том, что X принадлежит 5 участку
   
#### Блок-схема

```mermaid
graph TD
    A([Начало]) --> B[/Ввести: a, b, c, d, x/]
    B --> C{x == a or x == b or x == c or x == d}
    C -- Нет --> E{a < b and b < c and c < d}
    E -- Нет --> F[/Вывод: Некорректно введены границы участков, попробуйте снова/]
    F --> Z
    E -- Да --> G{x < a}
    G -- Да --> H[/Вывод: X находится в участке 1/]
    H --> Z
    G -- Нет --> I{x < b}
    I -- Да --> J[/Вывод: X находится в участке 2/]
    J --> Z
    I -- Нет --> K{x < c}
    K -- Да --> L[/Вывод: X находится в участке 3/]
    L --> Z
    K -- Нет --> M{x < d}
    M -- Да --> N[/Вывод: X находится в участке 4/]
    N --> Z
    M -- Нет --> O[/Вывод: X находится в участке 5/]
    C -- Да --> D[/Вывод: X не может быть равна краям участков, попробуйте снова/]
    D --> Z([Конец])
  ```

### 5. Программа

```java
import java.io.PrintStream;
import java.util.Scanner;

public class Main {
    // Объявляем объект класса Scanner для ввода данных
    public static Scanner in = new Scanner(System.in);
    // Объявляем объект класса PrintStream для вывода данных
    public static PrintStream out = System.out;

    public static void main(String[] args) {
        // Считывание пяти целых чисел a, b, c, d и x из консоли
        int a = in.nextInt();
        int b = in.nextInt();
        int c = in.nextInt();
        int d = in.nextInt();
        int x = in.nextInt();

        // Проверка условиям задачи: X не равна ни одной из точек A, B, C, D
        if ((x == a) || (x == b) || (x == c) || (x == d)) {
            out.println("X не может быть равна краям участков, попробуйте снова");

            // Определение участка, в который попадает X
            // Проверка корректности введенных границ участков
        } else if ((a<b) && (b<c) && (c<d)) {
            // Если X меньше первой границы (a), выводим сообщение о том, что X в первом участке,
            // иначе переходим к проверке следующей границы
            if (x < a) {
                out.println("X находится в участке 1");
                // Если X меньше второй границы (b), выводим сообщение о том, что X во втором участке,
                // иначе переходим к проверке следующей границы
            } else if (x < b) {
                out.println("X находится в участке 2");
                // Если X меньше третьей границы (c), выводим сообщение о том, что X в третьем участке,
                // иначе переходим к проверке следующей границы
            } else if (x < c) {
                out.println("X находится в участке 3");
                // Если X меньше четвертой границы (d), выводим сообщение о том, что X в четвертом участке,
                // иначе выводим сообщение о том, что X в пятом участке
            } else if (x < d) {
                out.println("X находится в участке 4");
            } else {
                out.println("X находится в участке 5");
            }
        } else {
            out.println("Некорректно введены границы участков, попробуйте снова");
        }
    }
}
```

### 6. Анализ правильности решения

Программа работает корректно на всем множестве решений с учетом ограничений.

1. Тест на `X = A` или `X = B` или `X = C` или `X = D`:

    - **Input**:
        ```
        1 3 5 7 1
        ```

    - **Output**:
        ```
        X не может быть равна краям участков, попробуйте снова
        ```

2. Тест на границы `A < B` и `B < C` и `C < D`:

    - **Input**:
        ```
        3 1 5 7 4
        ```

    - **Output**:
        ```
        Некорректно введены границы участков, попробуйте снова
        ```

3. Тест на `A < 0` и `B < 0` и `C < 0`и `D < 0` и `X < A`:

    - **Input**:
        ```
        -7 -5 -3 -1 -8
        ```

    - **Output**:
        ```
        X находится в участке 1
        ```

4. Тест на `A < 0` и `B < 0` и `C < 0`и `D < 0` и `X > D`:

    - **Input**:
        ```
        -7 -5 -3 -1 4
        ```

    - **Output**:
        ```
        X находится в участке 5
        ```

5. Тест на `A < 0` и `B < 0` и `C > 0`и `D > 0` и `B < X < C`:

    - **Input**:
        ```
        -7 -5 1 3 0
        ```

    - **Output**:
        ```
        X находится в участке 3
        ```
6. Тест на `A > 0` и `B > 0` и `C > 0`и `D > 0` и `A < X < B`:

   - **Input**:
       ```
       1 3 5 7 2
       ```

   - **Output**:
       ```
       X находится в участке 2
       ```
7. Тест на `A > 0` и `B > 0` и `C > 0`и `D > 0` и `C < X < D`:

   - **Input**:
       ```
       1 3 5 7 6
       ```

   - **Output**:
       ```
       X находится в участке 4
       ```