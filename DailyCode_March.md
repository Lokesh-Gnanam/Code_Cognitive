# CODE AND COGNITIVE MARCH 2026

## 1. 
In a classroom with assigned seat numbers ranging from 1 to N, students enter the room and occupy their seats. The seating arrangement is initially in sequential order, but due to a mix-up, one student's seat is left unoccupied. 



Create a program that utilizes binary search to identify and print the seat number that is missing, helping the teacher quickly resolve the seating discrepancy.

Input format :
The first line of input consists of an integer N, representing the total number of seats in the classroom.

The second line consists of N distinct space-separated integers, representing the occupied seat numbers.

Output format :
The output prints a single integer, representing the missing seat number.

If no seat is found missing, print "No missing seat number found in the classroom."



Refer to the sample output for formatting specifications.

Code constraints :
1 ≤ N ≤ 10

| Case | Total Seats ($N$) | Seat Numbers Present | Output |
| :--- | :--- | :--- | :--- |
| **1** | `7` | 1 2 3 4 6 7 8 | `5` |
| **2** | `6` | 2 3 4 5 6 7 | `1` |
| **3** | `3` | 1 2 3 | `No missing seat number found in the classroom.` |

------------------
```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int arr[10];

    for(int i = 0; i < n; i++)
        cin >> arr[i];

    sort(arr, arr + n);

    int left = 0, right = n - 1;
    int missing = -1;

    while(left <= right)
    {
        int mid = (left + right) / 2;

        if(arr[mid] != mid + 1)
        {
            missing = mid + 1;
            right = mid - 1;
        }
        else
        {
            left = mid + 1;
        }
    }

    if(missing == -1)
        cout << "No missing seat number found in the classroom.";
    else
        cout << missing;

    return 0;
}
```

----------------
----------------

## 2.
