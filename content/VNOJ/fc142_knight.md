---
title: "Free Contest 142 - KNIGHT"
date: 2022-12-25T15:31:05+07:00
katex: true
markup: "mmark"
---

## Vấn đề

[https://oj.vnoi.info/problem/fc142_knight](https://oj.vnoi.info/problem/fc142_knight)

## Hướng dẫn

Theo đề bài ta có thể suy ra được từ vị trí có tọa độ `(a; b)` quân mã có thể đi tới các vị trí sau:

-   `(a - 2; b - 1)`
-   `(a - 2; b + 1)`
-   `(a - 1; b - 2)`
-   `(a - 1; b + 2)`
-   `(a + 1; b - 2)`
-   `(a + 1; b + 2)`
-   `(a + 2; b - 1)`
-   `(a + 2; b + 1)`

Tổng quát lên ta được: Với tọa độ `(a; b)` và các giá trị `(i; j)` ($i \ne j$ . $1 \le i, j \le 2$) quân mã có thể đi tới:

-   `(a + i, b + j)`
-   `(a + i, b - j)`
-   `(a - i, b + j)`
-   `(a - i, b - j)`

Và ta chỉ cần kiêm tra xem tọa độ (x; y) của quân tốt có trùng với tọa độ nào trong các trường hợp trên hay không. Nếu có thì in ra $Yes$ và thoát chương trình, ngược lại cho tới khi xét hết các trường hợp mà chưa in ra `Yes` thì in ra $No$.

## Code mẫu

```cpp
#include <bits/stdc++.h>

using namespace std;

int a, b, x, y;

bool check(int m, int n) {
    //  kiểm tra tọa độ (m; n) là một trong các vị trí quân mã có thể đi tới
    //  có trùng với tọa độ (x; y) của quân tốt hay không
    return ((m == x) && (n == y));
}

int main() {
    cin >> a >> b >> x >> y;
    for (int i = 1; i <= 2; ++i) {
        for (int j = (i == 1 ? 2 : 1); j <= (2 - i + 1); ++j) {
            //  vòng lặp (i, j) ở 2 dòng trên đảm bảo i luôn khác j
            if (check(a + i, b + j) || check(a + i, b - j) || check(a - i, b + j) || check(a - i, b - j)) {
                //  nếu tọa độ của quân tốt trùng với 1 trong các tọa độ
                //  quân mã có thể đi tới thì in ra "Yes" và thoát chương trình.
                cout << "Yes";
                return 0;
            }
        }
    }
    //  không có tọa độ nào trùng nên ta in ra "No"
    cout << "No";
    return 0;
}
```
