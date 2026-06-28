```cpp title:"Reverse an array"
#include <bits/stdc++.h>
using namespace std;

    
void Recur(int arr[], int i, int j){
    if (i<j){
        swap(arr[i], arr[j]);
        Recur(arr, ++i, --j);
    }
}
    
int main(){
    int arr[5] = {5, 4, 3, 2, 1};
    int i = 0;
    int j = 4;
    Recur(arr, i, j);
    for (int i=0; i<5; i++) cout << arr[i];
}
```
