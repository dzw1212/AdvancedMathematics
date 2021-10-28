## Lecture 01

线性代数的主要目的：求解线性方程组；

n个方程，n个未知数；

对于一个2阶方程组：
$$
2x-y=0\\
-x+2y=3
$$
row picture：求两条直线的交点；

column picture：求两个向量的系数的正确组合；
$$
x
\begin{bmatrix}
2\\-1
\end{bmatrix}
+
y
\begin{bmatrix}
-1\\2
\end{bmatrix}
=
\begin{bmatrix}
0\\3
\end{bmatrix}
$$
matrix equation：
$$
Ax=b
$$
对于任意$b$是否有解？ =  列的线性组合能否覆盖整个三维空间？

若各个列独立，则必定有唯一解；若各个列不独立，则实际给出的方程数小于未知数的数量，则会有无限多个解或无解；

## Lecture 02

对于3阶方程组：
$$
x+2y+z=2\\
3x+8y+z=12\\
4y+z=2
$$
转换为矩阵：
$$
\begin{matrix}
1 & 2 & 1\\
3 & 8 & 1 \\
0 & 4 & 1
\end{matrix}
$$
添加$b$为右列，称为"增广矩阵"：
$$
\begin{matrix}
1 & 2 & 1 & 2 \\
3 & 8 & 1 & 12\\
0 & 4 & 1 & 2
\end{matrix}
$$

---

消元法elimination：

​	主元pivot：消元的过程中，每行不为0的第一个数；

​	消元生效：每行都有一个主元；
$$
\begin{matrix}
1 & 2 & 1\\
3 & 8 & 1 \\
0 & 4 & 1
\end{matrix}
->
\begin{matrix}
3 & 6 & 3\\
3 & 8 & 1 \\
0 & 4 & 1
\end{matrix}
->
\begin{matrix}
1 & 2 & 1\\
0 & 2 & -2 \\
0 & 4 & 1
\end{matrix}
->\begin{matrix}
1 & 2 & 1\\
0 & 2 & -2 \\
0 & 0 & 5
\end{matrix}
$$
​	消元失效：某一行全为0，没有主元（即两行重复）；

​	回代back substitution：
$$
\begin{align}
x+2y+z&=2\\
2y-2z&=6\\
5z&=-10
\end{align}
$$

---

矩阵消元：

先求得消除第2行第1列的元素的矩阵$E_{21}$：
$$
E_{21}
\begin{bmatrix}
1&2&1\\
3&8&1\\
0&4&1
\end{bmatrix}
=
\begin{bmatrix}
1&2&1\\
0&2&-1\\
0&4&1
\end{bmatrix}
$$

$$
E_{21}=
\begin{bmatrix}
1&0&0\\
-3&1&0\\
0&0&1
\end{bmatrix}
$$
再求得消除第3行第2列的元素的矩阵$E_{32}$：
$$
E_{32}
\begin{bmatrix}
1&2&1\\
0&2&-1\\
0&4&1
\end{bmatrix}
=
\begin{bmatrix}
1&2&1\\
0&2&-1\\
0&0&5
\end{bmatrix}
$$

$$
E_{32}=
\begin{bmatrix}
1&0&0\\
0&1&0\\
0&-2&1
\end{bmatrix}
$$

使用结合律将中间矩阵结合起来，
$$
(E_{32}E_{21})A=U
$$

---

置换矩阵$P$：在左边 --- 对矩阵的各行进行重新排列，即行变换；

​						在右边--- 对矩阵的各列进行重新排列，即列变换；
$$
P
\begin{bmatrix}
a&b\\
c&d
\end{bmatrix}
=
\begin{bmatrix}
c&d\\
a&b
\end{bmatrix}
$$

$$
P=
\begin{bmatrix}
0&1\\
1&0
\end{bmatrix}
$$

---

矩阵乘法支持结合律，但不支持交换律；

---

矩阵可逆 inverse：
$$
A^{-1}A=I
$$

## Lecture 03

矩阵相乘：
$$
AB=C
$$
举个例子，$C$中的元素$C_{34}$等于：
$$
C_{34}=\sum_{k=1}^{n}a_{3k}b_{k4}
$$
矩阵的维度：
$$
A_{m \times n}B_{n \times p}=C_{m \times p}
$$
计算方法：

①计算每个元素；

②将$AB$看做用$A$乘以$B$中的每一列向量，得到的结果组合为$C$，$C$的每一列，就是矩阵$A$中各列的、以$B$中元素为系数的线性组合的结果；

即$A$乘以$B$的每一列；

③$A$的每一行乘以$B$；

④$A$的每一列乘以$B$中的对应行，将结果相加；

⑤分块乘法；

---

逆矩阵：
$$
A^{-1}A=AA^{-1}=I
$$
对于方阵，左逆=右逆；

不是所有矩阵都可逆；

如果存在一个非零矩阵$X$，使得$AX=0$，则矩阵$A$不可逆；

​	证明：若$A$可逆，则有
$$
\begin{align}
A^{-1}AX&=A^{-1}0\\
IX&=0\\
X&=0
\end{align}
$$
​	与题设条件相悖，故$A$为不可逆矩阵。

求逆矩阵（高斯-约旦消元法）：
$$
A|I->I|A^{-1}
$$

## Lecture 04

将一个矩阵的行和列调换，称为对矩阵进行转置：
$$
\begin{align}
A&=
\begin{bmatrix}
1&2&0\\
3&-1&4
\end{bmatrix}
\\
A^{T}&=
\begin{bmatrix}
1&3\\
2&-1\\
0&4
\end{bmatrix}
\end{align}
$$
矩阵的转置的逆，等于矩阵的逆的转置（即对于单个矩阵，转置和逆的操作可以颠倒）：
$$
(A^{-1})^T=(A^T)^{-1}
$$
矩阵的积的逆矩阵：
$$
\begin{align}
AB&=C\\
C^{-1}&=B^{-1}A^{-1}
\end{align}
$$

---

从矩阵$A$得到矩阵$U$：
$$
\begin{align}
E_{21}A&=U\\
\begin{bmatrix}
1&0\\
-4&1
\end{bmatrix}
\begin{bmatrix}
2&1\\
8&7
\end{bmatrix}
&=
\begin{bmatrix}
2&1\\
0&3
\end{bmatrix}
\end{align}
$$
此时，想要$A$在等式的左侧：
$$
\begin{align}
A&=LU\\
({E_{21}}^{-1}E_{21})A&={E_{21}}^{-1}U\\
L&={E_{21}}^{-1}
\end{align}
$$
求$E_{21}$的逆矩阵：
$$
\begin{bmatrix}
1&0&|&1&0\\
-4&1&|&0&1
\end{bmatrix}
->
\begin{bmatrix}
1&0&|&1&0\\
0&1&|&4&1
\end{bmatrix}
\\
{E_{21}}^{-1}=
\begin{bmatrix}
1&0\\
4&1
\end{bmatrix}
$$

## Lecture 05

置换矩阵：行重新排列的单位矩阵；

​	对于$n$阶的矩阵，其置换矩阵的个数有$n!$个；

​	所有的置换矩阵都可逆，且其逆矩阵=转置矩阵：
$$
P^{-1}=P^T
$$

---

对称矩阵：矩阵进行转置后没有变化；

​	特点：元素关于多角线对称；

​	所有的矩阵的转置与自身的乘积都为对称矩阵；
$$
(R^TR)^T=R^TR
$$

---

向量空间

​	$R^2$覆盖一个plane；

​	$R^3$覆盖一个space；

​	$R^n$覆盖一个$n$维空间；

​	向量空间必穿过原点；

​	子空间(subspace)：属于母空间，而又具有向量空间的特性；

​		$R^2$的子空间：①$R^2$自身；

​								 ②经过原点，两端无限延伸的直线；

​								 ③零点（zero vector）;

​		$R^3$的子空间：①$R^3$自身；

​								 ②经过原点，两侧无限延伸的平面；

​								 ③经过原点，两端无限延伸的直线；

​								 ④零点（zero vector）;

​		一个矩阵的各个列向量的线性组合必然构成一个子空间，称为列空间；

​		假设有子空间$S$和子空间$T$，其两者的交集$S \cap T$同样为子空间；

​	向量加法：
$$
(x_1,x_2)+(y_1,y_2)=(x_1+y_1，x_2+y_2)
$$
​	向量数乘：
$$
k(x_1,x_2)=(kx_1,kx_2)
$$
​	向量点积：
$$
(x_1,x_2) \cdot (y_1,y_2)=x_1y_1+x_2y_2
$$

## Lecture 06

从列空间的角度看$Ax=b$：

​	是否有解？

​		如果矩阵$A$的列空间能够覆盖整个空间，则对于任意$b$方程均有解；

​		否则，对于一部分的$b$方程无解；

​	怎样的$b$才能有解？

​		$b=0$，此时只要$x=0$即可；

​		当且仅当$b$属于矩阵$A$的列空间时，才有解；

​	矩阵$A$的$n$列能否充满整个$n$维空间？

​		如果$n$列相互独立，即每一列不能由其他列通过线性组合得到，则能充满$n$维空间；

​		相互独立的列称为“主列”；

​			主列的选取规则为：靠前优先；

零空间：指使$Ax=0$成立的所以$x$组成的子空间；

​	如果$Av=0$且$Aw=0$，则$A(cv+dw)=0$；

## Lecture 07

矩阵的秩（rank）：矩阵经过消元后，得到的主元的数量；

​	主元所在列称为主列，其他列称为自由列；

​	对应的，回代后，有主变量和自由变量，自由变量可以取任意值，主变量随之变化；

​	对于一个$m \times n$的矩阵，若其秩为$r$，则其有$n-r$个自由变量；

简化行阶梯矩阵$R$($rref$)

​	在简化行阶梯矩阵中，主元为1，主元的上下均为0；

​	经过消元法得到主元后，进一步使主元的上下元素均为0，得到$R$；

---

举例：要求$Ax=0$的解
$$
A = 
\begin{bmatrix}
1&2&2&2\\
2&4&6&8\\
3&6&8&10
\end{bmatrix}
$$
解法①：经过消元法得到中间矩阵$U$：
$$
U=
\begin{bmatrix}
1&2&2&2\\
0&0&2&4\\
0&0&0&0
\end{bmatrix}
$$
此时主元为1和2，秩$r=2$，取自由变量$x_2$和$x_4$分别为$(1,0)$和$(0,1)$，回代得到解：
$$
\begin{align}
x_1+2x_2+2x_3+2x_4&=0\\
2x_3+4x_4&=0
\end{align}
$$

$$
x=c
\begin{bmatrix}
-2\\1\\0\\0
\end{bmatrix}
+d
\begin{bmatrix}
2\\0\\-2\\1
\end{bmatrix}
$$

解法②：在消元法的基础上进一步得到简化行阶梯矩阵$R$：
$$
R=
\begin{bmatrix}
1&2&0&-2\\
0&0&1&2\\
0&0&0&0
\end{bmatrix}
$$
主变量矩阵：
$$
I=
\begin{bmatrix}
1&0\\
0&1
\end{bmatrix}
$$
自由变量矩阵：
$$
F=
\begin{bmatrix}
2&-2\\
0&2
\end{bmatrix}
$$
交换第二列和第三列后可得：
$$
R=
\begin{bmatrix}
I&F\\
0&0
\end{bmatrix}
$$

$$
\begin{align}
RN&=0\\
\begin{bmatrix}
I&F\\
0&0
\end{bmatrix}
\begin{bmatrix}
-F\\
I
\end{bmatrix}
&=0\\
N&=
\begin{bmatrix}
-F\\
I
\end{bmatrix}
=
\begin{bmatrix}
-2&2\\
0&-2\\
1&0\\
0&1
\end{bmatrix}
\end{align}
$$
将之前交换过的两列交换回来：
$$
\begin{align}
N&=
\begin{bmatrix}
-2&2\\
1&0\\
0&-1\\
0&1
\end{bmatrix}
\\
x&=c
\begin{bmatrix}
-2\\1\\0\\0
\end{bmatrix}
+d
\begin{bmatrix}
2\\0\\-2\\1
\end{bmatrix}
\end{align}
$$

## Lecture 08

求解$Ax=b$形式

​	有解时右侧$b$需要满足的条件：$b$处于矩阵$A$的列空间内；

​	如果通过消元得到全0的行，则右侧的$b$的表达式也需要为0；

​	求通解：①先求一个特解（比如，令所有自由变量等于0）；

​				   ②求出任意解（$b=0$时的解，对应零空间）；

​				   ③通解 = 特解 + 任意解。

满秩

​	对于一个$m \times n$的矩阵$A$，其秩为$r$，有$r \leqslant m$且$r \leqslant n$；

​	(1) $r=n$时的满秩（列满秩）：

​		每一列都有一个主元，所有变量都是主变量，没有自由变量；

​		零空间内只存在零向量；

​		此时$Ax=b$的通解只有特解一个，即存在唯一解（如果有解的话）；

​	(2) $r=m$时的满秩（行满秩）：

​		每一行都有主元，有$r$个主变量，$n-r$个自由变量；

​		此时$Ax=b$必有解，且通解是特解+任意解的形式；

​	(3) $r=m=n$时的满秩：

​		零空间内只存在零向量；

​		此时$Ax=b$必有解，且存在唯一解；

|          | $Ax=0$     | $Ax=b$                                    |
| -------- | ---------- | ----------------------------------------- |
| 非满秩   | 有任意解   | 不一定有解，但如果有解，则解为特解+任意解 |
| 列满秩   | 只有零向量 | 不一定有解，但如果有解，则解为唯一解      |
| 行满秩   | 有任意解   | 一定有解，解为特解+任意解                 |
| 满秩方阵 | 只有零向量 | 一定有解，解为唯一解                      |

## Lecture 09

线性相关性

​	对于向量组，除去系数全为0的情况，如果存在一种线性组合，使得向量组的结果为零向量，则称向量组线性相关；否则，则称向量组线性无关；

​	两个向量线性相关，则代表可以由一个向量得到另一个向量，其中一个向量是重复多余的；

​	任意向量与零向量都是线性相关的；

​	对于$n$维空间，最多可以有$n$个向量线性无关，即$n$个线性无关向量可以构成$n$维空间；

