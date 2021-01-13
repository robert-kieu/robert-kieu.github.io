---
layout: post
title: Phương pháp sinh - Liệt kê các tập con k phần tử từ 1 đến N
date: 2020-09-22 11:20:13
summary: Liệt kê tập con k phần tử từ 1 đến N áp dụng phương pháp sinh.
categories: phuong-phap-sinh

---

Tiếp nối chuỗi bài Phương pháp sinh, mình tiếp tục gửi đến các bạn một bài mới. Mong đây là bài tập rèn luyện cũng như ví dụ minh hoạ rõ ràng hơn cho cách áp dụng Phương pháp sinh để giải bài toán yêu cầu liệt kê.

Bạn có thể xem lại bài trước để biết điều kiện để áp dụng phương pháp sinh cũng như hiểu được cách áp dụng nó một cách đơn giản nhất. Ở bài này, mình sẽ đưa ra một bài toán áp dụng phương pháp sinh để giải.

## Đề bài:

Liệt kê tập con k phần tử của tập {1,2,3,....,n}. Các tập phải chứa các số khác nhau, không tính vị trí.

Ví dụ: Với n = 3 và k=2, ta có tập {1,2,3}

Bạn cần liệt kê: {1,2};{1,3};{2,3}

## Phân tích:

**Input:** int n và int k

**Output:** liệt kê tất cả tập con có k phần tử trong tập từ 1 đến N.

**Cấu hình đầu tiên:** 1,2,....,k

**Cấu hình cuối cùng:** n -- k + 1,n -- k + 2,....,n

**Có thứ tự từ điển không?** Có

**Ý tưởng:** Xét từ phải qua trái, tìm vị trí có chữ số nhỏ hơn chính vị trí đó của cấu hình thì tăng lên một đơn vị và tất cả các chữ số phía sau sẽ bằng chữ số liền kề trước nó cộng thêm một đơn vị.

## Giải:

```cpp
#include<iostream>
#include<string>

using namespace std;

int main(){
    cout << "Input N:";
    short n;
    cin >> n;
    cout << "Input k: ";
    short k;
    cin >> k;
//Cau hinh
    string first_number;
    string last_number;
//Sinh cac cau hinh
    for(int i = 1; i <= k; i++) {
        first_number += (i + 48); // Cong 48 de chuyen tu int sang char trong bang ascii
        last_number += (n - k + i + 48);//Dung toan de ra bieu thuc
    }
    //In ra cau hinh dau tien
    cout << first_number << endl;

    //Thuat toan
    while(first_number != last_number){
        for(int i = k - 1; i >= 0; i--){
            if(first_number[i] < last_number[i]){
                first_number[i] = first_number[i] + 1;
                for(int j = i + 1; j < k; j++){
                    first_number[j] = first_number[j - 1] + 1;
                }
                break;//Sau khi tang 1 don vi thanh cong => ra 1 cau hinh => break
            }
        }
        cout << first_number << endl; // In ra cau hinh thanh cong
    }
    return 0;
}
```

## Tổng kết:

Vậy là hoàn thành cách giải bài toán rồi, áp dụng sơ đồ của bài trước để giải thôi. Các bạn có đóng góp ý kiến hay có thắc mắc gì có thể để lại bình luận bên dưới. Bạn nào code xong hãy paste code của các bạn và chèn link vào dưới bình luận nhé.

##Tham khảo: 
*Giải thuật và lập trình -- Lê Minh Hoàng*