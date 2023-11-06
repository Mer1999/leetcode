# leetcode
力扣刷题随想小悟

## [2136. 全部开花的最早一天](https://leetcode.cn/problems/earliest-possible-day-of-full-bloom/)

iota函数，给数组赋值
```C++
vector<int>id(n);
iota(id.begin(), id.end(), 0); // iota数组赋初值，从0到n-1
```

## [122. 买卖股票的最佳时机 II](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/)

原本思路想复杂了，想先找极小值点再找极大值点如此循环，每次找到极大值点就进行一次和极小值的求差值，如此还要判断最后的边界点是否需要求差。

实际官解贪心思路只需要判断相邻两天是否后一天比前一天高，如此累计，即相当于把原本思路的极大值减极小值拆分到这之中的若干天，愚蠢愚蠢。

## [137. 只出现一次的数字 II](https://leetcode.cn/problems/single-number-ii/)

一看每个数字的范围是int范围，便知要用位运算。

官解方法二：取余的思想，比较经典，但总是想不起来。除去只出现一次那个数字，其余的都是出现0次或3次，因此每位相加的和不是0就是3。而加上那个独特的数字则会导致某些位模3余1，也就能判断出独特数字的哪些位是1了。

官解方法三：数字电路，在拿到题的时候我第一反应就是遍历每个数去做位运算，但因为出现三次而不是两次导致1-0-1会回到原点。不过还是忘了可以用两位去存储多达4种情况，这样00-01-10-00实现一个循环，最终独特数字为1的位就会是01。

## [2652. 倍数求和](https://leetcode.cn/problems/sum-multiples/)

**容斥原理：**

三个的情况：|A∪B∪C|=|A|+|B|+|C|-|A∩B|-|A∩C|-|B∩C|+|A∩B∩C|

## [2558. 从数量最多的堆取走礼物](https://leetcode.cn/problems/take-gifts-from-the-richest-pile/)

STL最大堆的用法：

赋初值：```priority_queue<T>q(gifts.begin(), gifts.end());``` gifts是个vector<int>

类似于栈和队列,
```q.pop() q.top() q.push()```顾名思义，并且```top()```依旧是只返回值不出队

## [318. 最大单词长度乘积](https://leetcode.cn/problems/maximum-product-of-word-lengths/)

想到了位运算，没想到官解还真是。不过官解还有位运算优化，因为有些单词字母组成相同，则只需要保存相同组成最长的那个，使用哈希表储存。每个单词形成掩码后去哈希表里找是否已经存在，存在则留下较长的那个，不存在则添加。最后对哈希表内两两比较得到最大长度乘积。