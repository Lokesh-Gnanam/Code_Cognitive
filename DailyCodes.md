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
```
#include <iostream>
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




## 2.In modern operating systems, multiple applications run concurrently and are managed efficiently. A Circular Linked List (CLL) is an effective data structure that can be used to organize and iterate over these running applications in a cyclic manner.



Write a program to implement a Circular Linked List that stores the names of currently running applications. The program should accept application names as input and allow iteration over them. If no applications are provided, it should indicate that there are no running applications.

Input format :
The input consists of multiple lines, each containing the name of an application.

The input continues until the user enters "exit", which signals the end of input.



Refer to the sample input for a better understanding.

Output format :
The first line of output prints "Circular Linked List - Running Applications"

If applications were added:

The next line prints "Running Applications:"
Followed by each application name on a new line in the order they were added.
If no applications were added before typing exit:

It directly prints "No applications to iterate."


Refer to the sample output for formatting specifications.

Code constraints :
The given test cases fall under the following constraints:

Each application name is a string with a maximum length of 100 characters.

## Sample Test Cases


| Case | Input | Output |
| :--- | :--- | :--- |
| **1** | `Microsoft Office Suite`<br>`Adobe Creative Cloud`<br>`Google Chrome`<br>`Mozilla Firefox`<br>`VLC Media Player`<br>`Skype`<br>`exit` | **Circular Linked List - Running Applications**<br>Running Applications:<br>`Microsoft Office Suite`<br>`Adobe Creative Cloud`<br>`Google Chrome`<br>`Mozilla Firefox`<br>`VLC Media Player`<br>`Skype` |
| **2** | `exit` | **Circular Linked List - Running Applications**<br>No applications to iterate. |

----

```#include <iostream>
#include <string>
using namespace std;

struct Node
{
    string data;
    Node* next;
};

int main()
{
    Node* head = NULL;
    Node* temp = NULL;

    string app;

    while(true)
    {
        getline(cin, app);

        if(app == "exit")
            break;

        Node* newNode = new Node;
        newNode->data = app;

        if(head == NULL)
        {
            head = newNode;
            newNode->next = head;
            temp = head;
        }
        else
        {
            temp->next = newNode;
            newNode->next = head;
            temp = newNode;
        }
    }

    cout << "Circular Linked List - Running Applications" << endl;

    if(head == NULL)
    {
        cout << "No applications to iterate." << endl;
    }
    else
    {
        cout << "Running Applications:" << endl;

        Node* current = head;

        do
        {
            cout << current->data << endl;
            current = current->next;
        }
        while(current != head);
    }

    return 0;
}
```
---------------------------------------------------------------------------------------

