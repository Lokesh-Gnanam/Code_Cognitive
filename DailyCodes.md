# DailyCodes
## 1.Single File Programming Question
Problem Statement



Viswas wants to spend his weekend watching some short films. He has a list of short films with ratings and prefers to watch the highest-rated films first. To plan his viewing, he wants to see how the selection sort algorithm would organize the films in descending order, step by step.



You are required to implement Selection Sort in descending order and print the array after each step, showing how the list evolves until fully sorted.

Input format :
The first line contains an integer n, representing the number of films.

The second line contains n space separated integers, representing the ratings of the films.

Output format :
After each iteration (step) of the selection sort, print

"After his step : i"

where i is the step number (starting from 1), followed by the current array state.

After sorting is complete, print

"Finally, he got it..."

followed by the sorted array in descending order.



Refer to the sample output for the formatting specifications

Code constraints :
1 ≤ n ≤ 10

0 ≤ rating ≤ 100
## Sample Test Cases


| Input | Output |
| :--- | :--- |
| **5**<br>`3 4 5 1 2` | `After his step : 1`<br>`5 4 3 1 2`<br>`After his step : 2`<br>`5 4 3 1 2`<br>`After his step : 3`<br>`5 4 3 1 2`<br>`After his step : 4`<br>`5 4 3 2 1`<br>**Finally, he got it...**<br>`5 4 3 2 1` |
| **5**<br>`34 54 2 3 1` | `After his step : 1`<br>`54 34 2 3 1`<br>`After his step : 2`<br>`54 34 2 3 1`<br>`After his step : 3`<br>`54 34 3 2 1`<br>`After his step : 4`<br>`54 34 3 2 1`<br>**Finally, he got it...**<br>`54 34 3 2 1` |

---
Solution:
```#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int a[10];

    for(int i = 0; i < n; i++)
        cin >> a[i];

    for(int i = 0; i < n - 1; i++)
    {
        int maxIndex = i;

        // find maximum element in remaining array
        for(int j = i + 1; j < n; j++)
        {
            if(a[j] > a[maxIndex])
            {
                maxIndex = j;
            }
        }

        // swap
        int temp = a[i];
        a[i] = a[maxIndex];
        a[maxIndex] = temp;

        cout << "After his step : " << i + 1 << endl;

        for(int k = 0; k < n; k++)
            cout << a[k] << " ";

        cout << endl;
    }

    cout << "Finally, he got it..." << endl;

    for(int i = 0; i < n; i++)
        cout << a[i] << " ";

    return 0;
} 
```
-------------------------------------------------------------------------------------
