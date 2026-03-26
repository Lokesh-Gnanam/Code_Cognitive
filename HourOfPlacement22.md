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

