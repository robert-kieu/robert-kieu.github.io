---
layout: post
title: Cân bằng cây AVL (Code)
date: 2020-12-09 12:20:43
summary: Cân bằng cây là việc rất cần thiết để tối ưu việc tìm kiếm và thêm xoá dễ dàng hơn. Để cân bằng cây thì cây AVL là cây dễ dàng cân bằng nhất.
categories: can-bang-cay

---

Cân bằng cây là việc rất cần thiết để tối ưu việc tìm kiếm và thêm xoá dễ dàng hơn. Để cân bằng cây thì cây AVL là cây dễ dàng cân bằng nhất, các bạn có thể đọc thêm phần [lý thuyết ](https://levandong.com/thuat-toan-can-bang-cay-avl/)để hiểu rõ hơn về [cách cân bằng cây AVL](https://levandong.com/thuat-toan-can-bang-cay-avl/) trước khi bắt đầu code.

# Cấu trúc của một node cây AVL

Một node cần lưu trữ bốn thuộc tính bao gồm:

-   key: Để lưu giá trị của Node.
-   p_left: lưu con trỏ trỏ tới bên trái.
-   p_right: lưu con trỏ trỏ tới bên phải.
-   height: lưu chiều cao của node.

```cpp
struct NODE
{
	int key;
	NODE* p_left;
	NODE* p_right;
	int height;
};
```

# Quy ước

Chúng ta nên quy ước một số việc:

-   Tất cả các node lá hoặc node mới chưa thêm vào trong cây có height = 1.
-   Một node bất kì có chiều cao (height) là max(pLeft, pRight) + 1 tức là chiều cao lớn nhất của node bên trái hoặc bên phải và cộng thêm một đơn vị.
-   Một vị trí được cho là mất cân bằng khi height node bên phải và node bên trái chênh lệch nhau từ hai đơn vị trở lên.
-   Khi kiểm tra cây có cân bằng hay không, quy ước: -1 là cây lệch trái, 0 là cây cân bằng, 1 là cây lệch bên phải của node đó.
-   Mỗi khi thêm hoặc xoá phần tử ta cần cập nhật lại chiều cao của cây.
-   Để có thể dễ dàng duyệt, trong phần code mình sẽ sử dụng phép duyệt LRN để duyệt từ cuối cây duyệt lên.

# Chia nhỏ vấn đề

Trước khi bắt tay vào làm, chúng ta nên thực hiện bước chia để trị, tức là chia nhỏ vấn đề ra thành các vấn đề con rồi từ từ giải quyết các vấn đề đó trước rồi đến vấn đề cha. Hãy suy nghĩ thật đơn giản, hãy tạo version 1 rồi sau đó tối ưu lại thành version 2, đừng cố làm hoàn hảo ngay lúc đầu, mình học được điều này từ thầy mình và mình thấy việc code nhẹ nhàng hơn rất nhiều.

![](https://res-2.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/image.png)

Các bước thực hiện cân bằng cây AVL

Thường thì lúc viết, mình sẽ suy luận từ trên xuống dưới để tạo ra các hàm, mục đích là để chia nhỏ vấn đề. Nhưng lúc mình code mình sẽ code từ dưới code lên. Tức là mình sẽ viết hàm findMax sau đó viết các hàm xoay cho tới hàm kiểm tra node và cuối cùng là hàm cân bằng cây. Khi viết từng hàm, mình sẽ suy nghĩ hết tất cả các trường hợp có thể xảy ra và viết như một đứa trẻ, tức là mình không ngồi đánh giá xem liệu dòng code đó có dư thừa hay không? Có hay không thì mặc kệ, việc đó để cho version 2 làm.

## Lưu ý:

Trong các hàm này, lúc bạn xoay cây sẽ không có vấn đề, nhưng lúc bạn cập nhật height cho node sẽ xảy ra trường hợp node chỉ có một con trái hoặc phải, dẫn tới node còn lại là null, và bạn cần phải xử lý trường hợp đó trước.

# Code của hàm findMaxHeight:
```cpp
int findHeightMax(NODE* pRoot) {    
	if (pRoot->pLeft == nullptr && pRoot->pRight != nullptr) 
		return pRoot->pRight->height;    
	else if (pRoot->pLeft != nullptr && pRoot->pRight == nullptr) 
    		return pRoot->pLeft->height;    
    	else if (pRoot->pLeft == nullptr && pRoot->pRight == nullptr) 
		return 0;    
	return pRoot->pLeft->height > pRoot->pRight->height ? pRoot->pLeft->height : pRoot->pRight->height;
}
```

Code trên sẽ kiểm tra hai node con xem thằng nào lớn hơn thì trả về thằng lớn hơn đó.

# Code hàm rotateLeftLeft:
```cpp
//Xoay trái
void rotateLeftLeft(NODE* &pRoot) {
	NODE* temp = pRoot->p_left; // giu P1
	pRoot->p_left = pRoot->p_left->p_right; // bán con
	temp->p_right = pRoot; // Xoay
	pRoot = temp;// P1 lên làm cha

    //Cập nhật height. Cần xác định là những node lá sẽ không thay đổi height nên ta chỉ cập nhật các node không phải lá

	NODE* pNow = pRoot->p_right;
	pNow->height = findMaxHeight(pNow->p_left, pNow->p_right) + 1;
	pRoot ->height = findMaxHeight(pRoot->p_left, pRoot->p_right) + 1;
 }
```

Vì là hàm xoay cây sẽ thay đổi ngay chính cây truyền vào, nên ở đây mình sẽ dùng tham chiếu. Dùng con trỏ là trỏ vào địa chỉ rồi thì dùng tham chiếu để làm gì? Vì khi bạn dùng con trỏ nó sẽ sinh ra một con trỏ tạm trỏ vào pRoot ở trên, thì code sẽ sai ở dòng "pRoot = temp" pRoot tạm này sẽ được gán bằng temp chứ không được gán vào cây. Bạn cần lưu ý pRoot lúc này là một node con trỏ ở ngoài chứ không phải con trỏ của cây.

Tới đây, chắc các bạn cũng đã hiểu tại sao truyền tham chiếu rồi, ý đồ của mình nằm ở đây. Bạn để ý vòng tròn màu đỏ, bên trái là con trỏ thuộc cây, bên phải là con trỏ ở ngoài cây. Tới lúc này bạn đọc code ở trên dễ hiểu hơn rồi đấy.

![](https://res-4.cloudinary.com/hkmsxmysc/image/upload/q_auto/v1/ghost-blog-images/0-B-Si0bTG1JBDfGOE.png)

Sự khác nhau giữa truyền tham chiếu và con trỏ

# Code hàm rotateLeftRight:
```cpp
void rotateLeftRight(NODE*& pRoot) {
	NODE* pCur = pRoot->p_left; // pCur giữ vị trí P1 để thực hiện quay trái trước, pCur lúc này đóng vai trò là pRoot của cây con nhỏ  pRoot->left
	pRoot->p_left = pCur->p_right;
	pCur->p_right = nullptr;
	pRoot->p_left->p_left = pCur;

	//Cập nhật height cho cây sau khi xoay .
	NODE* pNow = pRoot->p_left;
	NODE* pNow1 = pNow->p_left;
	pNow1->height = findMaxHeight(pNow1->p_left, pNow1->p_right) + 1;
	pNow->height = findMaxHeight(pNow->p_left, pNow->p_right) + 1;


	//Thực hiện xong công việc quay trái, bây giờ thực hiện công việc quay phải
	//Cây hiện tại đã biến thành cây lệch trái bên trái => gọi hàm cũ là xong.

	rotateLeftLeft(pRoot);
}
```
Bạn hiểu được các phần trên thì phần này không cần giải thích gì nữa vì nó nằm ở phần [lý thuyết]().
Tương tự cho hai hàm bên phải vì nó đối xứng nhau.
# Code hàm isBalanceTree:
```cpp
/*Check Tree is Balance*/
int isBalanceTree(NODE* pRoot) {
	int left = 0, right = 0;
	if (pRoot->pLeft == nullptr && pRoot->pRight != nullptr) left = pRoot->pRight->height;// ton tai 1 node con ben trai
	else if (pRoot->pRight == nullptr && pRoot->pLeft != nullptr) right = pRoot->pLeft->height;// ton tai 1 node con ben phai
	else if (pRoot->pLeft != nullptr && pRoot->pRight != nullptr) {// 2 node con deu la nullptr
		left = pRoot->pLeft->height;
		right = pRoot->pRight->height;
	}

	int index = right - left;
	if (index > 1) return 1;
	else if (index < -1) return -1;
	else return 0;
}
```
Đặt tên là isBalanceTree nhưng thật ra nó kiểm tra xem node tại đó có cân bằng hay không thôi. Mà mình thấy là tên không sai, bởi vì node đang xét cân bằng thì cây con ở dưới cũng cân bằng cộng thêm việc mình duyệt cây là duyệt từ dưới lên trên.

# Code hàm BalanceTree:
```cpp
//Balance AVL
/*Bool is check succesfull*/
bool BalanceTree(NODE* &pRoot) {
	if (pRoot == nullptr) {
		return 0;
	}
	BalanceTree(pRoot->p_left);
	BalanceTree(pRoot->p_right);
	if (isBalanceTree(pRoot) == -1) { // lech trai
		NODE* p1 = pRoot->p_left;
		int index = p1->p_right->height - p1->p_left->height;
		if (index <= 0) {
			rotateLeftLeft(pRoot);
		}
		else {
			rotateLeftRight(pRoot);
		}
	}
	else if ( isBalanceTree(pRoot) == 1 ) {  // lech phai
		NODE* p1 = pRoot->p_right;
		int index = p1->p_right->height - p1->p_left->height;
		if (index >= 0) {
			rotateRightRight(pRoot);
		}
		else {
			rotateRightLeft(pRoot);
		}
	}
}
```

Các bước phức tạp chủ yếu các hàm trên, hàm này chỉ đơn giản là kiểm tra xem node bị mất cân bằng ở đâu, và mất cân bằng loại gì? trái trái, trái phải, phải phải hay phải trái rồi gọi hàm xoay thôi.

Nãy giờ, mình chỉ đi cân bằng cây, nhưng cây chỉ bị mất cân bằng khi thêm hoặc xoá. Vậy lúc thêm, xoá một giá trị nào đó trong cây, bạn cần cập nhật lại height của tất cả các node.

```cpp
void Insert(NODE* &pRoot, int x) {
	if (pRoot == nullptr) {
		NODE* temp = createNode(x);
		pRoot = temp;
		return;
	}

	if (x < pRoot->data) {
		Insert(pRoot->pLeft, x);
		pRoot->height = findHeightMax(pRoot) + 1;
	}
	else if (x > pRoot->data) {
		Insert(pRoot->pRight, x);
		pRoot->height = findHeightMax(pRoot) + 1;
	}
}
```
Hàm Insert này mình chỉ lấy bên hàm Insert của cây bình thường chỉ thêm phần cập nhật lại height của node.
# Code hoàn thiện

```cpp
struct NODE {
	int key;
	NODE* p_left;
	NODE* p_right;
	int height;
};

NODE* createNode(int data) {
	NODE* p = new NODE;
	p->key = data;
	p->p_left = nullptr;
	p->p_right = nullptr;
	p->height = 1;
	return p;
}

int findMaxHeight(NODE* pLeft, NODE* pRight) {
	if (pLeft == nullptr) return pRight->height;
	else if (pRight == nullptr) return pLeft->height;
	return pLeft->height > pRight->height ? pLeft->height : pRight->height;
}

/*Check Tree is Balance*/
int isBalanceTree(NODE* pRoot) {
	int left = 0, right = 0;
	if (pRoot->pLeft == nullptr && pRoot->pRight != nullptr) left = pRoot->pRight->height;// ton tai 1 node con ben trai
	else if (pRoot->pRight == nullptr && pRoot->pLeft != nullptr) right = pRoot->pLeft->height;// ton tai 1 node con ben phai
	else if (pRoot->pLeft != nullptr && pRoot->pRight != nullptr) {// 2 node con deu la nullptr
		left = pRoot->pLeft->height;
		right = pRoot->pRight->height;
	}

	int index = right - left;
	if (index > 1) return 1;
	else if (index < -1) return -1;
	else return 0;
}

//Xoay trai
void rotateLeftLeft(NODE* &pRoot) {
	NODE* temp = pRoot->p_left; // giu P1
	pRoot->p_left = pRoot->p_left->p_right; // bán con
	temp->p_right = pRoot; // Xoay
	pRoot = temp;// P1 lên làm cha

	//Cap nhat height. Cần xác định là những node lá sẽ không thay đổi height nên ta chỉ cập nhật các node không phải lá 
	NODE* pNow = pRoot->p_right;
	pNow->height = findMaxHeight(pNow->p_left, pNow->p_right) + 1;
	pRoot->height = findMaxHeight(pRoot->p_left, pRoot->p_right) + 1;
}

void rotateLeftRight(NODE*& pRoot) {
	NODE* pCur = pRoot->p_left; // pCur giữ vị trí P1 để thực hiện quay trái trước, pCur lúc này đóng vai trò là pRoot của cây con nhỏ  pRoot->left
	pRoot->p_left = pCur->p_right;
	pCur->p_right = nullptr;
	pRoot->p_left->p_left = pCur;

	//Cập nhật height cho cây sau khi xoay .
	NODE* pNow = pRoot->p_left;
	NODE* pNow1 = pNow->p_left;
	pNow1->height = findMaxHeight(pNow1->p_left, pNow1->p_right) + 1;
	pNow->height = findMaxHeight(pNow->p_left, pNow->p_right) + 1;


	//Thực hiện xong công việc quay trái, bây giờ thực hiện công việc quay phải
	//Cây hiện tại đã biến thành cây lệch trái bên trái => gọi hàm cũ là xong.

	rotateLeftLeft(pRoot);
}

//Balance AVL
/*Bool is check succesfull*/
bool BalanceTree(NODE* &pRoot) {
	if (pRoot == nullptr) {
		return 0;
	}
	BalanceTree(pRoot->p_left);
	BalanceTree(pRoot->p_right);
	if (isBalanceTree(pRoot) == -1) { // lech trai
		NODE* p1 = pRoot->p_left;
		int index = p1->p_right->height - p1->p_left->height;
		if (index <= 0) {
			rotateLeftLeft(pRoot);
		}
		else {
			rotateLeftRight(pRoot);
		}
	}
	else if ( isBalanceTree(pRoot) == 1 ) {  // lech phai
		NODE* p1 = pRoot->p_right;
		int index = p1->p_right->height - p1->p_left->height;
		if (index >= 0) {
			rotateRightRight(pRoot);
		}
		else {
			rotateRightLeft(pRoot);
		}
	}
}

```
# Tổng kết

Mong là bài viết dễ hiểu. Cây AVL là khởi đầu của các loại cây sau này như cây đỏ đen, cây AA các bạn tìm hiểu kỹ và tự code thử trước khi tham khảo bài viết. Mình sử dụng văn nói để dễ truyền đạt và dễ hiểu nên có thể từ ngữ sẽ không chuẩn 100%.

Bạn có thể sử dụng trang web này để kiểm tra bản thân code đúng hay sai.

[Giả lập cây AVL](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)