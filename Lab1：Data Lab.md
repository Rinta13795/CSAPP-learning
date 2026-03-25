
1.终端命令：
cd datalab-handout
make btest 编译
./dlc bits.c 检查语法
./btest 运行

套路：
- ✅ 判等：`!(a ^ b)`
- ✅ 掩码构造：`~(!!x) + 1`
- ✅ 条件选择：`(mask & a) | (~mask & b)`
- ✅ 条件翻转：`x ^ sign`
- ✅ 二分查找最高位


1.
```
```
```c
/*

* bitXo
r - x^y using only ~ and &

* Example: bitXor(4, 5) = 1

* Legal ops: ~ &

* Max ops: 14

* Rating: 1

*/

int bitXor(int x, int y) {

return ~((~((~x)&y))&(~(x&(~y))));

}

```
一：

德摩根定律：

~(x | y) = ~x & ~y

~(x & y) = ~x | ~y

变式：


x | y = ~(~x & ~y)

x & y = ~(~x | ~y)

(用真值表证明，记住结论就行)

二：

XOR 的定义：两个位不同时输出1，相同时输出0。

两种"不同"的情况：(就是讨论输出为真的情况，不满足则输出为假)

x=0, y=1 → ~x & y

x=1, y=0 → x & ~y

——>(~x & y)|(x & ~y)



```c
2.
/*

* tmin - return minimum two's complement integer (返回最小补码数)

* Legal ops: ! ~ & ^ | + << >>

* Max ops: 4

* Rating: 1

*/

int tmin(void) {

return 1<<31;

}
```
把谁移到目标位置，谁就在左边。 想要1到第31位，就是 1 << 31



```c

3.

/*

* isTmax - returns 1 if x is the maximum, two's complement number,

* and 0 otherwise

* Legal ops: ! ~ & ^ | +

* Max ops: 10

* Rating: 1

*/

int isTmax(int x) {

return (!((~(x+1))^x))&(!!(x+1));//这个&理解成且的意识就可以，不要听Claude说的那些公式

}//
```
```
用

TMax+1=TMin

(a^a)=0

!(a^a)=1

! 是逻辑非：

!0 = 1

!任何非零值 = 

2.

~(x+1) == x 这个性质，满足的只有 Tmax 和 -1 两个值

~(x+1) == x 等价于!(~(x+1)^x)

