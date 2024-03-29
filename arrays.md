# C++ 陣列 Array

## 介紹陣列

陣列是一種基礎的資料結構，當你有大量的變數需要進行存取的時候就會需要陣列來幫助我們

例如以下程式碼

```cpp=
#include <iostream>

using namespace std;

int main(void)
{
	int a,b,c,d,e,f,g,h,i,j,k,l,m,n;
	
	cout << a << b << c << d << e << f << g << h << i << j << k << l << m << n << "\n";
	
	return 0;
} 
```

假如我們使用陣列

```cpp=
#include <iostream>

using namespace std;

int main(void)
{
	int arr[14];
	
	for(int i=0;i<14;i++)
	{
		cin >> arr[i];
	}
	for(int i=0;i<14;i++)
	{
		cout << arr[i];
	}
	
	cout << "\n";
	
	return 0;
} 
```

看起來是不是變得很方便! 不用設定一大堆變數名稱

首先陣列跟我們宣告變數一樣，一開始都會決定型態跟變數名稱

```cpp=
int arr1[10]; // 宣告 10 個元素的整數陣列

char arr2[10]; // 宣告 10 個元素的字元陣列

string arr3[10]; // 宣告 10 個元素的字串陣列

bool arr4[10]; // 宣告 10 個元素的布林陣列
```

變數名稱後面的中括號 **[]** 為宣告的陣列大小

## 陣列索引值

首先假設我們宣告一個 10 個元素的整數陣列

```cpp=
int arr[10];
```
代表這個陣列共有 10 個變數分別是
**a[0],a[1],a[2],a[3],a[4],a[5],a[6],a[7],a[8],a[9]**

