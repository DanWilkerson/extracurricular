# [Stacks: Balanced Brackets (hackerrank.com)](https://www.hackerrank.com/challenges/ctci-balanced-brackets/problem) 

## Challenge Text

A bracket is considered to be any one of the following characters: (, ), {, }, [, or ].

Two brackets are considered to be a matched pair if the an opening bracket (i.e., (, [, or {) occurs to the left of a closing bracket (i.e., ), ], or }) of the exact same type. There are three types of matched pairs of brackets: [], {}, and ().

A matching pair of brackets is not balanced if the set of brackets it encloses are not matched. For example, {[(])} is not balanced because the contents in between { and } are not balanced. The pair of square brackets encloses a single, unbalanced opening bracket, (, and the pair of parentheses encloses a single, unbalanced closing square bracket, ].

Some examples of balanced brackets are []{}(), [({})]{}() and ({(){}[]})[].

By this logic, we say a sequence of brackets is considered to be balanced if the following conditions are met:

It contains no unmatched brackets.
The subset of brackets enclosed within the confines of a matched pair of brackets is also a matched pair of brackets.
Given  strings of brackets, determine whether each sequence of brackets is balanced. If a string is balanced, print YES on a new line; otherwise, print NO on a new line.

## Solution

```cpp
#include <map>
#include <set>
#include <list>
#include <cmath>
#include <ctime>
#include <deque>
#include <queue>
#include <stack>
#include <string>
#include <bitset>
#include <cstdio>
#include <limits>
#include <climits>
#include <cstring>
#include <cstdlib>
#include <fstream>
#include <numeric>
#include <sstream>
#include <iostream>
#include <algorithm>
#include <unordered_map>
#include <vector>

using namespace std;

bool is_balanced(string expression) {
    
    int braces = 0;
    int parens = 0;
    int brackets = 0;
    int len = expression.length();
    int i;
    vector<int> open_list(floor(len / 2));
    char c;
    int cVal;
    int counter = 0;
    
    if (len % 2 != 0) return false;
    
    for (i = 0; i < len; i++) 
    {
        
        c = expression[i];
        cVal = int(c);

        if (c == 123 || c == 91 || c == 40) {
            counter++;
            if (c == 40) cVal = 39;
            open_list.push_back(cVal);
        } else {

            if (open_list.back() + 2 != cVal) {
                 return false;
            }
            open_list.pop_back();
            counter--;
            
        }        
            
    }
    return counter == 0;
    
}

int main(){
    
    int t;
    cin >> t;
    for(int a0 = 0; a0 < t; a0++){
        string expression;
        cin >> expression;
        bool answer = is_balanced(expression);
        if(answer)
            cout << "YES\n";
        else cout << "NO\n";
    }

    return 0;
}
```

