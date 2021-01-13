---
layout: post
title: Phương pháp sinh - Liệt kê hoán vị
date: 2020-09-23 11:52:10
summary: Đây là bài viết cuối cùng về phương pháp sinh.
categories: phuong-phap-sinh
---

Đã qua hai bài viết về phương pháp sinh, bạn cũng có thể hiểu được cách sử dụng rồi. Hôm nay, mình sẽ giới thiệu với các bạn một bài mới, cấu trúc vẫn như cũ. Tuy nhiên, hơi nặng về thuật toán.

Bạn có thể xem lại bài trước để biết điều kiện để áp dụng phương pháp sinh cũng như hiểu được cách áp dụng nó một cách đơn giản nhất. Ở bài này, mình sẽ đưa ra một bài toán áp dụng phương pháp sinh để giải.

## Đề bài:

Liệt kê các hoán vị của tập {1,2,3,...,N} theo thứ tự từ điển.

Ví dụ: N = 3. Bạn cần liệt kê:

-   123
-   132
-   213
-   231
-   312
-   321

Với bài này, bạn tiếp tục sử dụng mô hình ở các bài trước để giải. Tuy nhiên, bài này khá nặng về thuật toán nhưng khá hay. Gợi ý nhỏ, bạn hãy liệt kê một số hoán vị với N = 6 có thể bạn dễ dàng tự suy ra thuật toán hơn. Bạn không nên chọn N = 3 vì số quá ít bạn khó có thể suy ra thuật toán để giải.

## Phân tích

**Input:** int N

**Output:** Liệt kê các số hoặc chuỗi hoán vị từ tập {1,2,...N}

**Cấu hình đầu tiên:** 1,2,...,N

**Cấu hình cuối cùng:** N,N-1,...,1

**Ý tưởng:** Bài này cần nhiều bước để giải, nên mình không ghi ra đây. Bạn có thể tham khảo trong cuốn Giải thuật và Lập trình -- Lê Minh Hoàng.

## Giải:
```cpp
#include<iostream>
#include<string>

using namespace std;

//Hàm hoán vị vị trí trong chuỗi.
void permutation(char& a, char& b) {
    char temp = a;
    a = b;
    b = temp;
}

int main() {
    cout << "Input N:";
    short n;
    cin >> n;

    string first_number; // Cấu hình đầu tiên
    string last_number; // Cấu hình cuối cùng
    //Sinh cấu hình đầu tiên, cấu hình cuối cùng
    for (int i = 1; i <= n; i++) {
        first_number += char(i + 48);
        last_number += (n - i + 1 + 48);
    }

    cout << first_number << endl;
    while (first_number != last_number) {
        int i = n - 1;// đặt cờ hiệu
        for (i; i >= 0; i--) {
            if (first_number[i] < first_number[i + 1]) {// Tìm vị trí số liền trước dãy giảm dần
                for (int k = n - 1; k > i; k--) { //Tìm số bé nhất ở dãy giảm dần, nhưng phải lớn hơn first_number[i]
                    if (first_number[k] > first_number[i]) {
                        permutation(first_number[i], first_number[k]);
                        int p = n - 1;//Tạo biến đếm từ phải qua trái để sắp xếp dãy giảm dần thành dãy tăng dần
                        for (int j = i + 1; j <= ((n - i) / 2); j++) {// Xét một nửa dãy giảm dần
                            permutation(first_number[j], first_number[p--]);
                        }
                        break;
                    }

                }
                cout << first_number << endl;
                break;
            }

        }
    }

    return 0;
}
```

## Tổng kết:

Đây là bải viết cuối cùng trong series Phương pháp sinh được code bằng ngôn ngữ C/C++. Mong rằng bài viết đơn giản, dễ hiểu và đặc biệt có thể cung cấp những ví dụ để các bạn hiểu rõ hơn về phương pháp này.

## Tham khảo:

*Giải thuật và Lập trình -- Lê Minh Hoàng*