矩阵的基

​	指线性无关的一组列向量，不唯一；

列空间的维数

​	列空间的维数 = 矩阵的秩 = $r$；

零空间的维数

​	零空间的维数 = 自由变量的个数 = $n-r$；

## Lecture 10

矩阵$A_{m \times n}$的四个基本 子空间

​	①列空间$C(A)$

​	②行空间$R(A)$，即$C(A^T)$

​	③零空间$N(A)$

​	④转置矩阵的零空间$N(A^T)$，又称左零空间

|                    | 维度dimension | 基basis              |
| ------------------ | ------------- | -------------------- |
| 列空间$C(A)$       | 矩阵的秩$r$   | 主列                 |
| 转置列空间$C(A^T)$ | 矩阵的秩$r$   | 行最简形$R$的前$r$行 |
| 零空间$N(A)$       | $n-r$         | 基础解系             |
| 转置零空间$N(A^T)$ | $m-r$         | $A^T$的基础解系      |

基：

​	定义：如果向量集$B={b_1,b_2...b_p}$是空间$H$的一个基，则有：

​				①$B$中各向量线性无关；

​				②由$B$生成的空间与$H$相同，即$H=Span{b_1,b_2...b_p}$；

---

实例：

​	矩阵$A$：
$$
A=
\begin{bmatrix}
1&2&3&1\\
1&1&2&1\\
1&2&3&1
\end{bmatrix}
$$
​	一、求矩阵$A$的列空间的基：
$$
A->U=
\begin{bmatrix}
1&2&3&1\\
0&-1&-1&0\\
0&0&0&0
\end{bmatrix}
$$
​		主列为第一列和第二列，则
$$
C(A)=Span{(
\begin{bmatrix}
1\\
1\\
1
\end{bmatrix}
,
\begin{bmatrix}
2\\
1\\
2
\end{bmatrix}
)}
$$


​	二、求矩阵$A$的行空间的基：

​		方法①：将$A$转置，
$$
A^T=
\begin{bmatrix}
1&1&1\\
2&1&2\\
3&2&3\\
1&1&1
\end{bmatrix}
->
\begin{bmatrix}
1&1&1\\
0&-1&0\\
0&0&0\\
0&0&0
\end{bmatrix}
$$
​			主列为第一列和第二列，则
$$
R(A)=C(A^T)=Span{(
\begin{bmatrix}
1\\2\\3\\1
\end{bmatrix}
,
\begin{bmatrix}
1\\1\\2\\1
\end{bmatrix}
)}
$$


​		方法②：

​			行变换不会改变行空间（但会改变列空间），因此$A$与其行最简形$R$的行空间相同，也就有着同样的基；基于该观点：
$$
A->R=
\begin{bmatrix}
1&0&1&1\\
0&1&1&0\\
0&0&0&0
\end{bmatrix}
$$

$$
R(A)=Span{(
\begin{bmatrix}
1\\0\\1\\1
\end{bmatrix}
,
\begin{bmatrix}
0\\1\\1\\0
\end{bmatrix}
)}
$$

​	三、求矩阵A的零空间的基

​		由之间的计算可知，$A$的第一列和第二列为主列，第三列和第四列为自由列；

​		取$x_3,x_4=(1,0)$和$(0,1)$，代入可得：$(-1,-1,1,0),(-1,0,0,1)$
$$
N(A)=Span{(
\begin{bmatrix}
-1\\-1\\1\\0
\end{bmatrix}
,
\begin{bmatrix}
-1\\0\\0\\1
\end{bmatrix}
)}
$$
​	四、求矩阵$A$的左零空间的基

​		方法①：将$A$转置，
$$
A^T=
\begin{bmatrix}
1&1&1\\
2&1&2\\
3&2&3\\
1&1&1
\end{bmatrix}
->
\begin{bmatrix}
1&1&1\\
0&-1&0\\
0&0&0\\
0&0&0
\end{bmatrix}
$$
​			可以看到$A^T$的第一列和第二列为主列，第三列为自由列；

​			取$x_3=1$，代入可得：$(-1,0,1)$
$$
N(A^T)=Span{(
\begin{bmatrix}
-1\\0\\1
\end{bmatrix}
)}
$$
​		方法②：

​			一个转换矩阵使$A$变为$R$：
$$
EA=R
$$
​			使用高斯-约旦消元法，将$A$和$I$组合起来进行消元，$E$记录下了转换过程：
$$
rref(
\begin{bmatrix}
A&|&I
\end{bmatrix})
=
\begin{bmatrix}
R&|&E
\end{bmatrix}
$$
​			将从$A$得到$R$的操作过程，在$I$上重复一遍，即可得到$E$：
$$
E=
\begin{bmatrix}
-1&2&0\\
1&-1&0\\
-1&0&1
\end{bmatrix}
$$
​			左零空间的秩此时为3-2=1，则取$E$的末尾一行作为基，可得：
$$
N(A^T)=Span{(
\begin{bmatrix}
-1\\0\\1
\end{bmatrix}
)}
$$

## Lecture 11

试图理解矩阵的维度

​	一个$3 \times 3$的矩阵向量空间的基为9，维度为9，其内的每个$3 \times 3$矩阵都可以由这9个基通过线性组合得到；

​	这些基分别为：
$$
\begin{bmatrix}
1&0&0\\
0&0&0\\
0&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&1&0\\
0&0&0\\
0&0&0
\end{bmatrix}
,...
\begin{bmatrix}
0&0&0\\
0&0&0\\
0&0&1
\end{bmatrix}
$$
​	将所有$3 \times 3$的矩阵组成的空间称为$M$，则$dim(M)=9$；

​	$M$中的对称矩阵子空间$S$的基=维数=6，这些基也是对称的：
$$
\begin{bmatrix}
1&0&0\\
0&0&0\\
0&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&0&0\\
0&1&0\\
0&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&0&0\\
0&0&0\\
0&0&1
\end{bmatrix}
\\
\begin{bmatrix}
0&1&0\\
1&0&0\\
0&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&0&1\\
0&0&0\\
1&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&0&0\\
0&0&1\\
0&1&0
\end{bmatrix}
$$
​	同理，$M$中的上三角矩阵$U$的基为：
$$
\begin{bmatrix}
1&0&0\\
0&0&0\\
0&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&0&0\\
0&1&0\\
0&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&0&0\\
0&0&0\\
0&0&1
\end{bmatrix}
\\
\begin{bmatrix}
0&1&0\\
0&0&0\\
0&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&0&0\\
0&0&1\\
1&0&0
\end{bmatrix}
,
\begin{bmatrix}
0&0&1\\
0&0&0\\
0&0&0
\end{bmatrix}
$$
​	此时，$S \cap U$的基是哪些呢？

​		一个矩阵既是对称矩阵，又是上三角矩阵，则它是一个对角矩阵；

​		对角矩阵 --- 除对角线之外的元素均为0的矩阵；

​		则它的基=维度=3，也可以通过观察$S$和$U$的基中相等的基得知；

## Lecture 12

图

​	图 = 节点 + 边；

​	图的一条边相当于矩阵的一行，一个节点相当于矩阵的一列，由此组合成的矩阵称    为“关联矩阵”；

![image-20210515174707413](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210515174707413.png)

​	该图有4个节点，5条线，因此其关联矩阵$A$应该是$5 \times 4$的；

​	将边的起点标记为-1，终点标记为1，则有：
$$
A = 
\begin{bmatrix}
-1&1&0&\\
0&-1&1&0\\
-1&0&1&0\\
-1&0&0&1\\
0&0&-1&1
\end{bmatrix}
$$
​	观察线①②③，其构成$A$的前三行，这三行不是线性无关的，第三行可以由第一行+第二行得到，表现在图中，线①②③构成一个回路（loop），线①+线②相当于线③；

​	即 **loop = dependent**.

​	(1)计算矩阵$A$的零空间：
$$
\begin{align}
Ax&=0\\
\begin{bmatrix}
-1&1&0&0\\
0&-1&1&0\\
-1&0&1&0\\
-1&0&0&1\\
0&0&-1&1
\end{bmatrix}
\begin{bmatrix}
x_1\\
x_2\\
x_3\\
x_4
\end{bmatrix}
&=0\\
\begin{bmatrix}
-x_1+x_2\\
-x_2+x_3\\
-x_1+x_3\\
-x_1+x_4\\
-x_3+x_4
\end{bmatrix}
&=0
\end{align}
$$

$$
x_1=x_2=x_3=x_4=c
$$

​		等式$Ax=0$有任意解，因此矩阵$A$不是列满秩，其列向量线性相关； 

​		从图上来看，只有四个点一样高时，才不会产生流动的线条，才能得到0；

​	(2)计算矩阵$A$的转置的零空间：
$$
\begin{align}
A^Ty&=0\\
\begin{bmatrix}
-1&0&-1&-1&0\\
1&-1&0&0&0\\
0&1&1&0&-1\\
0&0&0&1&1
\end{bmatrix}
\begin{bmatrix}
y_1\\y_2\\y_3\\y_4\\y_5
\end{bmatrix}
&=0\\
\begin{bmatrix}
1&0&1&1&0\\
0&1&1&1&0\\
0&0&0&1&1\\
0&0&0&0&0
\end{bmatrix}
\begin{bmatrix}
y_1\\y_2\\y_3\\y_4\\y_5
\end{bmatrix}
&=0
\end{align}
$$
​		主变量为$y_1,y_2,y_4$，自由变量为$y_3,y_5$，

​			取$(y3,y5)=(0,1)$和$(1,0)$，解为
$$
c
\begin{bmatrix}
1\\1\\0\\-1\\1
\end{bmatrix}
+d
\begin{bmatrix}
1\\1\\-1\\0\\0
\end{bmatrix}
$$
​		从图上来看，①+②-③和①+②+⑤-④形成了loop，都回到了起点；

---

树

​	没有回路的“图”即为“树”；

​	一个树若有$n$个节点，则其有$n-1$条边；

---

行向量的零空间的维数为$m-r$

由于$m$表示边数，$r$表示节点数-1，则有

​	$loops = edges-(nodes-1)$，洞的数量=边的数量-(节点的数量-1)

## Lecture 13

如果一个矩阵$U$的秩为3，

​	则矩阵$B=\begin{bmatrix} U\\0 \end{bmatrix}$的秩为3，矩阵$C=\begin{bmatrix} U&0\\0&U \end{bmatrix}$的秩为6；

---

对于矩阵$Ax=\begin{bmatrix} 2\\4\\2 \end{bmatrix}$，其解为
$$
x = 
\begin{bmatrix}
2\\0\\0
\end{bmatrix}
+
c
\begin{bmatrix}
1\\1\\0
\end{bmatrix}
+
d
\begin{bmatrix}
0\\0\\1
\end{bmatrix}
$$
​	（1）求矩阵$A$的行向量空间的维数；

​		解：$A_{m \times n}x_{3 \times 1}=b_{3 \times 1}$，则$m=3,n=3$，矩阵$A$为三行三列的矩阵；

​				由解的格式可知，自由变量有2个，因此$n-r=2,r=1$；

​				行向量空间的维数 = 列向量空间的维数 = 矩阵的秩 = $r$ = 1；

​	（2）求矩阵$A$；

​		解：当$c=d=0$时，
$$
x = 
\begin{bmatrix}
2\\0\\0
\end{bmatrix}
$$
​				结合$(2,4,2)$，可以得知$A$的第一列：
$$
\begin{bmatrix}
1&?&?\\
2&?&?\\
1&?&?
\end{bmatrix}
\begin{bmatrix}
2\\0\\0
\end{bmatrix}
=
\begin{bmatrix}
2\\4\\2
\end{bmatrix}
$$
​				从解中可以看到，$A$的零空间的一个解是$(0,0,1)$，可以得知$A$的第三列：
$$
\begin{bmatrix}
1&?&0\\
2&?&0\\
1&?&0
\end{bmatrix}
\begin{bmatrix}
0\\0\\1
\end{bmatrix}
=
0
$$
​				再结合零空间的解$(1,1,0)$，可以得知$A$的第二列等于负的第一列：
$$
\begin{bmatrix}
1&-1&0\\
2&-2&0\\
1&-1&0
\end{bmatrix}
\begin{bmatrix}
1\\1\\0
\end{bmatrix}
=
0
$$
​				综上所述，
$$
A=
\begin{bmatrix}
1&-1&0\\
2&-2&0\\
1&-1&0
\end{bmatrix}
$$
​	（3）当$b$为何值时，$Ax=b$一定有解？

​		解：当$b$位于矩阵$A$的列空间内时，方程有解；

​				即当$b=c\begin{bmatrix} 1\\2\\1 \end{bmatrix}$时，$Ax=b$一定有解。

---

矩阵向量空间内，所有的可逆矩阵不构成子空间（两个可逆矩阵相加不保证结果可逆）；

同理，奇异矩阵也不构成子空间（两个奇异矩阵的和不保证奇异）；

---

自身的平方为0的矩阵不止有零矩阵，如$B=\begin{bmatrix} 0&1\\0&0 \end{bmatrix}$，它的平方为0；

---

如果矩阵$C$是可逆的，则$CD$的零空间和$D$相同，$N(CD)=N(D)$，

​	即：左乘一个可逆矩阵，不改变矩阵自身的零空间；

---

矩阵$A$和$-A$拥有相同的四个子空间；

如果矩阵$A$和$B$用于相同的四个字空间，$A$不一定是$B$的倍数；

交换矩阵的两行，四个子空间中不变的是行空间和零空间；

行空间与零空间正交，它们的交集只有零向量，一个非零向量无法既在行空间又在零空间

## Lecture 14

正交(orthogonality) - 更为严苛的垂直

​	向量正交

​		若向量$x$和$y$，存在关系$x^Ty=0$，即$\sum\limits_{i=1}^{n} x_iy_i=0$，则称向量$x$和$y$正交，两个向量的夹角为$90 ^\circ$；

​		零向量与任何向量都正交；

​	子空间正交

​		若子空间$S$和$T$正交，则$S$中的任意向量与$T$中的任意向量都正交；

​		如果两个子空间相交于非零向量，那它们一定不正交，因为它们交集处的非零向量不与自身相交（只有零向量自身正交）；换句话说，如果两个子空间正交且相交，则它们的交集一定是零向量；

