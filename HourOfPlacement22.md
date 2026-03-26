# HOUR OF PLACEMENT 2026
## MYSQL
## Create a view named 'LongestCity' to find the longest city names, along with their respective lengths (i.e., the number of characters in the name).
Table : Station
<img width="532" height="325" alt="image" src="https://github.com/user-attachments/assets/5d21e38f-2d1b-47a2-ac87-a22a51fa754f" />
NOTE: All records are prepopulated.
Input format :
No console input.

Output format :
The output of the query should include the following headers to be considered:

city, length.

```mysql
CREATE VIEW LongestCity AS
SELECT city, LENGTH(city) AS length
FROM Station
WHERE LENGTH(city) = (
    SELECT MAX(LENGTH(city)) FROM Station
);
```

-----------------------
-----------------------

## C1.Write a program to find the square, square root, cube, and cube root of the given number.

Create a class Demo and include a constructor to initialize the value and write a method display to print square, square root, cube, and cube root of the given number after that the destructor destroys the object.





Input format :
The input consists of a single integer.

Output format :
The output prints that result.

Refer to the sample input and output for formatting specifications.

| Case | Input ($n$) | Constructor Output | Calculations | Destructor Output |
| :--- | :--- | :--- | :--- | :--- |
| **1** | `15` | `Inside Constructor` | **Square:** 225<br>**Square Root:** 3.87298<br>**Cube:** 3375<br>**Cube Root:** 2.46621 | `Inside Destructor` |

```cpp
#include <iostream>
#include <cmath>
#include <iomanip>
using namespace std;

class Demo {
    int num;

public:
    // Constructor
    Demo(int n) {
        num = n;
        cout << "Inside Constructor" << endl;
    }

    // Method to display results
    void display() {
        cout << "square = " << num * num << endl;
        cout << "square root = " << fixed << setprecision(5) << sqrt(num) << endl;
        cout << "cube = " << num * num * num << endl;
        cout << "cube root = " << fixed << setprecision(5) << cbrt(num) << endl;
    }

    // Destructor
    ~Demo() {
        cout << "Inside Destructor" << endl;
    }
};

int main() {
    int n;
    cin >> n;

    Demo obj(n);   // Constructor called
    obj.display();

    return 0;      // Destructor automatically called
}
```
-------------------
-------------------

## C2.Write a program to find the area of the wall. Create a class Wall with the following private attributes

length - double

height - double

Include parameterized constructor Wall(double length, double height) and a method calculateArea() which returns the area of the wall. In the main method get the length and breadth of two walls from the user.

Input format :
The first line of input consists of the length and breadth of wall1 separated by space.

The second line of input consists of the length and breadth of wall2 separated by space.



Output format :
The output prints the areas of wall1 and Wall2.

Refer to the sample input and output for formatting specifications.

| Case | Wall 1 Dimensions ($L \times W$) | Wall 2 Dimensions ($L \times W$) | Output |
| :--- | :--- | :--- | :--- |
| **1** | `10.5` x `8.6` | `8.5` x `6.3` | **Area 1:** 90.3<br>**Area 2:** 53.55 |
| **2** | `13.6` x `12.25` | `90.10` x `12.45` | **Area 1:** 166.6<br>**Area 2:** 1121.74 |

```cpp

#include <iostream>
using namespace std;

class Wall {
private:
    double length;
    double height;

public:
    // Parameterized constructor
    Wall(double l, double h) {
        length = l;
        height = h;
    }

    // Method to calculate area
    double calculateArea() {
        return length * height;
    }
};

int main() {
    double l1, h1, l2, h2;

    cin >> l1 >> h1;
    cin >> l2 >> h2;

    Wall wall1(l1, h1);
    Wall wall2(l2, h2);

    cout << "Area of Wall 1: " << wall1.calculateArea() << endl;
    cout << "Area of Wall 2: " << wall2.calculateArea();

    return 0;
}

```

---------------
---------------

## C3. Write a program to search for an element in a 1D array using pointers.

Input format :
The first line of the input consists of the value of n.

The next n inputs are the array elements separated by a space.

The last input is the element to be searched.

Output format :
The output prints the status of the search.

If the element is found, print its index else print Not found.

Refer sample input and output for formatting specifications.
| Case | Array Size ($n$) | Array Elements | Target | Output |
| :--- | :--- | :--- | :--- | :--- |
| **1** | `5` | 50, 40, 10, 20, 30 | `20` | `20 is found at index 3` |
| **2** | `5` | 50, 40, 30, 10, 20 | `80` | `Not found` |

```cpp

```

-----------------------
---------------------------


