# DailyCodes
## 1. Viswas wants to spend his weekend watching some short films. He has a list of short films with ratings and prefers to watch the highest-rated films first. To plan his viewing, he wants to see how the selection sort algorithm would organize the films in descending order, step by step.



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
---------------------------------------------------------------------------------------

## 3.Ashok is learning about doubly linked lists. He wants to write a program to insert a node in the middle of a doubly linked list.

As his friend, you have to guide Ashok in the program.

Input format :
The first line of input consists of an integer n, indicating the number of elements to be added to the doubly linked list.

The second line consists of n integers to be added to the doubly linked list.

The third line consists of an integer m, indicating the integer to be added in the middle of the doubly linked list.

Output format :
The output prints the updated linked list after inserting the element in the middle of the list.



Refer to the sample output for formatting specifications.

Code constraints :
1 ≤ n ≤ 30 (The value of n will be even)

1 ≤ list elements ≤ 105

## Sample Test Cases


| Input | Output |
| :--- | :--- |
| **4**<br>`1 2 3 4`<br>**7** | `1 2 7 3 4` |
| **6**<br>`1 2 3 4 5 6`<br>**9** | `1 2 3 9 4 5 6` |

------

```
#include <iostream>
using namespace std;

struct Node
{
    int data;
    Node* prev;
    Node* next;
};

int main()
{
    int n;
    cin >> n;

    Node* head = NULL;
    Node* temp = NULL;

    for(int i = 0; i < n; i++)
    {
        int x;
        cin >> x;

        Node* newNode = new Node;
        newNode->data = x;
        newNode->prev = NULL;
        newNode->next = NULL;

        if(head == NULL)
        {
            head = newNode;
            temp = head;
        }
        else
        {
            temp->next = newNode;
            newNode->prev = temp;
            temp = newNode;
        }
    }

    int m;
    cin >> m;

    int pos = n / 2;

    Node* current = head;

    for(int i = 1; i < pos; i++)
    {
        current = current->next;
    }

    Node* newNode = new Node;
    newNode->data = m;

    newNode->next = current->next;
    newNode->prev = current;

    current->next->prev = newNode;
    current->next = newNode;

    Node* display = head;

    while(display != NULL)
    {
        cout << display->data << " ";
        display = display->next;
    }

    return 0;
}
```
-------------------------------------------------
--------------------------------------------------------
## 4. Imagine you are working as a librarian in a large library. The library uses an automated system to keep track of book positions on the shelves. Each book is assigned a unique ID, but some IDs are more common than others due to the popularity of certain editions.



The system logs the positions of books in a sorted list based on their IDs. You need to find the first and last positions of a specific book ID in this sorted list using recursive binary search.



Example

Input:

10 

1 2 2 2 2 3 4 8 8 8 

8



Output:

7 9



Explanation:

The first and last positions of book ID 8 are [7, 9] since the index is 0-based.

Input format :
The first line of input consists of an integer n, representing the total number of book IDs.

The second line consists of a sorted list of n integers representing the book IDs.

The third line consists of an integer x, representing the specific book ID to find.

Output format :
The output displays indexes of the first and last occurrence of x, as space-separated integers.

If book ID x is not present in the shelves, print "NO OCCURRENCES".



Refer to the sample output for formatting specifications.

Code constraints :
The given test cases fall under the following specifications:

1 ≤ n ≤ 20

1 ≤ book ID, x ≤ 100
## Sample Test Cases


| Input | Output |
| :--- | :--- |
| **10**<br>`1 2 2 2 2 3 4 8 8 8`<br>**8** | `7 9` |
| **10**<br>`1 2 2 2 2 3 4 8 8 8`<br>**5** | `NO OCCURRENCES` |

----

```
#include <iostream>
using namespace std;

int firstOcc(int arr[], int low, int high, int x)
{
    if(low > high)
        return -1;

    int mid = (low + high) / 2;

    if(arr[mid] == x)
    {
        if(mid == 0 || arr[mid-1] != x)
            return mid;
        else
            return firstOcc(arr, low, mid-1, x);
    }
    else if(arr[mid] > x)
        return firstOcc(arr, low, mid-1, x);
    else
        return firstOcc(arr, mid+1, high, x);
}

int lastOcc(int arr[], int low, int high, int x, int n)
{
    if(low > high)
        return -1;

    int mid = (low + high) / 2;

    if(arr[mid] == x)
    {
        if(mid == n-1 || arr[mid+1] != x)
            return mid;
        else
            return lastOcc(arr, mid+1, high, x, n);
    }
    else if(arr[mid] > x)
        return lastOcc(arr, low, mid-1, x, n);
    else
        return lastOcc(arr, mid+1, high, x, n);
}

int main()
{
    int n;
    cin >> n;

    int arr[20];

    for(int i=0;i<n;i++)
        cin >> arr[i];

    int x;
    cin >> x;

    int first = firstOcc(arr,0,n-1,x);
    int last = lastOcc(arr,0,n-1,x,n);

    if(first == -1)
        cout<<"NO OCCURRENCES";
    else
        cout<<first<<" "<<last;

    return 0;
}
```
--------------------------------------------------------------------------------------
---------------------------------------------------
## 5.Tom is working in a warehouse inventory system, where the item IDs are assigned sequentially in ascending order. 



He wants to develop a program using recursive binary search to efficiently determine the closest item ID that is less than or equal to a given target ID. 



The program takes the total number of items and their sorted IDs as input, assisting warehouse staff in quickly identifying the closest available item less than or equal to the target ID. Help Tom in this program.

Input format :
The first line of input consists of an integer N, representing the number of items in the warehouse.

The second line consists of N space-separated integers, representing the sorted list of item IDs.

The third line consists of an integer representing the target item ID.

Output format :
The output prints "The closest item ID less than or equal to X is Y", where X is the target ID and Y is the closest item ID less than or equal to X.

If no such element exists, print "No closest item with an ID less than or equal to X exists in the warehouse", where X is the target ID.



Refer to the sample output for formatting specifications.

Code constraints :
In this scenario, the test cases fall under the following constraints:

1 ≤ N ≤ 10

1 ≤ item ID ≤ 100

## Sample Test Cases


| Case | Input | Output |
| :--- | :--- | :--- |
| **1** | **7**<br>`17 25 38 47 51 62 79`<br>**50** | The closest item ID less than or equal to 50 is **47** |
| **2** | **6**<br>`41 52 58 61 65 72`<br>**65** | The closest item ID less than or equal to 65 is **65** |
| **3** | **5**<br>`12 15 24 25 35`<br>**10** | No closest item with an ID less than or equal to 10 exists in the warehouse |

----

```
#include <iostream>
using namespace std;

int findClosest(int arr[], int low, int high, int x)
{
    if(low > high)
        return -1;

    int mid = (low + high) / 2;

    if(arr[mid] == x)
        return arr[mid];

    if(arr[mid] > x)
        return findClosest(arr, low, mid - 1, x);

    int temp = findClosest(arr, mid + 1, high, x);

    if(temp <= x && temp != -1)
        return temp;
    else
        return arr[mid];
}

int main()
{
    int n;
    cin >> n;

    int arr[10];

    for(int i = 0; i < n; i++)
        cin >> arr[i];

    int target;
    cin >> target;

    int result = findClosest(arr, 0, n - 1, target);

    if(result == -1)
        cout << "No closest item with an ID less than or equal to " << target << " exists in the warehouse";
    else
        cout << "The closest item ID less than or equal to " << target << " is " << result;

    return 0;
}
```
---------------------------------------
-----------------------------------------