![](https://i.imgur.com/Ph1kSWO.png)

上面這個圖呢，**x[0] = 1,x[1] = 2,x[3] = 4,x[4] = 5**

可以把陣列想像成很多個箱子，編號 $i$ 個箱子裡有著一個值 $k$

值得注意的是，當我們宣告一個大小為 $n$ 的陣列時，箱子編號(索引值)的範圍為 $0$ **~** $n - 1$

## 指定陣列元素的值

我們首先先來參考一個範例程式碼

```cpp=
#include <iostream>

using namespace std;

int main(void)
{
	int a[5] = {1,2,3,4,5};
	
	int b[5] = {1,2,3,4,5};
	
	cout << a[0] << " " << b[0] << "\n";
	
	cout << a[4] << " " << b[4] << "\n";
	
	return 0;
} 
```
輸出結果 : 
![](https://i.imgur.com/aiTqxj2.png)

首先，我們可以注意到我們一開始宣告 $a$ 陣列的大小為 $5$，並且我們在進行宣告的時候就指定一些值在索引值上

```cpp=
int a[5] = {1,2,3,4,5}; // 宣告一個名為 a 的大小為 5 的陣列

// 指定 a[0] = 1
// 指定 a[1] = 2
// 指定 a[2] = 3
// 指定 a[3] = 4
// 指定 a[4] = 5
```
## 陣列的使用

首先，為了讓大家更了解陣列的使用，提供以下範例

### 陣列輸入

```cpp=
cin >> a[30]; // 將陣列索引 30 給使用者輸入
```
### 陣列輸出
```cpp=
cout << a[75]; // 將陣列索引 75 輸出
```
### 賦予值
```cpp=
int save;

save = a[100]; // 將陣列 a 索引 100 的值賦予 save
```
## 陣列溢位

何謂溢位? 簡單來說就是使用陣列時超出你陣列所宣告的大小

```cpp=
int a[50];

a[-1] = 800; // 索引值不能為負數

a[50]; // 陣列索引是 0 ~ 49 所以沒有索引 50

a[105]; // 105 已經大幅超出陣列宣告時的大小了
```

如果有以上狀況出現，程式很可能就會當掉，在 Judge 上可能會出現 Runtime Error

另外補充一下，陣列索引值要是整數型態，以下為錯誤示範

```cpp=
int a[50];

a[3.14] = 2021; // 索引值不能為浮點數型態
```

## 陣列宣告技巧

為了避免溢位的狀況出現，我在寫題目時首先會先注意題目給的輸入範圍

例如
![](https://i.imgur.com/o3iXbo5.png)

此題為 TOJ 55 Number，我們可以看到題目表示 $N \le 10^5$

那麼我就會這樣去做宣告

```cpp=
int a[100005]; // 多保留 5 個大小，避免出錯
```

不過陣列開的大小還是依照個人習慣啦

不過這邊特別提醒的是，陣列也不是想開多大就開多大，大家應該會注意到在寫題目的時候

題目不是只有時間上的限制，也有**記憶體**的限制，開陣列就是使用你的記憶體

當你陣列大到你電腦記憶體受不了的時候，連你自己的電腦也會當掉

當然你傳到 Online Judge 上也是一樣的意思，所以你不是得到

Memory Limit Exceed 超出記憶體限制

![](https://i.imgur.com/pGxCSnY.png)

就是得到 Runtime Error 程式執行時爛掉

![](https://i.imgur.com/ga7CJ7c.png)

## 陣列動態宣告 (陣列變數宣告)

有時候我們會看到有些人宣告陣列時會這樣做

```cpp=
int n;

cin >> n;

int a[n];

for(int i=0;i<n;i++)
{
    cin >> a[i];
}

return 0;
```

我們可以看到，陣列是用變數去進行宣告大小，我們稱這個動作為**陣列動態宣告**或**陣列變數宣告**

這個在語法上雖然是沒問題的，但是這個做法有很多潛在的危險

有時候題目給的 $n$ 如果非常的大，可能程式因記憶體的關係就當掉了

或者你在寫程式的時候不小心在使用索引的時候超出陣列大小，可能就馬上當掉了

或者在 Judge 上得到 Runtime Error，因此我才會建議大家開陣列的時候

依照題目給的範圍進行宣告，且可以多預留一些大小給陣列使用

## 陣列題目示範

為了讓大家一開始能夠有個範例之後能夠舉一反三，先在這邊示範一道題目

![](https://i.imgur.com/Tsqe4w6.png)

此題為 **TCGS OJ b001** 最終倒數

首先我們可以注意到題目一開始會給 $N$ 表示有 $N$ 個數字

所以代表 $N$ 就是我們宣告陣列大小的依據 (我個人習慣題目給的大小 +5 作為依據)

接著我們利用迴圈將陣列 $0$ **~** $N-1$ 的索引填入，之後題目希望你

倒著輸出，也就是從索引 $N-1$ 輸出回 $0$，因此我們利用迴圈控制索引輸出

參考解答 : 
```cpp=
#include <iostream>

using namespace std;

int main(void)
{
	int n,i;
	
	cin >> n;
	
	int a[15]; // 宣告一個大小 15 名稱為 a 的陣列
	
	for(i=0;i<n;i++) // i = 0,1,2,...,n-2,n-1
	{
		cin >> a[i]; // 輸入 a[0] ~ a[n-1]
	}
	
	for(i=n-1;i>=0;i--) // i = n-1,n-2,...,1,0
	{
		cout << a[i] << " "; // 輸出 a[n-1] ~ a[0]
	}
	
	return 0;
}
```

這邊陣列剛開始學很常忘記的地方是
1. 忘記陣列索引值是從 $0$ 開始
2. 宣告一個大小為 $n$ 的陣列，那麼這個陣列可以使用的索引值為 $0$ **~** $n - 1$

這些部份當你練習夠多，用久了就會自然習慣了


## 多維陣列

陣列是可以變成多維型態的

```cpp=
int a[25][25]; // 宣告一個大小為 25 * 25 的二維陣列
int b[35][35][35]; // 宣告一個大小為 35 * 35 * 35 的三維陣列
```