​		行空间与零空间正交      <-> 	 $Ax=0$

​		列空间与左零空间正交  <->  	$A^Ty=0$

---

在解决现实问题时，由于观测误差等原因，结果$b$中包含错误数据，这可能导致$Ax=b$无解，此时需要利用转置矩阵：
$$
A^TAx'=A^Tb
$$
$A^TA$具有某些特殊的性质：①它是一个方阵 ；

​												②它是对称的；

​												③$A^TA$的秩与$A$相等 -> 当且仅当$A$列满秩时，$A^TA$是可逆的；

​												④$A^TA$的零空间与$A$相等；

## Lecture 15

投影

​	为什么需要投影？

​		求解$Ax=b$时，若$b$不在$A$的列空间则无解，此时可以通过投影将$b$化为最接近的、位于列空间的一个；

​		将$Ax=b$化为$Ax'=p$；

​	对于一维直线，向量$b$在向量$a$上的投影为$p$：

![image-20210516232106617](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210516232106617.png)

​	可以看到，$p$和$a$成倍数关系，设$p=Xa$；

​	由于$a$与虚线正交，可得（其中$a^Ta$为一个数，可以化为除法运算）：
$$
\begin{align}
a^T(b-p)&=0\\
a^T(b-Xa)&=0\\
a^Tb&=Xa^Ta\\
X&=\frac{a^Tb}{a^Ta}\\
p&=a\frac{a^Tb}{a^Ta}=\frac{aa^T}{a^Ta}b
\end{align}
$$
​	则投影矩阵$P=\frac{aa^T}{a^Ta}$；

​	可以看到，投影矩阵$P$具有以下性质：

​		①$P$的转置$P^T=P$；

​		②再对$p$在$a$上做一次投影，其还是为$p$，即$P^2=P$；

---

​	对于二维平面，向量$b$在平面上做投影，已知该平面即为矩阵$A$的列空间，$A$的列空间的基为$a_1$和$a_2$：

![image-20210517002130653](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210517002130653.png)
$$
p=Ax'=ca_1+da_2
$$
​	法线$b-p$垂直于$A$的列空间，则可知法线$b-p$位于$A$的左零空间；

