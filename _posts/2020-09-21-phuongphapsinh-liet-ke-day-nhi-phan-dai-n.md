---
layout: post
title: Phương pháp sinh - Liệt kê dãy nhị phân có độ dài N
date: 2020-09-21 12:25:30
summary: Phương pháp sinh là phương pháp dùng để liệt kê tổ hợp.
categories: phuong-phap-sinh
---

## Điều kiện
Phương pháp sinh được áp dụng để giải các bài toán liệt kê tổ hợp thoả hai điều kiện:
-   Có thể xác định thứ tự của các cấu hình.
-   Có thuật toán từ một cấu hình chưa phải là cấu hình cuối và sinh ra được cấu hình kế tiếp đó.

## Cấu hình là gì?

-- Giả sử bạn có tập O = {1,2,3} và đề bài yêu cầu tìm các chỉnh hợp không lặp chập 3, bạn sẽ liệt kê được:

-   {1,2,3} -- Đây là một cấu hình
-   {1,3,2} -- Đây là một cấu hình
-   {2,1,3} -- Đây là một cấu hình
-   {2,3,1} -- Đây là một cấu hình
-   {3,1,2} -- Đây là một cấu hình
-   {3,2,1} -- Đây là một cấu hình

Vậy theo yêu cầu bài toán, ta có được 6 cấu hình.

## Phương pháp sinh

Trước khi bước vào giải một bài toán bằng phương pháp sinh, bạn cần xác định cấu hình đầu tiên, cấu hình cuối cùng và thuật toán để sinh ra cấu hình tiếp theo từ một cấu hình đã có.\
Bạn có thể hiểu từ sơ đồ sau:

![Phương pháp sinh](https://1.bp.blogspot.com/-WGMcXNM0Mv0/X2hzKkhH8LI/AAAAAAAAAtg/0_K9fEi79dobToJVDY7wvrrZhlUq_gW0wCPcBGAYYCw/s338/phuong_phap_sinh_lvd.png "Phương pháp sinh")

## Bài toán liệt kê dãy nhị phân có độ dài N

### Phân tích:

**Input:** int N

**Output:** Liệt kê các cấu hình cần tìm

**Cấu hình đầu tiên:** 000......0

**Cấu hình cuối cùng:** 111......1

**Ý tưởng:** Tìm vị trí số 0 đầu tiên từ phải sang trái, cho số 0 đó thành số 1 và tất cả các số 1 phía sau sẽ thành số 0.

### Giải:

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
  int n = 25;
  cout << isPrime(n);
  return 0;
}
```

Tham khảo:

*Tài liệu chuyên Tin học Quyển 1 -- Hồ Sĩ Đàm.*