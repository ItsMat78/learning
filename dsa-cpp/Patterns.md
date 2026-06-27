```cpp title:Patterns
#include <bits/stdc++.h>
using namespace std;

void Pattern1(int n){
    for (int i=0; i<n; i++){
        for (int j=0; j<n; j++){
            cout << "*";
        }
        cout << "\n";
    }
}

void Pattern2(int n){
    for (int i=0; i<n; i++){
        for (int j=0; j<i+1; j++){
            cout << "*";
        }
        cout << "\n";
    }
}

void Pattern3(int n){
    for (int i=0; i<n; i++){
        for (int j=1; j<i+2; j++){
            cout << j;
        }
        cout << "\n";
    }
}

void Pattern4(int n){
    for (int i=1; i<=n; i++){
        for (int j=0; j<i; j++){
            cout << i;
        }
        cout << "\n";
    }
}

void Pattern5(int n){
    for (int i=0; i<n; i++){
        for (int j=n; j>i; j--){
            cout << "*";
        }
        cout << "\n";
    }
}

void Pattern6(int n){
    for (int i=0; i<n; i++){
        for (int j=n; j>i; j--){
            cout << n-j+1;
        }
        cout << "\n";
    }
}

void Pattern7(int n){
    for (int i=1; i<=n; i++){
        for (int j=1; j<=n-i; j++){
            cout << " ";
        }
        for (int j=0; j<2*i-1; j++){
            cout << "*";
        }
        for (int j=1; j<=n-i; j++){
            cout << " ";
        }
        cout << "\n";
    }
}

void Pattern8(int n){
    for (int i=1; i<=n; i++){
        for (int j=n; j>n-i+1; j--){
            cout << " ";
        }
        for (int j=2*(n-i)+1; j>0; j--){
            cout << "*";
        }
        for (int j=n; j>n-i+1; j--){
            cout << " ";
        }
        cout << "\n";
    }
}

void Pattern9(int n){
    for (int i=1; i<=n; i++){
        for (int j=1; j<=n-i; j++){
            cout << " ";
        }
        for (int j=0; j<2*i-1; j++){
            cout << "*";
        }
        for (int j=1; j<=n-i; j++){
            cout << " ";
        }
        cout << "\n";
    }
    for (int i=1; i<=n; i++){
        for (int j=n; j>n-i+1; j--){
            cout << " ";
        }
        for (int j=2*(n-i)+1; j>0; j--){
            cout << "*";
        }
        for (int j=n; j>n-i+1; j--){
            cout << " ";
        }
        cout << "\n";
    }
}

void Pattern10(int n){
    for (int i=1; i<=n; i++){
        for (int j=1; j<=i; j++){
            cout << "*";
        }
        cout << "\n";
    }
    for (int i=1; i<=n-1; i++){
        for (int j=n-i-1; j>=0; j--){
            cout << "*";
        }
        cout << "\n";
    }
}

void Pattern11(int n){
    bool bin = false;
    for (int i=1; i<=n; i++){
        if (i%2==1) bin = true;
        else bin = false;
        for (int j=1; j<i+1; j++){
            cout << bin << " ";
            bin = !bin;
        }
        cout << "\n";
    }
}

void Pattern12(int n){
    for (int i=1; i<=n; i++){
        for (int j=1; j<=i; j++){
            cout << j;
        }
        for (int j=2*(n-i); j>0; j--){
            cout << " ";
        }
        for (int j=i; j>0; j--){
            cout << j;
        }
        cout << "\n";
    }
}

void Pattern13(int n){
    int bin = 1;
    for (int i=1; i<=n; i++){
        for (int j=1; j<i+1; j++){
            cout << bin << " ";
            bin++;
        }
        cout << "\n";
    }
}

void Pattern14(int n){
    
     for (int i=1; i<=n; i++){
        char al = 'A';
        for (int j=1; j<=i; j++){
            cout << al;
            al = al + 1;
        }
        cout << "\n";
    }
}

void Pattern17(int n){
    for (int i=1; i<=n; i++){
        char al = 'A';
        for (int j=1; j<=n-i; j++){
            cout << " ";
        }
        for (int j=0; j<i; j++){
            cout << al;
            al = al+1;
        }
        al = al - 1;
        for (int j=0; j<i-1; j++){
            al = al - 1;
            cout << al;
        }
        for (int j=1; j<=n-i; j++){
            cout << " ";
        }
        cout << "\n";
    }
}

void Pattern18(int n){
    
    for (int i=1; i<=n; i++){
        char al = 'A';
        al = al + n - i;
        for (int j=1; j<=i; j++){
            cout << al;
            al = al + 1;
        }
        cout << "\n";
    }
}

void Pattern19(int n){
    for (int i=1; i<=n; i++){
        for (int j=1; j<=n-i+1; j++){
            cout << "*";
        }
        for (int j=0; j<2*(i-1); j++){
            cout << " ";
        }
        for (int j=n-i; j>=0; j--){
            cout << "*";
        }
        cout << "\n";
    }
    for (int i=1; i<=n; i++){
        for (int j=1; j<=i; j++){
            cout << "*";
        }
        for (int j=2*(n-i); j>0; j--){
            cout << " ";
        }
        for (int j=i; j>0; j--){
            cout << "*";
        }
        cout << "\n";
    }
}

void Pattern21(int n){
    for (int i=1; i<=n; i++){
        if(i == 1 || i == n){
            for (int j=1; j<=n; j++){
                cout << "*";
            }
        }
        else {
            cout << "*";
            for (int j=1; j<=n-2; j++){
                cout << " ";
            }
            cout << "*";
        }
        cout << "\n";
    }
}

void Pattern22(int n){
    for (int i=1; i <= n; i++){
        int k = n;
        for (int j = 1; j<=n; j++){
            cout << k << " ";
            if (j<i) k--;
        }
        for (int j = 1; j<=n-1; j++){
            if (j>n-i) k++;
            cout << k << " ";
        }
        cout << "\n";
    }
    for (int i=n-1; i >= 1; i--){
        int k = n;
        for (int j = 1; j<=n; j++){
            cout << k << " ";
            if (j<i) k--;
        }
        for (int j = 1; j<=n-1; j++){
            if (j>n-i) k++;
            cout << k << " ";
        }
        cout << "\n";
    }
}
```