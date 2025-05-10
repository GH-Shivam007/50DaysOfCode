# C++ Code Explanation with Diagrams

## 🚀 Problem 1: Nth Digit
### 🔍 Problem Statement
Given a number `n`, return the nth digit of the sequence of numbers starting from 1 (1, 2, 3, 4, ..., 11, 12, 13, ...). For example, the 3rd digit is '3' and the 11th digit is '0' (from 10).

### ✅ Approach
1. **Initialize variables**: Start by defining variables to track the length of the digits (`digitInNum`), the starting number (`start`), and the range of numbers in each digit length (`end`).
2. **Locate the range containing the nth digit**: While `n` is larger than the total number of digits in the current range (`digitInNum * end`), subtract that value from `n` and adjust the ranges.
3. **Determine the exact number**: After narrowing down to the right range, calculate the exact number that contains the nth digit.
4. **Extract and return the digit**: Convert the number to a string and return the appropriate digit.

### 🧾 Code
```cpp
class Solution {
public:
    int findNthDigit(int n) {
        long digitInNum = 1, start = 1, end = 9;

        while (n > digitInNum * end) {
            n -= digitInNum * end;
            digitInNum++;
            start *= 10;
            end *= 10;
        }

        long num = start + (n - 1) / digitInNum;
        string numStr = to_string(num);
        return numStr[(n - 1) % digitInNum] - '0';
    }
};

###📈 Time & Space Complexity
Time Complexity: O(log(n)), where n is the input number. The loop iterates to determine the range and number containing the nth digit, with the number of iterations growing logarithmically.

Space Complexity: O(1), since no additional space is used except for a few variables.

🧠 Insight
This approach avoids generating the entire sequence and directly calculates the nth digit using number properties. It efficiently reduces the search space by increasing the digit length in powers of 10.

🔁 Flowchart (Mermaid)
mermaid
Copy
Edit
graph LR
    A[Start] --> B[Initialize variables]
    B --> C{n > digitInNum * end}
    C -->|Yes| D[Update n, digitInNum, start, and end]
    C -->|No| E[Find the number containing nth digit]
    E --> F[Convert number to string]
    F --> G[Return nth digit]
    G --> H[End]
🚀 Problem 2: Swapping Nodes in a Linked List
🔍 Problem Statement
Given the head of a singly linked list, swap the kth node from the beginning and the kth node from the end of the list. Return the modified list.

✅ Approach
Store nodes in an array: Traverse the linked list and store each node in an array.

Identify the nodes to swap: Using the array, identify the kth node from the beginning and end.

Perform the swap: Swap the values of the identified nodes.

Return the modified list: Return the modified linked list.

🧾 Code
cpp
Copy
Edit
class Solution {
public:
    ListNode* swapNodes(ListNode* head, int k) {
        vector<ListNode*> nodes;
        ListNode* current = head;

        while (current) {
            nodes.push_back(current);
            current = current->next;
        }

        int n = nodes.size();
        swap(nodes[k - 1]->val, nodes[n - k]->val);

        return head;
    }
};
📈 Time & Space Complexity
Time Complexity: O(n), where n is the number of nodes in the linked list. We traverse the entire list to store the nodes in an array and perform the swap.

Space Complexity: O(n), due to storing the nodes in a vector.

🧠 Insight
This approach simplifies the swapping process by using extra space to store the nodes, making it easier to access the nodes to be swapped.

🔁 Flowchart (Mermaid)
mermaid
Copy
Edit
graph LR
    A[Start] --> B[Traverse list and store nodes in array]
    B --> C[Identify kth node from start and end]
    C --> D[Swap values of identified nodes]
    D --> E[Return modified linked list]
    E --> F[End]
Copy
Edit