​	法线$b-p$垂直于$a1$和$a_2$，
$$
\begin{align}
a_1^T(b-Ax')&=0\\
a_2^T(b-Ax')&=0\\
\begin{bmatrix}
a_1^T\\a_2^T
\end{bmatrix}
(b-Ax')&=0\\
A^T(b-Ax')&=0\\
A^Tb&=A^TAx'\\
x'&={(A^TA)}^{-1}{A^Tb}\\
p&=Ax'\\
&=A{(A^TA)}^{-1}{A^Tb}\\
\end{align}
$$
​	得投影矩阵$P=A{(A^TA)}^{-1}{A^T}$；

​	如果$P$是可逆矩阵，则
$$
\begin{align}
P&=A{(A^TA)}^{-1}{A^T}\\
&=AA^{-1}(A^T)^{-1}A^T\\
&=I
\end{align}
$$
​	此时$p=b$，即$b$原本就在$A$的列空间，其对列空间的投影即为其自身；

---

|             | 维数  | 形式                    |
| ----------- | ----- | ----------------------- |
| 投影矩阵$P$ | 1维   | $P=\frac{aa^T}{a^Ta}$   |
|             | $n$维 | $P=A{(A^TA)}^{-1}{A^T}$ |

|             | 性质    |
| ----------- | ------- |
| 投影矩阵$P$ | $P^T=P$ |
|             | $P^2=P$ |

|            | 形式                                                         |
| ---------- | ------------------------------------------------------------ |
| 近似解$x'$ | $A^TAx'=A^Tb$                                                |
|            | $x'={(A^TA)}^{-1}{A^Tb}$（假设此处的$A$列无关，因此$A^TA$为对称可逆矩阵，可以消元） |



## Lecture 16

投影的应用 - 最小二乘法

![image-20210519004627043](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210519004627043.png)

![image-20210519021346016](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210519021346016.png)

对于显然无解的三个点，找到误差最小的直线；

​	设直线为$y=C+Dx$，有
$$
\begin{align}
C+D&=1\\
C+2D&=2\\
C+3D&=2
\end{align}
$$

$$
\begin{bmatrix}
1&1\\
1&2\\
1&3
\end{bmatrix}
\begin{bmatrix}
C\\D
\end{bmatrix}
=
\begin{bmatrix}
1\\2\\2
\end{bmatrix}
$$

​	套用之前得到的近似解公式：
$$
\begin{align}
A^TAx'&=A^Tb\\
x'&=
\begin{bmatrix}
\frac{2}{3}\\
\frac{1}{2}
\end{bmatrix}
\end{align}
$$
​	最优解直线为：
$$
y=\frac{2}{3}+\frac{1}{2}x
$$
​	近似点为：
$$
p=(\frac{7}{6},\frac{10}{6},\frac{13}{6})
$$
​	距离$b$的误差为：
$$
e=(-\frac{1}{6},\frac{2}{6},+\frac{1}{6})
$$
​	$p$与$e$之间的关系：$p$位于列空间，而$e$垂直于整个列空间，因此$e$位于左零空间；

---

关于$A^TA$的特殊之处

​	结论：如果$A$的列无关，则$A^TA$一定是可逆矩阵；



## Lecture 17

正交基

​	一组向量，$q_1,q_2,q_3,...,q_n$，其两个向量之间两两正交，则称为正交基；

​	若其还具有以下性质：
$$
\begin{align}
q_i^Tq_j&=0 \quad (i \neq j)\\
q_i^Tq_j&=1 \quad (i = j)
\end{align}
$$
​	则称为标准正交基；

---

​	构建一个标准正交矩阵$Q$，
$$
Q=
\begin{bmatrix}
q_1&q_2&...&q_n
\end{bmatrix}
$$
​	则有：
$$
Q^TQ=I
$$
​	若此时恰好$Q$是一个方阵，则其可逆$Q^{-1}Q=I$，结合可知
$$
Q^T=Q^{-1}
$$

---

​	对应到投影矩阵上，如果$Q$是标准正交矩阵，
$$
\begin{align}
P&=Q(Q^TQ)^{-1}Q^T=QQ^T\\
Q^TQx'&=Q^Tb\\
x'&=Q^Tb
\end{align}
$$
​	在此基础上，如果$Q$还是方阵，
$$
\begin{align}
P&=QQ^T=QQ^{-1}=I\\
x'&=Q^Tb=Q^{-1}b
\end{align}
$$

---

格拉姆-施密特正交化法

​	对于两个线性无关向量$a$和$b$，希望得到它们的标准正交向量$q_1$和$q_2$；

​	思路：找到两个正交的向量$A$和$B$，然后单位化得到$q_1$和$q_2$，
$$
q_1=\frac{A}{||A||},q_2=\frac{B}{||B||}
$$
​	首先，用$a$确定$A$，

![image-20210520014151031](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210520014151031.png)
$$
\begin{align}
p&=Pb=\frac{aa^T}{a^Ta}b=a\frac{a^Tb}{a^Ta}\\
&=A\frac{A^Tb}{A^TA}\\
&=\frac{A^Tb}{A^TA}A \quad (\frac{A^Tb}{A^TA}是一个常量)\\
B&=e\\
&=b-p\\
&=b-\frac{A^Tb}{A^TA}A
\end{align}
$$
​	此时，再加上一个向量$C$，其与$A$、$B$正交，则类比$B$的解的形式可以想到，$C$的解为$c-c$在$ab$平面的投影；
$$
C=c-\frac{A^Tc}{A^TA}A-\frac{B^Tc}{B^TB}B
$$

---

​	对于$a=(1,1,1)$和$b=(1,0,2)$，求标准正交矩阵；

​	解：设$A$和$B$,
$$
\begin{align}
A&=a=
\begin{bmatrix}
1\\1\\1
\end{bmatrix}\\
B&=b-\frac{A^Tb}{A^TA}A\\
&=b-A\\
&=
\begin{bmatrix}
0\\-1\\1
\end{bmatrix}
\end{align}
$$

$$
q_1=\frac{1}{\sqrt{3}}
\begin{bmatrix}
1\\1\\1
\end{bmatrix}
,
q_2=\frac{1}{\sqrt{2}}
\begin{bmatrix}
0\\-1\\1
\end{bmatrix}
$$

$$
Q=\begin{bmatrix}
q_1&q_2
\end{bmatrix}
$$

---

原矩阵$A$与其标准正交矩阵$Q$的关系

​	①从$A$到$Q$只进行了列变换和乘除操作，因此$A$的列空间没有发生变化，$A$和$Q$和列空间相同；

​	从$A$得到$Q$的过程可以逆向为：
$$
\begin{align}
A&=QR\\
Q^TA&=Q^TQR\\
Q^TA&=R\\
R&=
\begin{bmatrix}
q_1\\q_2
\end{bmatrix}
\begin{bmatrix}
a&b
\end{bmatrix}\\
&=
\begin{bmatrix}
q_1a&q_1b\\
q_2a&q_2b
\end{bmatrix}
\end{align}
$$
​	又$q_2$与$a$正交，有：
$$
R=
\begin{bmatrix}
q_1a&q_1b\\
0&q_2b
\end{bmatrix}
$$
​	可以看到，R是一个上三角矩阵，因此②$A$可以被分解为一个标准正交矩阵和一个上三角矩阵；

## Lecture 18

行列式（determinant）

​	每个方阵都有与其相关的行列式，记作$detA$或$|A|$；

​	行列式可用于检测矩阵的可逆性：

​		矩阵可逆 <---> 行列式不为0；

​		矩阵奇异 <---> 行列式为0；




|        | 性质                                                         | 推论                                                         |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 行列式 | ①单位矩阵的行列式值为1，即$detI=1$；                         |                                                              |
|        | ②交换行，行列式的值会取反；                                  | 将单位矩阵$I$的行交换，得到置换矩阵$P$，置换矩阵的行列式值为1或-1，即$detP=\pm 1$；<br />交换列，行列式的值同样会取反； |
|        | ③行列式乘以系数t，等于行列式的其中一行的每个元素都乘以系数t；<br />行列式可以拆分和组合； |                                                              |
|        | ④如果行列式的两行相等，则该行列式的值为0；                   | 如果行列式的两列成倍数关系，那么该行列式的值为0；            |
|        | ⑤一行减去另一行的$k$倍，行列式的值不变；                     |                                                              |
|        | ⑥若有一行是0，则行列式的值为0；                              | 若有一列为0，则行列式的值也为0；                             |
|        | ⑦对于上三角矩阵，其行列式的值等于所有对角线上的元素的乘积；  |                                                              |
|        | ⑧当且仅当矩阵$A$为奇异矩阵，$detA=0$；                       |                                                              |
|        | ⑨矩阵乘积的行列式等于矩阵行列式的乘积，即$det(AB)=(detA)(detB)$； | 逆矩阵的行列式为$det(A^{-1})=\frac{1}{detA}$<br />矩阵平方行列式为$det(A^2)=(detA)^2$<br />矩阵倍数的行列式为$det(kA)=k^ndetA$ |
|        | ⑩矩阵转置不改变行列式的值，即$det(A^T)=detA$；               |                                                              |

$$
t
\left|
\begin{matrix}
a&b\\
c&d
\end{matrix}
\right|
=
\left|
\begin{matrix}
at&bt\\
c&d
\end{matrix}
\right|
=
\left|
\begin{matrix}
a&b\\
ct&dt
\end{matrix}
\right|
$$

$$
\left|
\begin{matrix}
a+a'&b+b'\\
c&d
\end{matrix}
\right|
=
\left|
\begin{matrix}
a&b\\
c&d
\end{matrix}
\right|
+
\left|
\begin{matrix}
a'&b'\\
c&d
\end{matrix}
\right|
$$


$$
\begin{align}
\left|
\begin{matrix}
a&b\\
c-ka&d-kb
\end{matrix}
\right|
&=
\left|
\begin{matrix}
a&b\\
c&d
\end{matrix}
\right|
+
\left|
\begin{matrix}
a&b\\
-ka&-kb
\end{matrix}
\right|
\\
&=
\left|
\begin{matrix}
a&b\\
c&d
\end{matrix}
\right|
-k
\left|
\begin{matrix}
a&b\\
a&b
\end{matrix}
\right|
\\
&=
\left|
\begin{matrix}
a&b\\
c&d
\end{matrix}
\right|

\end{align}
$$

## Lecture 19

行列式的值

​	对于2阶行列式，
$$
\begin{align}
\left|
\begin{matrix}
a&b\\
c&d
\end{matrix}
\right|
=
\left|
\begin{matrix}
a&0\\
c&d
\end{matrix}
\right|
+
\left|
\begin{matrix}
0&b\\
c&d
\end{matrix}
\right|\\
&=
\left|
\begin{matrix}
a&0\\
c&0
\end{matrix}
\right|
+
\left|
\begin{matrix}
a&0\\
0&d
\end{matrix}
\right|
+
\left|
\begin{matrix}
0&b\\
c&0
\end{matrix}
\right|
+
\left|
\begin{matrix}
0&b\\
0&d
\end{matrix}
\right|\\
&=
\left|
\begin{matrix}
a&0\\
0&d
\end{matrix}
\right|
+
\left|
\begin{matrix}
0&b\\
c&0
\end{matrix}
\right|\\
&=
\left|
\begin{matrix}
a&0\\
0&d
\end{matrix}
\right|
-
\left|
\begin{matrix}
c&0\\
0&b
\end{matrix}
\right|\\
=ad-bc
\end{align}
$$

​	对于3阶行列式，
$$
\begin{align}
\left|
\begin{matrix}
a_{11}&a_{12}&a_{13}\\
a_{21}&a_{22}&a_{23}\\
a_{31}&a_{32}&a_{33}
\end{matrix}
\right|
=
\left|
\begin{matrix}
a_{11}&0&0\\
0&a_{22}&0\\
0&0&a_{33}
\end{matrix}
\right|
+
\left|
\begin{matrix}
a_{11}&0&0\\
0&0&a_{23}\\
0&a_{32}&0
\end{matrix}
\right|\\
+
\left|
\begin{matrix}
0&a_{12}&0\\
a_{21}&0&0\\
0&0&a_{33}
\end{matrix}
\right|
+
\left|
\begin{matrix}
0&a_{12}&0\\
0&0&a_{23}\\
a_{31}&0&0
\end{matrix}
\right|\\
+
\left|
\begin{matrix}
0&0&a_{13}\\
a_{21}&0&0\\
0&a_{32}&0
\end{matrix}
\right|
+
\left|
\begin{matrix}
0&0&a_{13}\\
0&a_{22}&0\\
a_{31}&0&0
\end{matrix}
\right|\\
=(123)+(132)\\+(213)+(231)\\+(312)+(321)
\end{align}
$$
​	对于$n$阶行列式，其项数有$n!$项，行列式的值为$detA=\sum \limits_{i=1}^{n!}f_i$；

---

代数余子式

​	将$n$阶矩阵化为$n-1$阶；

​	元素$a_{ij}$的代数余子式表示行列式的分解式中含有该元素的所有子项的和；

​	如3解行列式中，
$$
\left|
\begin{matrix}
a_{11}&a_{12}&a_{13}\\
a_{21}&a_{22}&a_{23}\\
a_{31}&a_{32}&a_{33}
\end{matrix}
\right|
$$
​	元素$a_{11}$的代数余子式为：
$$
\left|
\begin{matrix}
a_{11}&|&a_{12}&a_{13}\\
---&---&---&---\\
a_{21}&|&a_{22}&a_{23}\\
a_{31}&|&a_{32}&a_{33}
\end{matrix}
\right|
$$
​	设元素$a_{ij}$对应的代数余子式为$C_{ij}$，则行列式的值为（沿第一行展开）：
$$
detA=\sum \limits_{i=1}^{n}(\pm)a_{1i}C_{1i}
$$
​	当$i+j$为偶数时，符号为正；当$i+j$为奇数时，符号为负；



##  Lecture 20

逆矩阵公式

​	对于2阶矩阵
$$
{
\begin{bmatrix}
a_{11}&a_{12}\\
a_{21}&a_{22}
\end{bmatrix}
}^{-1}
=
\frac{1}{a_{11}a_{22}-a_{12}a_{21}}
\begin{bmatrix}
C_{11}(a_{22})&C_{21}(-a_{12})\\
C_{12}(-a_{21})&C_{22}(a_{11})
\end{bmatrix}
$$


​	由$A^T$的各元素的代数余子式组成的矩阵称为伴随矩阵，表示为$A^*$;

​	矩阵$A$的逆矩阵$A^{-1}$等于$\frac{1}{detA}$乘以$A^*$；
$$
A^{-1}=\frac{1}{detA}A^*
$$

---

克拉默法则
$$
\begin{align}
Ax&=b\\
x&=A^{-1}b\\
&=\frac{1}{detA}A^*b

\end{align}
$$
​	假设$A$是3阶矩阵，
$$
A=
\begin{bmatrix}
a_1&a_2&a_3
\end{bmatrix}
$$
​	则解$x$为，
$$
x_1=\frac{1}{detA}detB_1\\
x_2=\frac{1}{detA}detB_2\\
x_3=\frac{1}{detA}detB_3
$$
​	其中
$$
B_1=
\begin{bmatrix}
b&a_2&a_3
\end{bmatrix}\\
B_2=
\begin{bmatrix}
a_1&b&a_3
\end{bmatrix}\\
B_3=
\begin{bmatrix}
a_1&a_2&b
\end{bmatrix}\\
$$

---

行列式与体积

![image-20210522141442225](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210522141442225.png)

​	行列式的值等于以列向量为棱的平行四边体的体积；

## Lecture 21

特征值与特征向量

​	对于一般的$x$，$Ax$得到的结果的方向与$x$不一定相同，但对于特征向量$x$，其结果$Ax$始终与$x$平行，即$Ax$与$x$成倍数关系，写作$Ax=\lambda x$，其中$\lambda$称为特征值；

​	比如对于投影矩阵$P$，向量$b$通过投影矩阵$P$在平面上投影得到向量$p$，此场景中有哪些特征向量？

​		(1) 所有处于平面上的向量，其投影后还是自身，特征值为1；

​		(2) 所有垂直于平面上的向量，其投影后为零向量，特征值为0；

​	求解特征向量与特征值
$$
\begin{align}
Ax&=\lambda x\\
(A-\lambda I)x&=0
\end{align}
$$
​		矩阵$A-\lambda I$必须是一个奇异矩阵，否则方程只有零解，而零向量不能算作特征向量；
$$
det(A-\lambda I)=0
$$
​		假如此时
$$
A=
\begin{bmatrix}
3&1\\
1&3
\end{bmatrix}\\
\begin{align}
\left|
\begin{matrix}
3-\lambda & 1\\
1&3-\lambda
\end{matrix}
\right|
&=0\\
(3-\lambda)^2-1&=0\\
\lambda^2-6\lambda +8&=0 \quad (6=trace,8=detA)\\
\lambda&=2,4
\end{align}
$$
​		当$\lambda=2$时，
$$
\begin{align}
\begin{bmatrix}
1&1\\1&1
\end{bmatrix}
x=0\\
x=c
\begin{bmatrix}
1\\-1
\end{bmatrix}
\end{align}
$$
​		当$\lambda=4$时，
$$
\begin{align}
\begin{bmatrix}
-1&1\\1&-1
\end{bmatrix}
x=0\\
x=c
\begin{bmatrix}
1\\1
\end{bmatrix}
\end{align}
$$
​		观察$\begin{bmatrix} 0&1\\1&0\end{bmatrix}$和$\begin{bmatrix} 3&1\\1&3\end{bmatrix}$的特征值，可以发现，当矩阵+$nI$后，其对应的几个特征值也+$n$，而特征向量不变；

​		矩阵$A$的特征值为$\lambda$，矩阵$B$的特征值为$\alpha$，则矩阵$A+B$的特征值不一定为$\lambda+\alpha$，仅当$B=nI$时才成立；

---

​	对于旋转矩阵（能将向量旋转$\theta^\circ$而不改变向量大小的矩阵）：
$$
Q=
\begin{bmatrix}
cos\theta & -sin\theta\\
sin\theta & cos\theta
\end{bmatrix}
$$
​	当$\theta=90^\circ$时，
$$
Q=
\begin{bmatrix}
0&-1\\
1&0
\end{bmatrix}
$$
​	求$Q$的特征值$\lambda$：
$$
\begin{align}
trace&=0+0=0\\
detQ&=0-(-1)=1\\
\lambda^2+1&=0\\
\lambda &= \pm i
\end{align}
$$

---

​	对于对角矩阵，如
$$
\begin{bmatrix}
3&1\\
0&3
\end{bmatrix}
$$

$$
\begin{align}
trace &= 3+3=6\\
detA&=3*3=9\\
\lambda^2-6\lambda+9&=0\\
(\lambda-3)^2&=0\\
\lambda&=3
\end{align}
$$

​	此时只有一个特征值，只有一个特征向量，对于这样的矩阵称为退化矩阵（degenerate matrix）；

|        | 性质                                                   |
| ------ | ------------------------------------------------------ |
| 特征值 | ①$n$阶矩阵有$n$个特征值；                              |
|        | ②特征值的和等于矩阵对角线元素的和，也就是迹（trace）； |



## Lecture 22

特征值矩阵与特征向量矩阵

​	将矩阵$A$的所有特征向量提取出来组成一个矩阵，称为特征向量矩阵；
$$
S=
\begin{bmatrix}
x_1&x_2&...&x_n
\end{bmatrix}
$$
​	将矩阵$A$与其特征向量矩阵$S$相乘，
$$
\begin{align}
AS&=
\begin{bmatrix}
Ax_1&Ax_2&...&Ax_n
\end{bmatrix}\\
&=
\begin{bmatrix}
\lambda_1x_1&\lambda_2x_2&...&\lambda_nx_n
\end{bmatrix}\\
&=
\begin{bmatrix}
x_1&x_2&...&x_n
\end{bmatrix}
\begin{bmatrix}
\lambda_1&0&...&0\\
0&\lambda_2&...&0\\
0&0&...&0\\
0&0&0&\lambda_n
\end{bmatrix}\\
&=S\Lambda
\end{align}
$$
​	其中$\Lambda$称为特征值矩阵，其对角线元素均为特征值；

​	对角化（对于特征向量矩阵$S$不可逆的矩阵，不可对角化）：
$$
\begin{align}
AS&=S\Lambda\\
\Lambda &= S^{-1}AS\\
A&=S\Lambda S^{-1}
\end{align}
$$
​	考虑$A^2$的情况：
$$
\begin{align}
A^2x&=A\lambda x\\
&=\lambda Ax\\
&=\lambda^2x
\end{align}
$$
​	即$A^2$的特征值为$\lambda^2$；
$$
\begin{align}
A^2&=S\Lambda S^{-1}S\Lambda S^{-1}\\
&=S\Lambda^2S^{-1}

\end{align}
$$
​	即$A^2$的特征值矩阵为$\Lambda^2$；

| 矩阵  | 特征值      | 特征值矩阵  | 特征向量矩阵 |
| ----- | ----------- | ----------- | ------------ |
| $A$   | $\lambda$   | $\Lambda$   | $S$          |
| $A^k$ | $\lambda^k$ | $\Lambda^k$ | $S$          |

---

假设有一组向量$u_0,u_1,u_2,...,u_k$，其具有规律$u_{k+1}=Au_k$，求解$u_{100}$；
$$
\begin{align}
u_1&=Au_0\\
u_2&=Au_1=A^2u_0\\
&...\\
u_k&=A^ku_0
\end{align}
$$
此时空有形式，但还是无法求解$u_{100}$；

如何求解$u_{100}$？
$$
\begin{align}
u_0&=c_1x_1+c_2x_2+...+c_nx_n\\
Au_0&=c_1\lambda_1x_1+c_2\lambda_2x_2+...+c_n\lambda_nx_n\\
&=u_0\Lambda\\
u_{100}&=A^{100}u_0=u_0\Lambda^{100}
\end{align}
$$
此时$\Lambda^{100}$的值可以算出，能够得到$u_{100}$的值；

---

求解斐波那契数列（0,1,1,2,3,5,8,13,21,...）的第100项；

观察可知，斐波那契数列具有规律：
$$
\begin{align}
F_0&=0\\
F_1&=1\\
F_{k+2}&=F_{k+1}+F_k
\end{align}
$$
思路：将斐波那契数列构建出$u_k=A^ku_0$的结构；

设
$$
u_k=
\begin{bmatrix}
F_{k+1}\\F_k
\end{bmatrix}
$$
则
$$
\begin{align}
u_{k+1}&=
\begin{bmatrix}
F_{k+2}\\
F_{k+1}
\end{bmatrix}\\
&=
\begin{bmatrix}
F_{k+1}+F_k\\
F_{k+1}
\end{bmatrix}\\
&=
\begin{bmatrix}
1&1\\
1&0
\end{bmatrix}
\begin{bmatrix}
F_{k+1}\\
F_{k}
\end{bmatrix}\\
&=
\begin{bmatrix}
1&1\\
1&0
\end{bmatrix}
u_k
\end{align}
$$
得到
$$
A=
\begin{bmatrix}
1&1\\
1&0
\end{bmatrix}
$$

$$
\begin{align}
(1-\lambda)(-\lambda)-1&=0\\
\lambda^2-\lambda-1&=0\\
(\lambda-\frac{1}2{})^2-\frac{5}{4}&=0\\
\lambda&=\frac{1}{2} \pm \frac{\sqrt{5}}{2}
\end{align}
$$

则
$$
u_{100}=c_1\lambda_1^{100}x_1+c_2\lambda_2^{100}x_2
$$
其中
$$
\begin{align}
A-\lambda I&=
\begin{bmatrix}
1-\lambda&1\\
1&-\lambda
\end{bmatrix}\\
(A-\lambda I)x&=0\\
\begin{bmatrix}
1-\lambda&1\\
1&-\lambda
\end{bmatrix}
\begin{bmatrix}
\lambda\\1
\end{bmatrix}
&=0
\end{align}
$$

$$
x_1=
\begin{bmatrix}
\lambda_1\\1
\end{bmatrix}
,
x_2=
\begin{bmatrix}
\lambda_2\\1
\end{bmatrix}
$$

代入计算即可。



## Lecture 23

解微分方程
$$
\begin{align}
\frac{du_1}{dt}&=-u_1+2u_2\\
\frac{du_2}{dt}&=u_1-2u_2
\end{align}
$$

已知当$t=0$时，$u_0=\begin{bmatrix}1\\0\end{bmatrix}$，求$u_t$；

可以看到，当$t=0$，即最初时刻，$u_1=1,u_2=0$，且$u_1$的导数小于0，$u_2$的导数大于0，说明$u_1$在减小而$u_2$在增大，且减小和增大的趋势在逐渐减弱，最后趋于一个稳态；

解：
$$
A=
\begin{bmatrix}
-1&2\\
1&-2
\end{bmatrix}
$$

$$
\begin{align}
(-1-\lambda)(-2-\lambda)-2&=0\\
\lambda^2+3\lambda&=0\\
\lambda_1&=0\\
\lambda_2&=-3
\end{align}
$$

$$
\begin{bmatrix}
-1-0&2\\1&-2-0
\end{bmatrix}
->x_1=
\begin{bmatrix}
2\\1
\end{bmatrix}
$$


$$
\begin{bmatrix}
-1-(-3)&2\\1&-2-(-3)
\end{bmatrix}
->x_2=
\begin{bmatrix}
1\\-1
\end{bmatrix}
$$
试图构建$u_k=\Lambda^ku_0$的形式：

设
$$
u_t=
\begin{bmatrix}
u_{1(t)}\\u_{2(t)}
\end{bmatrix}
=
c_1e^{\lambda_1 t}x_1+c_2e^{\lambda_2 t}x_2
$$

$$
\begin{align}
\frac{du_t}{dt}&=c_1\lambda_1e^{\lambda_1 t}x_1+c_2\lambda_2e^{\lambda_2 t}x_2\\
&=A(c_1e^{\lambda_1 t}x_1+c_2e^{\lambda_2 t}x_2)\\
&=Au_t
\end{align}
$$


$$
u_{t+1}=\frac{du_t}{dt}=Au_t
$$
已知
$$
u_0=
\begin{bmatrix}
1\\0
\end{bmatrix}
$$
计算$c_1,c_2$，
$$
c_1
\begin{bmatrix}
2\\1
\end{bmatrix}
+c_2
\begin{bmatrix}
1\\-1
\end{bmatrix}
=
\begin{bmatrix}
1\\0
\end{bmatrix}\\
c_1=c_2=\frac{1}{3}
$$
综上所述，
$$
u_t=\frac{1}{3}x_1+\frac{1}{3}e^{-3t}x_2
$$
观察解的形式，前一项不变，后一项随着$t$的增大而减小，符合之前观察到的趋势；

极限状态，
$$
u_\infty=\frac{1}{3}
\begin{bmatrix}
2\\1
\end{bmatrix}
$$

---

微分方程的稳态，指$u_t$最终等于一个常数；

若想存在稳态，需要

​	①$e^{\lambda t}->0$，即$\lambda<0$（若$\lambda$的形式为复数，则只有实数部分才起作用），如果任何$\lambda$的实数部分$>0$，则解无法收敛；

​	②矩阵的迹小于0；

​	③矩阵的行列式的值大于0；

---

解耦

​	回到上一个方程中，可以看到$A$的两列相互耦合，
$$
A=
\begin{bmatrix}
-1&2\\
1&-2
\end{bmatrix}
$$
​	可以用特征值和特征向量来对角化，进行解耦合；

​	设$u=Sv$，
$$
\begin{align}
\frac{du}{dt}&=Au\\
\frac{dSv}{dt}&=ASv\\
\frac{dv}{dt}&=S^{-1}ASv=\Lambda v
\end{align}
$$
​	此时的$\Lambda$是不耦合的；
$$
\frac{dv_1}{dt}=\lambda_1v_1\\
\frac{dv_2}{dt}=\lambda_2v_2\\
$$

$$
\begin{align}
\frac{dv}{dt}&=\Lambda v->v_t=e^{\Lambda t}v_0\\
\frac{du}{dt}&=A u->u_t=e^{A t}u_0\\
\because A&=S\Lambda S^{-1},e^{At}=Se^{\Lambda t}S^{-1}\\
\therefore u_t&=Se^{\Lambda t}S^{-1}u_0
\end{align}
$$

​	为什么$e^{At}=Se^{\Lambda t}S^{-1}$？

​		$e^{At}$称为矩阵指数；

​		幂级数公式：
$$
e^x=1+x+\frac{x^2}{2}+\frac{x^3}{6}+...+\frac{x^n}{n!}
$$
​		矩阵版本的幂级数公式：
$$
e^{At}=I+At+\frac{(At)^2}{2}+\frac{(At)^3}{6}+...+\frac{(At)^n}{n!}
$$
​		而$A=S\Lambda S^{-1}$，$A^n=S\Lambda^n S^{-1}$，
$$
\begin{align}
e^{At}&=I+S\Lambda S^{-1}t+\frac{S\Lambda^2S^{-1}t^2}{2}+...+
\frac{S\Lambda^nS^{-1}t^n}{n!}\\
&=Se^{\Lambda t}S^{-1}
\end{align}
$$


## lecture 24

马尔可夫矩阵

​	马尔可夫矩阵满足两条性质（其幂矩阵也满足）：

​		①所有元素大于等于0；

​		②每一列元素的和为1；

​	讨论马尔可夫矩阵的幂的稳态

​		微分矩阵中，若想得到稳态，需要$\lambda=0$，使得$e^{\lambda t}=1$；

​		幂矩阵中，若想得到稳态，需要$\lambda =1$，使得$\lambda^k=1$；

​			①其中一个$\lambda=1$；

​			②其他$|\lambda|<1$；

​		为何每一列元素的和为1$->$特征值为1？

​			$A$的每一元素的和为1，则$A-I$中，每一列都被减去了1，则每一列元素的何为0；

​			即所有行的和为0，即存在至少一行可以由其他行通过线性组合得到，$A-I$是奇异的；

​			因此，1是其中一个特征值；

---

马尔可夫矩阵的应用

​	马尔可夫矩阵常用于概率领域，因此要求元素为正且和为1（$100\%$）；

​	例如
$$
\begin{bmatrix}
U_甲\\U_乙
\end{bmatrix}_{t=k+1}
=
\begin{bmatrix}
0.9&0.2\\
0.1&0.8
\end{bmatrix}
\begin{bmatrix}
U_甲\\U_乙
\end{bmatrix}_{t=k}
$$
​	表示每次迁移，甲地90%人留在甲地，10%的人流向乙地；乙地80%的人留在乙地，20%的人流向甲地；

​	初始时，甲地有0人，乙地有1000人，
$$
\begin{bmatrix}
U_甲\\U_乙
\end{bmatrix}_{t=0}
=
\begin{bmatrix}
0\\1000
\end{bmatrix}
$$
​	经过一次迁移后，
$$
\begin{bmatrix}
U_甲\\U_乙
\end{bmatrix}_{t=1}
=
\begin{bmatrix}
0.9&0.2\\
0.1&0.8
\end{bmatrix}
\begin{bmatrix}
0\\1000
\end{bmatrix}
=
\begin{bmatrix}
200\\800
\end{bmatrix}
$$
​	如果经过无数次迁移后，两地的人数为多少呢？

​	计算特征值和特征向量：
$$
\begin{align}
\left|
\begin{matrix}
0.9-\lambda&0.2\\
0.1&0.8-\lambda
\end{matrix}
\right|
&=
(0.9-\lambda)(0.8-\lambda)-0.1 \times 0.2\\
&=\lambda^2-1.7\lambda+0.70\\
&=(\lambda-0.7)(\lambda-1)\\
&=0\\
\lambda_1&=0.7\\
\lambda_2&=1
\end{align}
$$

$$
\begin{align}
\begin{bmatrix}
0.2&0.2\\
0.1&0.1
\end{bmatrix}
->x_1&=
\begin{bmatrix}
1\\-1
\end{bmatrix}
\\
\begin{bmatrix}
-0.1&0.2\\
0.1&-0.2
\end{bmatrix}
->
x_2&=
\begin{bmatrix}
2\\1
\end{bmatrix}
\end{align}
$$

​	幂矩阵：
$$
\begin{align}
u_k&=c_1\lambda_1^kx_1+c_2\lambda_2^kx_2\\
&=c_11^kx_1+c_2(0.7)^kx_2
\end{align}
$$
​	当$k->\infty$时，$(0.7)^k$趋近于0，则$u_k=c_1x_1$；

​	代入初始值，计算$c_1$：
$$
u_0=
c_1
\begin{bmatrix}
2\\1
\end{bmatrix}
+
c_2
\begin{bmatrix}
1\\-1
\end{bmatrix}
=
\begin{bmatrix}
0\\1000
\end{bmatrix}
$$

$$
c_1=\frac{1000}{3},c_2=-\frac{2000}{3}
$$

​	则当$k->\infty$时，$u_k=\frac{1000}{3}\begin{bmatrix} 2\\1\end{bmatrix}$；

---

傅里叶级数

​	假设有一组标准正交基$q_1,q_2,...,q_n$，它们组成$n$维空间，此空间的任意向量$v$可由这组基的线性组合得到：
$$
v=q_1x_1+q_2x_2+...+q_nx_n
$$
​	使用矩阵表示：
$$
\begin{align}
v&=Qx\\
x&=Q^{-1}v=Q^Tv
\end{align}
$$

---

已知向量$a=\begin{bmatrix} 2\\1\\2 \end{bmatrix}$，（1）求三维空间中能够投影在$a$上的投影矩阵$P$；

解：
$$
P=A(A^TA)^{-1}A^T
$$
​	对于一维的$A$，可简化为：
$$
\begin{align}
P&=
\frac{aa^T}{a^Ta}\\
&=\frac{1}{9}
\begin{bmatrix}
2\\1\\2
\end{bmatrix}
\begin{bmatrix}
2&1&2
\end{bmatrix}\\
&=
\frac{1}{9}
\begin{bmatrix}
4&2&4\\
2&1&2\\
4&2&4
\end{bmatrix}
\end{align}
$$
（2）求矩阵$P$的特征值与特征向量；

解：可以看到，矩阵$P$的秩为1，其零空间是二维的，则有其中两个特征值为0；

​		又矩阵$P$的迹为1，则第三个特征值为1；

​		当$\lambda=0$时，
$$
x_1=\begin{bmatrix}
0\\-2\\1
\end{bmatrix}
,
x_2=\begin{bmatrix}
1\\-2\\0
\end{bmatrix}
$$
​		当$\lambda=1$时，
$$
\frac{1}{9}
\begin{bmatrix}
-5&2&4\\
2&-8&2\\
4&2&-5
\end{bmatrix}
->
x_3=
\begin{bmatrix}
2\\1\\2
\end{bmatrix}
$$
（3）已知$u_{k+1}=Pu_k$，$u_0=\begin{bmatrix} 9\\9\\0\end{bmatrix}$，求解$u_k$；

解：
$$
\begin{align}
u_k&=c_1\lambda_1^kx_1+c_2\lambda_2^kx_2+c_3\lambda_3^kx_3\\
&=c_3x_3 \quad(x>0)
\end{align}
$$
​	当$k=0$时，由于$0^0=1$，所以
$$
u_0=c_1x_1+c_2x_2+c_3x_3
$$
​	观察$u_k$的形式，可以看出$u_k=u_1=u_2=...=u_{k-1}$，这也符合对已经在$A$上的向量反复投影得到的还是自身的性质；
$$
\begin{align}
u_1&=Pu_0\\
u_1&=\frac{aa^Tu_0}{a^Ta}\\
&=a\frac{a^Tu_0}{a^Ta}\\
&=\frac{a}{9}
\begin{bmatrix}
2&1&2
\end{bmatrix}
\begin{bmatrix}
9\\9\\0
\end{bmatrix}\\
&=3a\\
&=\begin{bmatrix}
6\\3\\6
\end{bmatrix}\\
\therefore
u_k&=\begin{bmatrix}
6\\3\\6
\end{bmatrix}\\
\end{align}
$$

---

假设有$t=1,y=4;t=2,y=5;t=3,y=8$，将这三个点拟合到一条过原点的直线上；

解：
$$
\begin{align}
y&=xt\\
Ax&=b\\
\begin{bmatrix}
1\\2\\3
\end{bmatrix}
x&=
\begin{bmatrix}
4\\5\\8
\end{bmatrix}
\end{align}
$$
​	可以看到该方程是无解的，需要借助投影矩阵找到最接近$b$的$p$：
$$
\begin{align}
p&=Pb=\frac{aa^Tb}{a^Ta}\\
&=\frac{1}{14}
\begin{bmatrix}
1\\2\\3
\end{bmatrix}
\begin{bmatrix}
1&2&3
\end{bmatrix}
\begin{bmatrix}
4\\5\\8
\end{bmatrix}
\\
&=\frac{19}{7}
\begin{bmatrix}
1\\2\\3
\end{bmatrix}
\end{align}
$$
​	代入可得：
$$
\begin{align}
Ax'&=p\\
x'&=\frac{19}{7}
\end{align}
$$

---

有两个向量$a_1=(1,2,3),a_2=(1,1,1)$，找到此平面上的两个正交基；

解：使用格拉姆-施密特正交化法求解：

​		将$a_1$视作一个正交向量，$a_2$投影在$a_1$上的部分为$p$，正交于$a_1$的部分为$e$；
$$
\begin{align}
e&=b-p\\
&=b-Pb\\
\because Pb&=\frac{a_1a_1^Ta_2}{a_1a_1^T}\\
&=\frac{1}{14}
\begin{bmatrix}
1\\2\\3
\end{bmatrix}
\begin{bmatrix}
1&2&3
\end{bmatrix}
\begin{bmatrix}
1\\1\\1
\end{bmatrix}\\
&=\frac{3}{7}
\begin{bmatrix}
1\\2\\3
\end{bmatrix}\\
b&=\begin{bmatrix}
1\\1\\1
\end{bmatrix}\\
\therefore
e&=
\begin{bmatrix}
1\\1\\1
\end{bmatrix}
-
\frac{3}{7}
\begin{bmatrix}
1\\2\\3
\end{bmatrix}
=
\frac{1}{7}
\begin{bmatrix}
4\\1\\-2
\end{bmatrix}
\end{align}
$$

---

有一个$4x4$的矩阵$A$，特征值分别为$\lambda_1,\lambda_2,\lambda_3,\lambda_4$，

（1）当特征值满足什么条件时，矩阵是可逆的？

（2）$A^{-1}$的行列式的值等于多少？

（3）$A+I$的迹是多少？

解：

（1）若$A$是可逆的，则$A$的列向量线性无关，$Ax=0$只有零解，$\lambda$不为0；

（2）
$$
det(A^{-1})=\frac{1}{detA}=\frac{1}{\lambda_1\lambda_2\lambda_3\lambda_4}
$$
（3）$A$的迹为$\lambda_1+\lambda_2+\lambda_3+\lambda_4$，则$A+I$的迹为$\lambda_1+\lambda_2+\lambda_3+\lambda_4+4$；

---

已知
$$
A_4=
\begin{bmatrix}
1&1&0&0\\
1&1&1&0\\
0&1&1&1\\
0&0&1&1
\end{bmatrix}
$$
求$A_n$的行列式$D_n$；

解：

​	借助代数余子式，可以看出$D_n=D_{n-1}-D_{n-2}$；

​	构造$u_{k+1}=Au_k$结构：
$$
u_k=
\begin{bmatrix}
D_n\\D_{n-1}
\end{bmatrix}
=\begin{bmatrix}
1&-1\\1&0
\end{bmatrix}
\begin{bmatrix}
D_{n-1}\\D_{n-2}
\end{bmatrix}
$$

$$
A=
\begin{bmatrix}
1&-1\\1&0
\end{bmatrix}
$$

$$
\begin{align}
(1-\lambda)(-\lambda)+1&=0\\
\lambda^2-\lambda+1&=0\\
(\lambda-\frac{1}{2})^2&=-\frac{3}{4}\\
\lambda&=\frac{1}{2} \pm \frac{\sqrt{3}}{2}
\end{align}
$$

​	特征值正好是圆上的两点，一个是60°，一个是-60°，因此$u_k$既不收敛也不发散，而是周期变化；



## Lecture 25

对称矩阵的特征值和特征向量

​	实对称矩阵具有两个性质：①实对称矩阵的特征值都是实数；

​								  			    ②实对称矩阵属于不同特征值的特征向量是相互垂直的；

​	矩阵$A$与其特征向量矩阵有以下关系：
$$
A=S\Lambda S^{-1}
$$
​	假设$A$是实对称矩阵，则其$S$可以单位化为标准正交矩阵$Q$，
$$
A=Q\Lambda Q^{-1}=Q\Lambda Q^T（谱定理）
$$

---

​	为什么实对称矩阵的特征值为实数？

​		对一般的矩阵有等式(1)：
$$
Ax=\lambda x
$$
​		假设$\lambda$为虚数，则存在其共轭的另一个特征值$\overline \lambda$，见等式(2)：
$$
A\overline x=\overline \lambda \overline x
$$
​		对等式(2)两边进行转置，并右乘$x$，
$$
\begin{align}
\overline x^T A^T=\overline \lambda \overline x^T\\
\overline x^T A=\overline \lambda \overline x^T\\
\overline x^T Ax=\overline \lambda \overline x^T x\\
\end{align}
$$
​		对等式(1)两边左乘$\overline x^T$，
$$
\overline x^TAx=\lambda \overline x^T x
$$
​		结合两式可以得到$\lambda = \overline \lambda$，因此$\lambda$为实数；

​		此外，$\overline x^T x$可以用来表示一个复数向量的长度的平方；

---

对称矩阵的实质

​	从谱定理$A=Q\Lambda Q^T$可以看出，每一个对称矩阵都是一些互相垂直的投影矩阵的组合；

---

对称矩阵的特征值的正负

​	对称矩阵，主元的符号与特征值的符号一致；

​	对称矩阵，主元的乘积等于特征值的乘积，等于行列式的值；

|            | 性质                                  |
| ---------- | ------------------------------------- |
| 实对称矩阵 | ①所有的特征值均为实数；               |
|            | ②不同的特征值对应的特征向量互相正交； |
|            | ③可以写为谱定理形式$A=Q\Lambda Q^T$； |
|            | ④主元的符号和个数与特征值一致；       |



## Lecture 26

复矩阵

​	复向量的模

​		若向量$z$的分量中存在复数，则向量$z$是一个复向量；

​		一般向量$x$的模为$\sqrt{x^Tx}$，但此方法对复向量不适用，复向量的模为$\sqrt{\overline z^Tz}$；

​		求复向量$z=\begin{bmatrix} 1\\i\end{bmatrix}$的模：
$$
\begin{align}
\begin{bmatrix}
1&-i
\end{bmatrix}
\begin{bmatrix}
1\\i
\end{bmatrix}
&=
1+(-i)i
=2\\
||z||&=\sqrt{2}
\end{align}
$$
​		将取共轭和转置结合为$H$，即$\overline z^Tz = z^Hz$；

​	复向量的点积

​		同样的，需要取共轭复数：
$$
x \cdot y=x^Hy
$$
​	复对称矩阵

​		对于复对称向量，其满足的性质不再是$A^T=A$，而是$A^H=A$；

​		如$\begin{bmatrix} 3&1+i\\1-i&3\end{bmatrix}$是一个典型的复对称矩阵；

​	复正交矩阵

​		需满足性质$Q^HQ=I$；

---

傅里叶矩阵

​	一种重要的、用途广泛的复矩阵；

​	$n$阶傅里叶矩阵：
$$
\begin{bmatrix}
1&1&1&...&1\\
1&w&w^2&...&w^{n-1}\\
1&w^2&w^4&...&w^{2(n-1)}\\
...&...&...&...&...\\
1&w^{n-1}&w^{2(n-1)}&...&w^{(n-1)^2}
\end{bmatrix}
$$
​	其中
$$
\begin{align}
w&=e^{i\frac{2 \pi}{n}}=cos(\frac{2\pi}{n})+isin(\frac{2\pi}{n})\\
w_{ij}&=w^{(i-1)(j-1)}
\end{align}
$$
​	当$n=4$时，$w=cos90^\circ+isin90^\circ=i$，对应的傅里叶矩阵$F_n$为
$$
\begin{bmatrix}
1&1&1&1\\
1&i&-1&-i\\
1&-1&1&-1\\
1&i&-1&i
\end{bmatrix}
$$
​	通过观察可见，傅里叶矩阵$F_n$的每一列之间相互正交，$\frac{1}{\sqrt{n}}F_n$的每一列之间相互标准正交；
$$
\begin{align}
F_n^{-1}F_n&=I\\

\end{align}
$$


$F_{64}$与$F_{32}$之间有什么关联（FFT-快速傅里叶变换）？

​	$w_{64}=e^{i\frac{2\pi}{64}},w_{32}=e^{i\frac{2\pi}{32}}$，因此$w_{32}=w_{64}^2$；
$$
\begin{align}
\begin{bmatrix}
F_{64}
\end{bmatrix}
=
\begin{bmatrix}
I&D\\
I&-D
\end{bmatrix}
\begin{bmatrix}
F_{32}&0\\
0&F_{32}
\end{bmatrix}
\begin{bmatrix}
P
\end{bmatrix}\\
D=
\begin{bmatrix}
1&0&0&0&0\\
0&w&0&0&0\\
0&0&w^2&0&0\\
0&0&0&...&0\\
0&0&0&0&w^{63}
\end{bmatrix}
\end{align}
$$


​	$F_{64}$乘以一个向量，需要$64^2$次运算；转换为$\begin{bmatrix} F_{32} &0\\0&F_{32}\end{bmatrix}$的形式，只需要$2(32)^2+32$算，其中所加的$32$为转换过程中的修正矩阵运算开销；

​	继续下去，可以将$F_{32}$分解为两个$F_{16}$，$(32)^2->2(16)^2+16$；

​	......

​	最终迭代得到结果，$(64)^2->log_264 \cdot \frac{64}{2}$；

​	即$n$阶傅里叶矩阵的运算复杂度可以化简为：
$$
n^2->\frac{1}{2}nlog_2n
$$
​	这就是FFT的重要作用 --- 缩减运算复杂度；



## Lecture 27

正定矩阵 - 一种特殊的对称矩阵

​	怎么判断是正定矩阵？

​	对于矩阵$A=\begin{bmatrix} a&b\\b&c\end{bmatrix}$，条件①$\lambda_1>0,\lambda_2>0$；

​													   ②$a>0,ac-b^2>0$；

​													   ③$a>0,\frac{ac-b^2}{a}>0$；（实际上与第②条相同）

​													   ④$x^TAx>0$；

​	一个矩阵，恰好达到临界条件，如$\begin{bmatrix} 2&6\\6&18 \end{bmatrix}$，其$ac-b^2=0$，被称为半正定矩阵，使用其验证条件④：
$$
\begin{align}
x^TAx&=0\\
\begin{bmatrix}
x_1&x_2
\end{bmatrix}
\begin{bmatrix}
2&6\\
6&18
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}
&=
\begin{bmatrix}
2x_1&6x_1\\
6x_2&18x_2
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}\\
&=
\begin{bmatrix}
2x_1^2+6x_1x_2\\
6x_1x_2+18x_2^2
\end{bmatrix}\\
&=2x_1^2+12x_1x_2+18x_2^2\\
&=ax^2+2bxy+cy^2
\end{align}
$$
​	设$f(x,y)=x^TAx=ax^2+2bxy+cy^2$，求该函数的极值；

​	解：回忆一下高数中求二元函数极值的方法，通过求二阶导数来算：
$$
\begin{align}
f_{xx}(x,y)&=2a=A\\
f_{xy}(x,y)&=2b=B\\
f_{yy}(x,y)&=2c=C\\
\end{align}
$$
​			当$B^2-AC<0$时有极值，$A<0$时有极大值，$A>0$时有极小值；
$$
\begin{align}
4b^2-4ac&<0\\
b^2-ac&<0\\
b^2&<ac\\
c&>18
\end{align}
$$
![image-20210529131459521](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210529131459521.png)

​	当$c=18$时恰好为临界点，
$$
\begin{align}
2x^2+12xy+18y^2&=0\\
2(x^2+6xy+9y^2)&=0\\
2(x+3y)^2+0y^2&=0 \quad <配方>
\end{align}
$$
​	即：当$c=18$时，方程可以表示为一个平方，结果肯定是$\geqslant 0$的；

​			当$c>18$时，方程可以表示为两个平方，结果肯定是$\geqslant 0$的；

​			当$c<18$时，方程可以表示为一个平方，结果有可能是$< 0$的；	

​	此时的$2$和$0$恰好就是矩阵$\begin{bmatrix} 2&6\\6&18 \end{bmatrix}$经过消元之后的主元，$2\times 1$和$2 \times 3$恰好就是消元后第一行的值；

​	因此，条件④是条件①②③的集合体，可以直接用条件④判断是否为正定矩阵；

---

判断矩阵$A$是否为正定矩阵；

解：
$$
A=
\begin{bmatrix}
2&-1&0\\
-1&2&-1\\
0&-1&2
\end{bmatrix}
->
\begin{bmatrix}
2&-1&0\\
0&\frac{3}{2}&-1\\
0&0&\frac{4}{3}
\end{bmatrix}
$$


​		矩阵$A$的主元分别为$2,\frac{3}{2},\frac{4}{3}$，因此
$$
x^TAx=2(x-\frac{1}{2}y)^2+\frac{3}{2}(y-\frac{2}{3}z)^2+\frac{4}{3}z^2
$$
​		取$x^TAx=1$处截取，得到一个椭圆球体，三个特征值分别是长轴、短轴、高，三个特征向量即为对应的坐标轴，由此$A=Q\Lambda Q^T$，将三者结合到了一起，称为主轴定理；

---

​	正定矩阵如何得到？

​		在最小二乘法中，使用$A^TAx'=A^Tb$进行计算，其中$A^TA$就是一个正定矩阵；

​		证明：
$$
x^T(A^TA)x=(Ax)^T(Ax)=||Ax||^2
$$
​			当$A$列满秩时，有$||Ax||^2>0$，此时$A^TA$为正定矩阵；



|          | 性质                                    |
| -------- | --------------------------------------- |
| 正定矩阵 | ①所有主元均为正数；                     |
|          | ②所有特征值均为正数；                   |
|          | ③所有子行列式（包括自身）的值均为正数； |
|          | ④$x^TAx>0$；                            |
|          | ⑤正定矩阵的逆矩阵也是正定矩阵；         |
|          | ⑥正定矩阵的和也是正定矩阵；             |
|          | ⑦若矩阵$A$列满秩，则$A^TA$为正定矩阵；  |



## Lecture 28

相似矩阵

​	假设$A$和$B$是两个$n$阶的方阵，$A$和$B$是相似的，这意味着存在某个可逆矩阵$M$，使得
$$
B=M^{-1}AM
$$
​	之前对于矩阵$A$与其特征向量矩阵$M$，存在关系$S^{-1}AS=\Lambda$，因此$A$和$\Lambda$是相似的，$\Lambda$是$A$最为特殊的相似矩阵，除了$\Lambda$之外$A$还有很多其他的相似矩阵；

​	相似的矩阵具有相同的特征值；

​		证明：
$$
\begin{align}
Ax&=\lambda x\\
AMM^{-1}x&=\lambda x\\
M^{-1}AMM^{-1}x&=M^{-1}\lambda x\\
BM^{-1}x&=\lambda M^{-1}x\\
B(M^{-1}x)&=\lambda (M^{-1}x)
\end{align}
$$
​		可以看到$B$和$A$的特征值相同$\lambda_B=\lambda_A$，特征向量$x_B=M^{-1}x_A$；

---

​	假设矩阵$A$具有相同的两个特征值，

​	（1）$A=\begin{bmatrix} 4&0\\0&4\end{bmatrix}$
$$
\begin{align}
M^{-1}AM&=B\\
M^{-1}4IM&=B\\
4M^{-1}IM&=B\\
4I&=B\\
A&=B
\end{align}
$$
​			对于这一类的矩阵（即$cI$），其相似矩阵即为其自身；
$$
\begin{align}
Ax&=\lambda x\\
4Ix&=4x\\
x&=x
\end{align}
$$
​			任何$n$维的非零向量都是这一类矩阵的特征向量；

​	（2）$A=\begin{bmatrix} 4&1\\0&4 \end{bmatrix}$ (若尔当标准型)

​			其与$trace=8,det=16$的矩阵相似；
$$
\begin{align}
Ax&=\lambda x\\
\begin{bmatrix}
4&1\\0&4
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}
&=
\begin{bmatrix}
4x_1\\4x_2
\end{bmatrix}\\
\begin{bmatrix}
4x_1+x_2\\4x_2
\end{bmatrix}
&=
\begin{bmatrix}
4x_1\\4x_2
\end{bmatrix}\\
x&=c
\begin{bmatrix}
1\\0
\end{bmatrix}
\end{align}
$$
​			该类矩阵只有一个线性无关特征向量（猜测）；

---

​	对于矩阵，
$$
\begin{bmatrix}
0&1&0&0\\
0&0&1&0\\
0&0&0&0\\
0&0&0&0
\end{bmatrix}
$$
​	其特征值$\lambda_1=\lambda_2=\lambda_3=\lambda_4=0$ ，$Ax=0$，则特征向量$x$在矩阵$A$的零空间内，零空间的维数=秩=4-2=2，因此有两个特征向量；

​	对于另一个矩阵，
$$
\begin{bmatrix}
0&1&0&0\\
0&0&0&0\\
0&0&0&1\\
0&0&0&0
\end{bmatrix}
$$
​	其特征值也全是0，特征向量也有两个，乍看之下似乎是上一个矩阵的相似矩阵，但其实不是；
$$
\begin{bmatrix}
0&1&0&|&0\\
0&0&1&|&0\\
0&0&0&|&0\\
-&-&-&-&-\\
0&0&0&|&0
\end{bmatrix}
\quad
\begin{bmatrix}
0&1&|&0&0\\
0&0&|&0&0\\
-&-&-&-&-\\
0&0&|&0&1\\
0&0&|&0&0
\end{bmatrix}
$$
​	第一个矩阵和第二个矩阵的分块不同，这些分块叫做“若尔当块”；

​	若尔当块

​		使用$J_i$表示$i$阶的若尔当块，其只有一个重复的特征值，只有一个特征向量，且对角线上方的一斜列均为1；
$$
J_i=
\begin{bmatrix}
\lambda_i&1&0&...&0\\
0&\lambda_i&1&...&0\\
0&0&\lambda_i&...&0\\
0&0&0&...&1\\
0&0&0&0&\lambda_i
\end{bmatrix}
$$
​	若尔当阵

​		若尔当阵$J$ 为由若尔当块$J_i$组成的矩阵，特征向量的个数为若尔当块的个数，每一个若尔当块对应一个特征向量；
$$
J=
\begin{bmatrix}
J_1& & &  \\
 &J_2& & \\
 & &...& \\
  & & &J_d
\end{bmatrix}
$$
​	若尔当定理

​		每个方阵$A$都相似于一个若尔当矩阵$J$；

​		如果$A$可对角化，对应的若尔当阵即为$\Lambda$；

​		

## Lecture 29

奇异值分解SVD

​	任意一个矩阵$A$可以被分解为下面这种形式：
$$
A=U\Sigma V^T
$$
​	其中，$U$和$V$是两个不同的正交矩阵，$\Sigma$是一个对角矩阵；

​	特殊形式

​		如果$A$是一个正定矩阵，则$A=Q\Lambda Q^T$；

​		如果$A$是一个可对角化的矩阵，则$A=S\Lambda S^{-1}$；(此处$S$不正交，不是奇异值分解的形式)

​	推导

​		倘若在行空间内找一个典型向量$v$，然后使用矩阵$A$变换到列空间的标准向量$u$，可得$Av=\sigma u$，其中$\sigma$为缩放因子，表示倍数关系；

​		在行空间内找到一组正交基，但是这组正交基经过变换后，在列空间内不一定正交，若要保持正交性，需要在行空间内找到一组特殊的正交基；

​		假设此时找到了特殊的一组正交基$\begin{bmatrix}v_1&v_2&...&v_r \end{bmatrix}$（$r$为行空间的维数），
$$
\begin{align}
Av&=\sigma u\\
A
\begin{bmatrix}
v_1&v_2&...&v_r
\end{bmatrix}
&=
\begin{bmatrix}
u_1&u_2&...&u_r
\end{bmatrix}
\begin{bmatrix}
\sigma_1&&&\\
&\sigma_2&&\\
&&...&\\
&&&\sigma_r
\end{bmatrix}\\
AV&=U\Sigma\\
AVV^T&=U\Sigma V^T\\
A&=U\Sigma V^T
\end{align}
$$

​		若此时将$U$化为$V$，
$$
\begin{align}
A&=U\Sigma V^T\\
A^TA&=(U\Sigma V^T)^TU\Sigma V^T\\
&=V\Sigma ^TU^TU\Sigma V^T\\
&=V\Sigma^T\Sigma V^T\\
&=V
\begin{bmatrix}
\sigma_1^2&&&\\
&\sigma_2^2&&\\
&&...&\\
&&&\sigma_r^2
\end{bmatrix}
V^T
\end{align}
$$
​		可以看到，$V$是$A^TA$的特征向量矩阵；	

​	若此时将$V$化为$U$，
$$
\begin{align}
A&=U\Sigma V^T\\
AA^T&=U\Sigma V^T(U\Sigma V^T)^T\\
&=U\Sigma V^TV\Sigma^TU^T\\
&=U\Sigma\Sigma^TU^T\\
&=U
\begin{bmatrix}
\sigma_1^2&&&\\
&\sigma_2^2&&\\
&&...&\\
&&&\sigma_r^2
\end{bmatrix}
U^T
\end{align}
$$
​		可以看到，$U$是$AA^T$的特征向量矩阵；

​	例题：求矩阵$A=\begin{bmatrix} 4&4\\-3&3\end{bmatrix}$的奇异值分解；

​	解：计算$A^TA$的特征向量矩阵$V$：
$$
\begin{align}
A^TA&=
\begin{bmatrix}
4&-3\\4&3
\end{bmatrix}
\begin{bmatrix}
4&4\\-3&3
\end{bmatrix}\\
&=
\begin{bmatrix}
25&7\\7&25
\end{bmatrix}\\
(25-\lambda)^2-49&=0\\
25-\lambda&=\pm7\\
\lambda_1&=32\\
\lambda_2&=18
\end{align}
$$

$$
\begin{align}
\begin{bmatrix}
-7&7\\7&-7
\end{bmatrix}
->
v_1&=
\frac{1}{\sqrt2}
\begin{bmatrix}
1\\1
\end{bmatrix}\\
\begin{bmatrix}
7&7\\7&7
\end{bmatrix}
->
v_2&=
\frac{1}{\sqrt2}
\begin{bmatrix}
1\\-1
\end{bmatrix}\\
V&=
\frac{1}{\sqrt2}
\begin{bmatrix}
1&1\\1&-1
\end{bmatrix}
\end{align}
$$

​			计算$AA^T$的特征向量矩阵$U$：
$$
\begin{align}
AA^T&=
\begin{bmatrix}
4&4\\-3&3
\end{bmatrix}
\begin{bmatrix}
4&-3\\4&3
\end{bmatrix}\\
&=
\begin{bmatrix}
32&0\\0&18
\end{bmatrix}\\
(32-\lambda)(18-\lambda)&=0\\
\lambda_1&=32\\
\lambda_2&=18
\end{align}
$$

$$
\begin{align}
\begin{bmatrix}
0&0\\0&-14
\end{bmatrix}
->
u_1&=
\begin{bmatrix}
1\\0
\end{bmatrix}\\
\begin{bmatrix}
14&0\\0&0
\end{bmatrix}
->
u_2&=
\begin{bmatrix}
0\\1
\end{bmatrix}\\
U&=
\begin{bmatrix}
1&0\\0&1
\end{bmatrix}
\end{align}
$$

​			**注意：$AA^T$和$A^TA$的特征值相同，因此次序要一致**

​			计算特征值对角矩阵$\Sigma$：
$$
\Sigma=
\begin{bmatrix}
\sqrt{32}&0\\0&\sqrt{18}
\end{bmatrix}
$$
​			矩阵$A$奇异值分解为：
$$
\begin{align}
A&=U\Sigma V^T\\
&=
\frac{1}{\sqrt2}
\begin{bmatrix}
\sqrt{32}&0\\0&\sqrt{18}
\end{bmatrix}
\begin{bmatrix}
1&1\\1&-1
\end{bmatrix}\\
&=
\begin{bmatrix}
4&4\\3&-3
\end{bmatrix}
\quad ?
\end{align}
$$
​			此时得到的结果与期望值不同，原因在于，没有给$v_i$和$u_i$建立对应关系；

​			在求特征向量时，比如对于$\begin{bmatrix} 1\\1\end{bmatrix}$，我们可以取$\begin{bmatrix} 1\\-1\end{bmatrix}$，也可以取$\begin{bmatrix} -1\\1\end{bmatrix}$，因此需要使用$Av=\sigma u$得到正确的特征向量；

​			例如本例题中，$u_1=\begin{bmatrix} 1\\0 \end{bmatrix}$，$u_2=\begin{bmatrix} 0\\1 \end{bmatrix}$，其对应的$v$为：
$$
\begin{align}
\begin{bmatrix}
4&4\\-3&3
\end{bmatrix}
v_1
&=
4\sqrt2
\begin{bmatrix}
1\\0
\end{bmatrix}\\
v_1&=
\frac{1}{\sqrt2}
\begin{bmatrix}
1\\1
\end{bmatrix}\\
\begin{bmatrix}
4&4\\-3&3
\end{bmatrix}
v_2
&=
3\sqrt2
\begin{bmatrix}
0\\1
\end{bmatrix}\\
v_2&=
\frac{1}{\sqrt2}
\begin{bmatrix}
-1\\1
\end{bmatrix}\\
V&=
\frac{1}{\sqrt2}
\begin{bmatrix}
1&-1\\1&1
\end{bmatrix}
\end{align}
$$
​			所以正确的奇异值分解为：
$$
A=
\frac{1}{\sqrt2}
\begin{bmatrix}
\sqrt{32}&0\\0&\sqrt{18}
\end{bmatrix}
\begin{bmatrix}
1&1\\-1&1
\end{bmatrix}\\
$$


---

​		例题：求$A=\begin{bmatrix} 4&3\\8&6\end{bmatrix}$的SVD分解；

​		解：$A$的秩为1，其列空间和行空间都是一维的，

​				行空间为$c\begin{bmatrix} 4\\3\end{bmatrix}$，单位化为$\frac{1}{5}\begin{bmatrix}4\\3 \end{bmatrix}$；（对应非0的$\sigma$）

​					与其正交的零空间的单位向量为$\begin{bmatrix} \frac{3}{5}\\ -\frac{4}{5} \end{bmatrix}$；（对应等于0的$\sigma$）

​				列空间为$c\begin{bmatrix}1\\2 \end{bmatrix}$，单位化为$\frac{1}{\sqrt5}\begin{bmatrix}1\\2 \end{bmatrix}$；（对应非0的$\sigma$）

​					与其正交的左零空间的单位向量为$\frac{1}{\sqrt5}\begin{bmatrix} 2\\ -1\end{bmatrix}$；（对应等于0的$\sigma$）



​				求$\Sigma$：
$$
\begin{align}
A^TA&=
\begin{bmatrix}
4&8\\3&6
\end{bmatrix}
\begin{bmatrix}
4&3\\8&6
\end{bmatrix}\\
&=
\begin{bmatrix}
80&60\\
60&45
\end{bmatrix}\\

\end{align}
$$
​				观察可见，该矩阵的秩为1，因此其中一个$\lambda=0$，另一个$\lambda=trace-0=125$；

​				则$\Sigma=\begin{bmatrix} 5\sqrt5&0\\0&0\end{bmatrix}$；

​				矩阵$A$的奇异值分解为：
$$
\begin{align}
A&=U\Sigma V^T\\
&=
\frac{1}{\sqrt5}
\begin{bmatrix}
1&2\\2&-1
\end{bmatrix}
\begin{bmatrix}
5\sqrt5&0\\0&0
\end{bmatrix}
\frac{1}{5}
\begin{bmatrix}
4&3\\3&-4
\end{bmatrix}
\end{align}
$$


## lecture 30

线性变换

​	线性变换需要遵守的规则：①$T(v+w)=T(v)+T(w)$；

​												   ②$T(cv)=cT(v)$；

​	如何判断一个操作是否是线性变换？

​		(1) 看是否满足规则①②；

​		(2) 重点观察$T(0)$是否满足规则；

---

​	例1：将向量$v$沿着某一方向平移$v_0$，得到新向量$T(v)$，该操作是线性变换吗？

​		解：将向量$v$的2倍平移后得到的向量显示不是$2T(v)$，因此该操作不是线性变换；

​	例2：求长度操作$T(v)=||v||$是线性变换吗？

​		解：该操作不满足$T(-v)=-T(v)$，因此不是线性变换；

​	例3：对于平面内的任意向量，逆时针旋转45度的操作是线性变换吗？

​		解：是的；

---

​	每一个线性变换可以使用一个对应的矩阵来表示；

​	一个向量可以由其基向量的组合表示，因此，只要确定了线性变换对基向量的影响，就可以知道线性变换对整个空间的影响；
$$
\begin{align}
v&=c_1v_1+c_2v_2+...+c_nv_n\\
T(v)&=c_1T(v_1)+c_2T(v_2)+...+c_nT(v_n)
\end{align}
$$
​	例：一个线性变换将$x-y$平面的左边投影在一条直线上，求对应的矩阵；

![image-20210531022841664](C:\Users\dzw\AppData\Roaming\Typora\typora-user-images\image-20210531022841664.png)

​	解：原本的基向量为$x$轴和$y$轴，重新选取基向量，一个在直线上，另一个在直线的正交线上；

​			(1) 分析线性变换对基向量的影响
$$
T(v_1)=v_1,T(v_2)=0
$$

​			(2) 写为矩阵形式
$$
\begin{bmatrix}
1&0\\0&0
\end{bmatrix}
\begin{bmatrix}
c_1\\c_2
\end{bmatrix}
=
\begin{bmatrix}
c_1\\0
\end{bmatrix}
$$
​			如果选择$x,y$轴为坐标，矩阵即为投影矩阵$P$：
$$
P=
\frac{aa^T}{a^Ta}
$$


​	求线性变换矩阵的方式

​		①确定输入变量$R^n$的基向量$v_1,v_2,...,v_n$与输出变量$R^m$的基向量$w_1,w_2,...w_m$；

​		②
$$
T(v_1)=a_{11}w_1+a_{21}w_2+...+a_{m1}w_m\\
T(v_2)=a_{12}w_1+a_{22}w_2+...+a_{m2}w_m\\
...
$$

---

​	例题：输入为$c_1+c_2x+c_3x^2$，输出为$c_2+2c_3x$，求$T=\frac{d}{dx}$操作对应的矩阵；

​	解：输入基为$\begin{bmatrix} 1\\x\\x^2\end{bmatrix}$，输出基为$\begin{bmatrix} 1\\x\end{bmatrix}$，因此
$$
A
\begin{align}
\begin{bmatrix}
c_1\\c_2\\c_3
\end{bmatrix}
&=\begin{bmatrix}
c_2\\2c_3
\end{bmatrix}\\
A&=
\begin{bmatrix}
0&1&0\\
0&0&2
\end{bmatrix}
\end{align}
$$

## Lecture 31

例1、求解方程
$$
\frac{du}{dt}=Au=
\begin{bmatrix}
0&-1&0\\
1&0&-1\\
0&1&0
\end{bmatrix}
u
$$
​	解：该矩阵表示的微分方程组为
$$
\frac{du_1}{dt}=0u_1-u_2+0u_3\\
\frac{du_2}{dt}=u_1+0u_2-u_3\\
\frac{du_3}{dt}=0u_1+u_2+0u_3\\
$$
​	对于微分方程，通解为$u_t=c_1e^{\lambda_1t}x_1+c_2e^{\lambda_2t}x_2+c_3e^{\lambda_3t}x_3$，因此需要求解特征值与特征向量；

​	由于$A$的列向量线性相关，因此有一个特征值为0；
$$
\begin{align}
\left|
\begin{matrix}
-\lambda&-1&0\\
1&-\lambda&-1\\
0&1&-\lambda
\end{matrix}
\right|
&=
0\\
-\lambda^3-2\lambda&=0\\
\lambda(\lambda^2+2)&=0\\
\lambda_1&=0\\
\lambda_2&=+\sqrt2i\\
\lambda_3&=-\sqrt2i\\
\end{align}
$$
形如$A$这样的矩阵称为反对称矩阵，其具有性质$A^T=-A$；

怎样的矩阵的特征向量是正交的呢？

​	需要满足性质$A^TA=AA^T$，满足这一条件的矩阵有对称矩阵、反对称矩阵、正交矩阵；

---

例2、已知$\lambda_1=0,\lambda_2=c,\lambda_3=2$，且特征向量
$$
x_1=
\begin{bmatrix}
1\\1\\1
\end{bmatrix}
x_2=
\begin{bmatrix}
1\\-1\\0
\end{bmatrix}
x_3=
\begin{bmatrix}
1\\1\\-2
\end{bmatrix}
$$
​		(1) 当$c$满足什么条件时，矩阵可以对角化？

​		解：矩阵$A$可对角化的条件是 --- 其特征向量矩阵$S$可逆，即列向量线性无关；

​				本题中三个特征向量线性无关且互相正交，因此$c$可以取任意值；

​		(2) 当$c$满足什么条件时，矩阵对称？

​		解：只要$c$是实数就可以；

​		(3) 当$c$满足什么条件时，矩阵是正定矩阵？

​		解：有一个特征值是0，因此无论$c$取什么值都不会是正定矩阵；

​		(4) 当$c$满足什么条件时，矩阵是马尔可夫矩阵？

​		解：马尔可夫矩阵的特征值要求一个为1，其他的小于1（才能达到稳态），

​				由于有一个特征值是2大于1，因此无论$c$取什么值都不会是马尔可夫矩阵；

​		(5) $\frac{1}{2}A$可能是投影矩阵吗？

​		解：$\frac{1}{2}A$的特征值为$0,\frac{c}{2}，1$，投影矩阵要求特征值为0或1，因此可能是投影矩阵；



|              | 特征值或特征向量要求                   |
| ------------ | -------------------------------------- |
| 可对角化矩阵 | 特征向量矩阵可逆                       |
| 对称矩阵     | 特征值均为实数                         |
| 正定矩阵     | 特征值均为正数                         |
| 马尔可夫矩阵 | 一个特征值为1，其他特征值小于1         |
| 投影矩阵     | 特征值为0或1                           |
| 正交矩阵     | 特征值的绝对值为1，行列式的绝对值也为1 |

---

例3、矩阵$A$对称且正交，那么

​	(1) 该矩阵一定是正定矩阵吗？

​		不是，特征值若为-1则不是正定矩阵；

​	(2) 它的特征值一定不重复吗？

​		不是，特征值只有1或-1，如果矩阵的阶大于2，则肯定会有重复的特征值；

​	(3) 它可以被对角化吗？

​		是的，任何对称矩阵、任何正交矩阵都可以对角化；

​	(4) 它是非奇异矩阵吗？

​		是的，正交矩阵的行列式的绝对值为1，因此其必定非奇异；

​	(5) 证明$\frac{A+I}{2}$是投影矩阵

​		① 投影矩阵是对称的； --->成立

​		②投影矩阵满足$P^2=P$；
$$
\begin{align}
&\because A=A^T=A^{-1}\\
&\therefore A^2=I
\end{align}
$$

$$
\begin{align}
(\frac{A+I}{2})^2&=\frac{A+I}{2}\\
\frac{1}{4}(A^2+2AI+I^2)&=\frac{1}{2}(A+I)\\
\frac{1}{4}(2A+2I)&=\frac{1}{2}(A+I)\\
\end{align}
$$

​			--->成立

​		③投影矩阵的特征值为0或1；

​			$A$的特征值为$\pm 1$，则$\frac{A+I}{2}$的特征值为1或0 --->成立



## Lecture 32

左逆、右逆和伪逆

​	对于一个$r$阶的$m\times n$矩阵，

​		①什么情况下会有一个双边逆使得$A^{-1}A=AA^{-1}=I$？

​			方阵 + 满秩，即$r=m=n$；

​		②列满秩，即$r=n$时，$A^TA$为$n$阶的可逆方阵，此时有左逆$(A^TA)^{-1}A^T$；
$$
\begin{align}
(A^TA)^{-1}(A^TA)&=I\\
((A^TA)^{-1}A^T)A&=I
\end{align}
$$
​		③行满秩，即$r=m$时，$AA^T$为$m$阶的可逆方阵，此时有右逆$A^T(AA^T)^{-1}$；
$$
\begin{align}
(AA^T)(AA^T)^{-1}&=I\\
A(A^T(AA^T)^{-1})&=I
\end{align}
$$
​			

​			尝试将左逆和右逆乘在另一侧会发生什么：
$$
AA^{-1}_{left}=P_A\\
A^{-1}_{right}A=P_{A^T}
$$
​			得到了投影矩阵，

​				$P_A$为对列空间的投影，其对于列空间内的向量等同于$I$；

​				$P_{A^T}$为对行空间的投影，其对于行空间内的向量等同于$I$；

​		④对于$r<m,r<n$的情况，

​			忽略零空间与左零空间，只考虑行空间与列空间的情况；

​			行空间的$x$乘以矩阵$A$后变成了列空间的$Ax$，
$$
Ax=A\quad x
$$
​			伪逆即为该过程的逆过程，即列空间的$Ax$乘以伪逆后还原为行空间的$x$，
$$
x=A^+\quad Ax
$$
​			如何求出伪逆$A^+$？

​				在SVD分解中，$A=U\Sigma V^T$，其中
$$
\begin{align}
\Sigma&=
\begin{bmatrix}
\sigma_1&&&&\\
&\sigma_2&&&\\
&&...&&\\
&&&\sigma_r&\\
&&&&0
\end{bmatrix}(n\times m)\\
\Sigma^+&=
\begin{bmatrix}
1/\sigma_1&&&&\\
&1/\sigma_2&&&\\
&&...&&\\
&&&1/\sigma_r&\\
&&&&0
\end{bmatrix}(m\times n)
\end{align}
$$

$$
\begin{align}
\Sigma \Sigma^+&=
\begin{bmatrix}
1&&\\
&...&\\
&&0
\end{bmatrix}(n\times n)\\
\Sigma^+ \Sigma&=
\begin{bmatrix}
1&&\\
&...&\\
&&0
\end{bmatrix}(m\times m)
\end{align}
$$

​				$\Sigma\Sigma^+$为到列空间的投影，$\Sigma^+\Sigma$为到行空间的投影；
$$
A^+=V\Sigma^+U
$$


|           | 四个子空间                                         | 逆                   |
| --------- | -------------------------------------------------- | -------------------- |
| $r=m=n$   | 零空间和左零空间都只有零向量，四个子空间只存在两个 | 双边逆$A^{-1}$       |
| $r=n<m$   | 零空间只有零向量                                   | 左逆$(A^TA)^{-1}A^T$ |
| $r=m<n$   | 左零空间只有零向量                                 | 右逆$A^T(AA^T)^{-1}$ |
| $r<m,r<n$ | 四个子空间都存在                                   | 伪逆                 |



## Lecture 33

例1、已知$Ax=\begin{bmatrix} 1\\0\\0\end{bmatrix}$无解，$Ax=\begin{bmatrix} 0\\1\\0\end{bmatrix}$有且仅有一个解，

​		(1) 求矩阵$A$的$m,n,r$；

​		解：从$b$为$3\times1$向量可以看出，矩阵$A$的行数$m=3$；

​				当$A$行满秩时，$Ax=b$必定有解，因此此处$r<m$即$r<3$；

​				当$A$列满秩时，$Ax=b$只有唯一解（零空间内的通解为零向量），因此此处$r=n$；

​		(2) 判断题：

​			① $detA^TA=detAA^T$；

​					$A^TA$可逆而$AA^T$不可逆，因此两者的行列式不可能相等；

​			② $A^TA$可逆；

​					$A^TA$为$n$阶方阵，当$r=n$时可逆；

​					$r(A^TA)=r(AA^T)=r(A)=n$，因此$A^TA$可逆；

​			③ $AA^T$是正定矩阵；

​					$AA^T$为$3\times3$矩阵，但$r=n<3$，因此不是正定矩阵；

​		(3) 求解$A^Ty=c$对任意$c$的解；

​		解：$A^T$为行满秩矩阵，因此$A^Ty=c$一定有解，其解的形式为特解 + 任意解；

---

例2、已知$A=\begin{bmatrix} v_1&v_2&v_3\end{bmatrix}$，

​	(1) 若$Ax=v_1-v_2+v_3$，求解$x$；

​	解：
$$
\begin{align}
Ax&=v_1-v_2+v_3\\
\begin{bmatrix}
v_1&v_2&v_3
\end{bmatrix}
x&=
\begin{bmatrix}
v_1&v_2&v_3
\end{bmatrix}
\begin{bmatrix}
1\\-1\\1
\end{bmatrix}\\
x&=
\begin{bmatrix}
1\\-1\\1
\end{bmatrix}
\end{align}
$$
​	(2) 假设$v_1-v_2+v_3=0$，则解是否唯一？

​	解：解一定存在的条件是行满秩，解唯一的条件是列满秩，可以看出列向量线性相关，因此解不唯一；

​	(3) 假设$v_1,v_2,v_3$正交，则$v_1v_2$平面上哪一点最接近$v_3$？

​	解：三者相交于零点，因此零点最接近$v_3$；

---

例3、已知一个马尔可夫矩阵，

​	(1) 求特征值；
$$
A=
\begin{bmatrix}
0.2&0.4&0.3\\
0.4&0.2&0.3\\
0.4&0.4&0.4
\end{bmatrix}
$$
​	解：观察可以发现，行向量线性相关，因此其中一个特征值为1；

​			又因为是马尔可夫矩阵，因此第二个特征值为1；

​			第三个特征值为$0.8-1=-0.2$；

​			因此三个特征值分别为1，0，-0.2；

​	(2) 已知$u_0=\begin{bmatrix} 0\\10\\0\end{bmatrix}$，求稳态；

​	解：
$$
\begin{align}
u_k&=A^ku_0\\
&=c_1\lambda_1^kx_1+c_2\lambda_2^kx_2+c_3\lambda_3^kx_3
\end{align}
$$
​	将$\lambda_1=0,\lambda_2=1,\lambda_3=-0.2$代入，得$u_k=c_2x_2$；

​	代入$\lambda_2=1$，计算$x_2$：
$$
\begin{align}
\begin{bmatrix}
-0.8&0.4&0.3\\
0.4&-0.8&0.3\\
0.4&0.4&-0.6
\end{bmatrix}
->x_2=
\begin{bmatrix}
3\\3\\4
\end{bmatrix}
\end{align}
$$
​	由于马尔可夫矩阵的总和不会变，$3+3+4=0+10+0$，因此$c_2=1$，
$$
u_k=\begin{bmatrix}
3\\3\\4
\end{bmatrix}
$$

---

例4、① 求投影到直线$a=\begin{bmatrix} 4\\-3\end{bmatrix}$上的矩阵；

​		解：
$$
\begin{align}
P&=\frac{aa^T}{a^Ta}\\
&=
\begin{bmatrix}
4\\-3
\end{bmatrix}
\begin{bmatrix}
4&-3
\end{bmatrix}
/
\begin{bmatrix}
4&-3
\end{bmatrix}
\begin{bmatrix}
4\\-3
\end{bmatrix}\\
&=\frac{1}{25}
\begin{bmatrix}
16&-12\\
-12&9
\end{bmatrix}
\end{align}
$$


​		② 矩阵有特征值$0,3$和特征向量$\begin{bmatrix} 1\\2\end{bmatrix},\begin{bmatrix} 2\\1\end{bmatrix}$，求矩阵$A$；

​		解：
$$
A=S\Lambda S^{-1}
$$
​		③ 矩阵$A$是一个实矩阵，且对于任意矩阵$B$，$A$不能写为$B^TB$，求$A$；

​		解：$B^TB$是方阵且对称，因此$A$可以是长方形矩阵或非对称方阵；

​		④ 矩阵$A$有正交的特征向量，但矩阵$A$不对称，求$A$；

​		解：实对称矩阵的特征向量一定正交，但特征向量正交的矩阵不一定是实对称矩阵；

---

例5、已知
$$
\begin{bmatrix}
1&0\\1&1\\1&2
\end{bmatrix}
\begin{bmatrix}
c\\d
\end{bmatrix}
=
\begin{bmatrix}
3\\4\\1
\end{bmatrix},
\begin{bmatrix}
c'\\d'
\end{bmatrix}
=
\begin{bmatrix}
\frac{11}{3}\\-1
\end{bmatrix}
$$
​			(1) 求投影$p$；

​			解：
$$
\begin{align}
p&=Pb\\
&=\frac{AA^Tb}{A^TA}\\
&=Ax'\\
&=
\begin{bmatrix}
\frac{11}{3}&0\\
\frac{11}{3}&-1\\
\frac{11}{3}&-2\\
\end{bmatrix}
\end{align}
$$
​			(2) 找出另一个非0的$b$，使得最小二乘法的结果为0；

​			解：最小二乘法的结果为0，即$x'=0,p=Ax'=0$，
$$
\begin{align}
p&=Pb=0\\
\frac{AA^Tb}{A^TA}&=0\\
AA^Tb&=0\\
A^Tb&=0\\
\begin{bmatrix}
1&1&1\\
0&1&2
\end{bmatrix}
b&=0\\
b&=c
\begin{bmatrix}
1\\-2\\1
\end{bmatrix}
\end{align}
$$

