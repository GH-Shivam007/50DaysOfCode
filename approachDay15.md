💡 C++ Code Explanation with Diagrams
🚀 Problem: Excel Sheet Column Title
🔍 Problem Statement
Given an integer columnNumber, return its corresponding column title as it appears in an Excel sheet.
(Like 1 → A, 28 → AB, etc.)

✅ Approach
This problem is similar to converting a number into a base-26 numeral system, but with 1-indexing instead of 0-indexing.

Initialize an empty string to build the result.

While columnNumber is greater than 0:

Subtract 1 from columnNumber (to make it 0-indexed).

Get the current character by computing (columnNumber % 26) + 'A'.

Prepend this character to the result string.

Divide columnNumber by 26 for the next iteration.

🧾 Code
cpp
Copy
Edit
class Solution {
public:
    string convertToTitle(int columnNumber) {
        string res = "";

        while (columnNumber > 0) {
            columnNumber--;
            res = char((columnNumber % 26) + 'A') + res;
            columnNumber /= 26;
        }

        return res;        
    }
};
📈 Time & Space Complexity
Time Complexity: O(log₍₂₆₎n)

Space Complexity: O(1) (ignoring the output string)

🧠 Insight
Instead of base-10 or binary, this is base-26 using letters. Adjustment is needed due to 1-indexing (A=1 not 0).

🔁 Flowchart (Mermaid)
mermaid
Copy
Edit
flowchart LR
    Start --> Check[columnNumber > 0]
    Check --> Subtract[Subtract 1 from columnNumber]
    Subtract --> ComputeChar[Compute char = (columnNumber % 26) + 'A']
    ComputeChar --> Prepend[Prepend char to result]
    Prepend --> Divide[columnNumber /= 26]
    Divide --> Check
    Check -- No --> Return[Return result string]
🚀 Problem: Add Two Numbers (Linked List)
🔍 Problem Statement
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order. Add the two numbers and return the result as a linked list.

✅ Approach
Create a dummy node to simplify appending nodes.

Use a carry variable to track overflow from sum > 9.

Loop through both lists until all digits and carry are processed:

Add values from both lists (if they exist) to the total.

Get new digit num = total % 10 and update carry = total / 10.

Create a new node with num and link it to the result list.

Return the list starting from dummy->next.

🧾 Code
cpp
Copy
Edit
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummy = new ListNode();
        ListNode* res = dummy;
        int total = 0, carry = 0;

        while (l1 || l2 || carry) {
            total = carry;

            if (l1) {
                total += l1->val;
                l1 = l1->next;
            }
            if (l2) {
                total += l2->val;
                l2 = l2->next;
            }

            int num = total % 10;
            carry = total / 10;
            dummy->next = new ListNode(num);
            dummy = dummy->next;
        }

        ListNode* result = res->next;
        delete res;
        return result;         
    }
};
📈 Time & Space Complexity
Time Complexity: O(max(m, n)) — where m and n are the lengths of the two lists.

Space Complexity: O(max(m, n)) — one node per digit in the result.

🧠 Insight
Simple simulation of elementary school addition digit by digit using linked list traversal.

🔁 Flowchart (Mermaid)
mermaid

'''
flowchart TD
    Start --> Init[Initialize dummy, res, carry = 0]
    Init --> Loop[While l1 or l2 or carry]
    Loop --> Total[total = carry]
    Total --> L1Check{l1 exists?}
    L1Check -- Yes --> AddL1[total += l1->val; l1 = l1->next]
    AddL1 --> L2Check
    L1Check -- No --> L2Check{l2 exists?}
    L2Check -- Yes --> AddL2[total += l2->val; l2 = l2->next]
    AddL2 --> Calc[Calculate num = total % 10, carry = total / 10]
    L2Check -- No --> Calc
    Calc --> NewNode[Create new node with num and link]
    NewNode --> Loop
    Loop -- No --> Return[Return res->next]
  


    
