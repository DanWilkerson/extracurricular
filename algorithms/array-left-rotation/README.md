# [Arrays: Left Rotation (hackerrank.com)](https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem) 

## Challenge Text

A left rotation operation on an array shifts each of the array's elements  unit to the left. For example, if  left rotations are performed on array , then the array would become .

Given an array  of  integers and a number, , perform  left rotations on the array. Then print the updated array as a single line of space-separated integers.

## Solution

```cpp
#include <vector>
#include <iostream>

using namespace std;


int main(){
    int n;
    int k;
    cin >> n >> k;
    vector<int> a(n);
    for(int a_i = 0;a_i < n;a_i++){
        cin >> a[a_i];
    }


    for (int i = k; i < n; i++) {
        
        cout << a[i] << " ";
        
    }
    
    for (int i = 0; i < k; i++) {
        
        cout << a[i] << " ";
        
    }

    cout << endl;
    return 0;
}
```

