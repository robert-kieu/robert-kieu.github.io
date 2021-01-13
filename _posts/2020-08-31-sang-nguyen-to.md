---
layout: post
title: Mảng số nguyên tố - Phương pháp Sàng Eratosthenes
date: 2020-08-31 11:30:12
summary: Sàng nguyên tố là phương pháp để liệt kê các số nguyên tố nhỏ hơn một số cho trước.
categories: math
---

Ở bài trước, mình có giới thiệu các bạn cách để kiểm tra xem một số nguyên N có phải là số nguyên tố hay không? Tuy nhiên, nếu thao tác trên mảng sẽ khá chậm, dùng phương pháp sàng Eratosthene như thế nào để tối ưu?
Bạn có thể dùng code cũ để giải bài toán này như sau:

```cpp
#include<iostream>
#include<cmath>

using namespace std;

/*Thuật toán:
+ Số 1 không phải là số nguyên tố.
+ Số 2 là số chẵn duy nhất là số nguyên tố.
+ Số nguyên tố đều là số lẻ => số chia cũng phải là số lẻ. Vì số lẻ không thể chia hết cho số chẵn được.
*/

//Hàm kiểm tra số Nguyên tố.
bool isPrime(int n){
  if(n == 2) return true;
  else if(n == 1 || n % 2 == 0) return false;
  else{
    for(int i = 3; i <= sqrt(n); i+=2){
      if(n % i == 0) return false;
    }
  }
  return true;
}
 
int main(){
    int n = 1000;
    for(int i = 2; i <= n; i++){
        if(isPrime(i) == true){
            cout << i << " ";
        }
        else continue;
    }
    
    return 0;
}
```
Cách trên tuy đơn giản nhưng lại chạy khá chậm. Một cách khác, chạy nhanh hơn khi sử dụng sàng nguyên tố Eratosthene nhưng có một nhược điểm tốn nhiều bộ nhớ.

## Nhận xét:

Nếu một số là số nguyên tố thì bội của nó không phải là số nguyên tố. Vậy chúng ta cần lọc những số là bội của số nguyên tố. Bạn có thể triển khai bằng cách đặt cờ hiệu.
-   Giả sử tất cả đều là số nguyên tố.
-   Tìm bội của các số nguyên tố và đánh dấu nó không phải là số nguyên tố.
-   Xuất kết quả ra màn hình các số được đánh dấu là số nguyên tố.

![Sàng nguyên tố. Nguồn: Wikipedia](https://upload.wikimedia.org/wikipedia/commons/b/b8/Animation_Sieb_des_Eratosthenes_%28vi%29.gif)

## Cài đặt:

Ở đây giá trị của mảng là số 0 và 1 dùng để đánh dấu, chúng ta cần lưu ý điều mà chúng ta thực sự quan tâm là chỉ số của mảng tượng trưng cho các số.

```cpp
#include<iostream>

using namespace std;
const int MAX = 1000;

int main(){
    bool arr[MAX + 1]; // Tạo mảng arr có MAX + 1 phần tử, lý do chúng ta sẽ bỏ số 0 và số 1 và lấy tới số MAX.
    
    //Mặc định tất cả phần từ là true <=> Mặc định tất cả đều là số nguyên tố. Lấy phần từ thứ 2
    arr[0] = false;
    arr[1] = false;
    for(int i = 2; i <= MAX; i++){
        arr[i] = true;
    }
    
    //Bắt đầu sàng nguyên tố theo thuật toán.
    for(int i = 2; i <= MAX; i++){
        if(arr[i] == true){ // Nếu như một số là số nguyên tố
            for(int j = i * 2; j <= MAX; j+=i ){ //Bội của nó sẽ không phải là số nguyên tố.
                arr[j] = false;
            }
        }
        else continue;
    }
    
    //Xuất kết quả
    for(int i = 0; i <= MAX; i++){
        if(arr[i] == true){
            cout << i << " ";
        }
        else continue;
    }
    
    return 0;
}
```
