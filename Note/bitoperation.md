- - -
### 数据内存分布 ###
- 266 00001010 00000001 00000000 00000000</br>

- - -
### 位运算 ###
- 检测数字是否为2的次幂
	>x = 1000<br>
	>x - 1= 0111<br>
	>x & (x - 1)= 0000<br>
	>2的次幂 二进制中只有某一位为1<br>
- 统计32位二进制中1的个数
	>不断使用x&(x-1)<br>
	>示例：<br>
	>int x = 15;<br>
    >int i = 0;<br>
    >while(x!=0)<br>
    >{<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;x = x&(x-1);<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;i++;<br>
    >}<br>
- 将A转换为B需要改变的bit位数
	>移位并异或
	>示例：<br>
	>int a = 0;<br>
    >int b = 15;<br>
    >int n = 0;<br>
    >while(a||b)<br>
    >{<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;if(a^b)n++;<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;a>>=1;<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;b>>=1;<br>
    >}<br>
- 数组中只有一个数出现一次其他的出现两次，找出该数字
    >将数组中所有的数字异或，结果为只出现一次的数字<br>
    >示例：<br>
    >int number = 0;<br>
    >int arg[5] = {11,22,44,22,11};<br>
    >int i =4;<br>
    >number = arg[4];<br>
    >while(i){number^=arg[i-1];i--;}<br>
- 数组中有两个数字出现一次，其他数字均出现两次
    >将数组中所有数字异或，异或结果为数组中只出现一次的两个数字，在异或结果中任选某一位二进制位位1的位置，将数组中与异或结果位置相同的做异或可求出其中一个出现一次的，在与第一次异或结果做异或可求出另一个出现一次的数字
- 右移操作 A>>B A>>>B
    >右移操作分为算数右移和逻辑右移 C/C++ 中不进行区分<br>
    >算数右移：左边补符号位<br>
    >逻辑右移：左边补0<br>
    >示例：<br>
    >A = 1111111111······01<br>
    >B = 2<br>
    >A>>B = 1111111111······00<br>
    >A>>>B = 0011111111······00<br>
- 按位非 ~
    >按位去反<br>
- 位运算求A+B
    >A^B 求出非进位结果<br>
    >(A&B)>>1 仅进位结果<br>
    >示例：<br>
    >while(b)<br>
    >{<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;int _a = a ^ b;<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;int _b = (a & b)>>1;<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;a = _a;<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;b = _b;<br>
    >}<br>
- & 判断奇偶性
    >与1 &运算
    >printf("%d  %d\n",11&1,12&1);
- 求绝对值
    >示例：<br>
    >int i = a>>31;//算数右移 <br>
    >return (a^i)-i;//与-1异或等于去反 与0异或不发生改变 <br>
- 位运算素数压缩
    >哈希法 压缩哈希表<br>
    >使用连续内存存储连续的超长二进制数<br>
    >示例：<br>
    >int i,j;<br>
    >int pi = 0;<br>
    >int pnb[50] = {0};//素数表<br>
    >int flag[4] = {0};//素数标志<br>
    >for(i=2;i<100;i++)<br>
    >if(!((flag[i/32]>>(i%32))&1))//取出某一位<br>
    >{<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;pnb[pi++] = i;//存储素数<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;for(j=i;j<100;j+=i)<br>
    >&nbsp;&nbsp;&nbsp;&nbsp;flag[j/32]|=(1<<(j%32));//将所有i的倍数置为1<br>
    >}<br>

- - -
 ### 深拷贝和浅拷贝(C) ###
>深拷贝：内容拷贝 地址不发生变化<br>
>浅拷贝：完全拷贝 地址发生变化<br>
>结构体使用memcpy和结构体直接赋值属于浅拷贝<br>
>串使用memcpy和strcpy使用深拷贝<br>
