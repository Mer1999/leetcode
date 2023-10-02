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