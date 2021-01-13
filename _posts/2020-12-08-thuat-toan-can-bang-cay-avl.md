---
layout: post
title: Thuật toán cân bằng cây AVL
date: 2020-12-8 10:20:10
summary: Tại sao phải cân bằng cây? Cân bằng cây là gì? Cách cân bằng cây AVL như thế nào?
categories: algorithms
---
Tại sao phải cân bằng cây? Cân bằng cây là gì? Cách cân bằng cây AVL như thế nào? Trong bài viết này mình sẽ trình bày lý thuyết, bài viết sau mình sẽ trình bày code và giải thích.

# Tại sao phải cân bằng cây?

Bạn hãy nhìn vào cây sau đây, bạn thấy cây này giống gì?

![](https://res-1.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-952Qr9QE9Q5y1dBm.png)

Bạn có thấy giống Linked List không? Mà Binary Tree được tạo ra để phục vụ việc tìm kiếm nhanh hơn, thêm, xoá phần tử dễ dàng hơn với O(log2(n)) nhưng khi các bạn thêm các phần tử và không may nó thành Linked List, việc tìm kiếm là O(n). Vậy chúng ta nên cân bằng để cây trở thành Binary Tree và việc tìm kiếm phần tử sẽ dễ dàng hơn.

# Cân bằng cây là gì?

Thay vì cây của bạn biến thành Linked List thì bạn sẽ biến nó thành Binary Tree thực sự, cũng là hình trên nhưng khi bạn thêm sẽ tự động cân bằng lại cây?

![](https://res-3.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-gKoLbOEDABxiZk_X.png)

Theo cây AVL cây được gọi là cân bằng khi chiều cao của cây con bên phải không cao hơn cây con bên trái quá một đơn vị và ngược lại. Tức là chiều cao chỉ được chênh lệch nhau từ tối đa 1 đơn vị.

Ví dụ:

![](https://res-4.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-9qq3Oo38lTiTeZH3.png)

![](https://res-4.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-YYTDdvjOjqHWlbuC.png)

# Cân bằng cây AVL như thế nào?

Bạn cần làm quen với việc xoay cây, để làm quen với việc này, mình sẽ đưa ra các ví dụ từ dễ đến phức tạp. Nói nôm na là các bạn sẽ cầm cây và quay theo một hướng xác định. Đầu tiên, đến với hình dễ nào:

![](https://res-2.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-2eUotfbmvaYqgFuc.png)

Xoay cây từ phải sang trái

Bạn hãy tưởng tượng bạn đang cầm Node A và bạn hất Node A từ phải sang trái, thì theo quán tính Node P sẽ bay xuống làm con Node A, vậy là cây cân bằng. Hình trên là **cây lệch bên phải** nên bạn phải xoay bên trái và tương tự với **cây lệch bên trái** thì các bạn phải xoay sang phải.

Nâng độ khó game lên chút xíu bây giờ các bạn thử xoay cây này xem vẫn áp dụng cách xoay như trên. Hình dưới, cây bị mất cân bằng tại Node 18 vì Node 20 và Node 12 cách nhau 2 đơn vị. Còn tại cây con Node 15 thì cây vẫn cân bằng vì Node 16 và Node 12 chỉ cách nhau 1 đơn vị và cây AVL cho phép điều đó.

![](https://res-3.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-6H7dWfzPcBKBtZAk.png)

Cây lệch trái bên trái

Khác một tý với ví dụ bên trên là bạn chỉ cần cầm Node A và hất sang bên phải là xong. Đối với **cây lệch trái bên trái** bạn cũng hất tương tự nhưng bạn phải thực hiện hành động bán " *con* ". Cụ thể:

-   Khi bạn cầm Node 15 hất sang bên phải thì Node 15 sẽ làm cha và Node 18 sẽ làm Node con bên phải của Node 15, cây con Node 13 vẫn sẽ là cây con bên trái của Node 15.
-   Mình cá là các bạn thấy thắc mắc ở Node 16 sẽ quăng đi đâu? Vì nếu xoay mà không bán con thì thành ra Node 15 có 3 liên kết (không còn là cây binary nữa).
-   Node 16 sẽ bán mình cho Node bên trái của Node 18.

![](https://res-1.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-A4dKY5frCfk9zlPQ.png)

Sau khi xoay cây

Tương tự với **cây lệch phải bên phải**:

![](https://res-5.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-gEz2MOkupC7o16hX.png)

Cây lệch phải bên phải

Chắc tới đây, các bạn sẽ hỏi **cây lệch trái bên trái** là gì? **Cây lệch phải bên phải** là gì? Thực ra do mình hiểu nhưng không biết giải thích thế nào cho dễ hiểu nên mình sẽ lấy ví dụ tường minh để các bạn tự nhận ra. Và đây là **cây lệch trái bên phải**:

![](https://res-4.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-OnqD9xoUYOpXC2ov.png)

Cây lệch trái bên phải

Mình đoán là nhìn hình các bạn cũng hiểu được lệch trái bên trái là gì rồi. Với **cây lệch trái bên phải** thì hơi phức tạp xíu, các bạn nên lấy giấy bút ra để vẽ và đọc kỹ để tránh nhầm lẫn.

Đầu tiên, các bạn cần lấy cây con bên trái xoay bên trái để biến cây trở thành **cây bên trái lệch trái**.

![](https://res-4.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-KBHyD9fgZopsTD68.png)

Biến cây chưa biết về cây đã biết

Tới đây, cân bằng cây quá dễ dàng chỉ cần dùng thuật toán cân bằng **cây bên trái lệch trái** là xong.

![](https://res-3.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-5jGsqtqI2FSTLDgC.png)

Cây AVL sau khi cân bằng

Và tương tự như vậy với cây lệch phải bên phải.

# Tổng kết

Mình đã giới thiệu xong phần lý thuyết về cây AVL và thuật toán để cân bằng cây AVL và mình có một số gợi ý sau đây:

-   Bạn có thể sử dụng [trang này](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html) để xem bạn cân bằng cây có đúng hay không?
-   Bạn nên tập xoay cây nhiều lần và là những cây phức tạp hơn trước khi code. Bạn có thể cho một cây bất kỳ bằng cách: vẽ cây trước, sau đó điền số vào.
-   Bạn có thắc mắc gì về thuật toán đừng ngại để lại comment bên dưới nhé.