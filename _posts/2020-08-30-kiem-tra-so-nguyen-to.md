---
layout: post
title: Kiểm tra số nguyên tố C++
date: 2020-08-30 12:32:15 +0700
summary: Số nguyên tố được sử dụng khá nhiều trong Toán học và Tin học bởi sự đặc biệt của nó. Vậy đâu là cách tìm số nguyên tố trong lập trình?
categories: math
---

Số nguyên tố được sử dụng khá nhiều trong Toán học và Tin học bởi sự đặc biệt của nó. Vậy đâu là cách tìm số nguyên tố trong lập trình?

## Định nghĩa

Số nguyên tố là số có đúng hai ước số là 1 và chính nó. Tức là ngoài số 1 và chính nó, nó sẽ không chia hết cho bất kì số nào nữa. Ví dụ số 5 hay số 43 là số nguyên tố, bởi vì:

- 5 chỉ chia hết cho 1 và 5.
- 43 chỉ chia hết cho 1 và 43.

## Kiểm tra số nguyên tố theo định nghĩa

Đây là cách đơn giản và dễ dàng cài đặt nhất. Giả sử bạn cần kiểm tra xem n có phải là số nguyên tố hay không? Bạn chỉ cần kiểm tra xem n có chia hết cho bất kì số nào trong khoảng từ 1 đến n ( khoảng là không lấy hai đầu mút ).

Ví dụ: n = 7, thì bạn cần xét lần lượt, 7/2, 7/3, 7/4, 7/5, 7/6.

Bạn có thấy cách trên xét rất nhiều không? Có cách để xét ít hơn, và tôi đoán đa số mọi người sử dụng. Thay vì bạn xét từ $$ 2 \to n -1  $$ thì bạn chị cần xét từ $$ 2 \to \sqrt{n} $$.

## Chứng minh

Giả sử n không là số nguyên tố thì ta luôn tách ra được:

$$ n = k_{1} . k_{2} $$ và $$ 0 < k_{1} \le k_{2} < n. $$

$$ k_{1}.k_{2} \le n $$
$$ \Rightarrow k_{1}^{2} \le n $$
$$ \Leftrightarrow k_{1} \le \sqrt{n} $$
Vậy bạn có thể hiểu đơn giản là $$ k_{1} $$​ lớn nhất cũng chỉ là $$ \sqrt{n} $$ , mà nếu bạn có $$ k_{1}​ $$ thì chắc chắn là số đó không phải là số nguyên tố. Vậy bạn chỉ cần xét giá trị $$ 2 \to \sqrt{n} $$​.

Vậy để cải tiến, bạn cần có những nhận xét sau:

Số nguyên tố là số lẻ, vì nếu số chẵn thì $$ k_{1} = 2 $$ vậy chắc chắn không phải là số nguyên tố. Vậy bạn có thể sử dụng bước nhảy là 2 để xét.

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
## Tham khảo:
*Tài liệu chuyên Tin học Quyển 1 -- Hồ Sĩ Đàm.*