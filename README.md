[合集 \- 3个月搞定计算机二级C语言(6\)](https://github.com)[1\.2个月搞定计算机二级C语言——真题（5）解析10\-29](https://github.com/main-studio/p/18511838)[2\.2个月搞定计算机二级C语言——真题（6）解析10\-30](https://github.com/main-studio/p/18515198)[3\.2个月搞定计算机二级C语言——真题（7）解析11\-03](https://github.com/main-studio/p/18523045)[4\.2个月搞定计算机二级C语言——真题（8）解析11\-03](https://github.com/main-studio/p/18523099)[5\.2个月搞定计算机二级C语言——真题（9）解析11\-06](https://github.com/main-studio/p/18531036):[FlowerCloud机场](https://hushicha.org)6\.2个月搞定计算机二级C语言——真题（10）解析11\-08收起
## 1\. 前言


本篇我们讲解[2个月搞定计算机二级C语言](https://github.com)——真题10


[![真题10-程序评分](https://img2024.cnblogs.com/blog/2881477/202411/2881477-20241107203331440-612350631.png)](https://github.com)


## 2\. 程序填空题


### 2\.1 题目要求


[![真题10-程序填空](https://img2024.cnblogs.com/blog/2881477/202411/2881477-20241107203331225-1646112441.png)](https://github.com)


### 2\.2 提供的代码



```
#include  
#pragma warning (disable:4996)
double  fun(double x[], int n)
{
	int i, k = 0;
	double avg = 0.0, sum = 0.0;
	for (i = 0; i < n; i++)
		avg += x[i];
	/**********************found***********************/
	avg /= ____(1)____;
	for (i = 0; i < n; i++)
		if (x[i] > avg)
		{
			/**********************found***********************/
			____(2)____ += x[i];
			k++;
		}
	/**********************found***********************/
	return  ____(3)____;
}
main()
{
	double score[12] = { 50,60,70,80,90,100,55,65,75,85,95,99 };
	double aa;
	aa = fun(score, 12);
	printf("%f\n", aa);
}

```

### 2\.3 解题思路


**第（1）处填空：**


在这条语句之前，程序使用`for`循环将所有学生的成绩加到了变量`avg`中，这里我们要实现的是求平均成绩，所以需要使用`avg`除学生的数量`n`，即可得到所有学生的平均成绩，并赋值给`avg`。


其中`avg /= n;`等价于`avg = avg / n;`。



```
avg /= n;

```

**第（2）处填空：**


经过`if (x[i] > avg)`判断，进来以后的`x[i]`都是大于平均成绩`avg`的，这里要执行的是将符合条件的`x[i]`累加至`sum`（程序已给出），并且每次使`k++`以便于后续求平均值。



```
sum += x[i];

```

**第（3）处填空：**


这里我们需要返回的是高于平均成绩的学生成绩的平均值，其中`sum`为高于平均成绩的学生总成绩，`k`为高于平均成绩的学生人数，用`sum / k`即可得到高于平均成绩的学生成绩的平均值。



```
return  (sum / k);

```

### 2\.4 代码实现


填写完整的代码：



```
#include  
#pragma warning (disable:4996)
double  fun(double x[], int n)
{
	int i, k = 0;
	double avg = 0.0, sum = 0.0;
	for (i = 0; i < n; i++)
		avg += x[i];
	/**********************found***********************/
	avg /= n;
	for (i = 0; i < n; i++)
		if (x[i] > avg)
		{
			/**********************found***********************/
			sum += x[i];
			k++;
		}
	/**********************found***********************/
	return  (sum / k);
}
main()
{
	double score[12] = { 50,60,70,80,90,100,55,65,75,85,95,99 };
	double aa;
	aa = fun(score, 12);
	printf("%f\n", aa);
}

```

提示：为确保代码正常运行，请在题库编程环境的对应题目中进行测试和运行。


## 3\. 程序修改题


### 3\.1 题目要求


[![真题10-程序修改](https://img2024.cnblogs.com/blog/2881477/202411/2881477-20241107203331266-1126860948.png)](https://github.com)


### 3\.2 提供的代码



```
#include 
void  fun(char* s)
{
    int  i, j;
    for (i = 0, j = 0; s[i] != '\0'; i++)
        if (s[i] >= '0' && s[i] <= '9')
            /**********found**********/
            s[j] = s[i];
    /**********found**********/
    s[j] = "\0";
}
main()
{
    char  item[80];
    printf("\nEnter a string  :  "); gets(item);
    printf("\n\nThe  string  is  : \"%s\"\n", item);
    fun(item);
    printf("\n\nThe string of changing is  : \"%s\"\n", item);
    getchar();
}

```

### 3\.3 解题思路


**第（1）处修改：**


这里需要将取出的数字字符形成新的字符串，并取代原字符串。


只使用`s[j]`是不行的，因为在程序中`j`始终没有改变值，一直为 0，导致每次的数字字符都会存储到`s[0]`的地址中，并没有形成新的字符串，所以我们要在这里让`j++`，从而改变存储的地址。



```
s[j++]=s[i];

```

**第（2）处修改：**


`""`是用来表示字符串的，而这里的`s[j]`只能存储单个字符，所以需要使用`''`来括起来。


这里给`s[j]`赋值`'\0'`是应为字符串是以`'\0'`作为结尾的。



```
s[j]='\0';

```

### 3\.4 代码实现


修改后的代码：



```
#include 
void  fun(char  *s)
{  int  i,j;
   for(i=0,j=0; s[i]!='\0'; i++)
        if(s[i]>='0' && s[i]<='9')
/**********found**********/
            s[j++]=s[i];
/**********found**********/
        s[j]='\0';
}
main()
{  char  item[80];
   printf("\nEnter a string  :  ");gets(item);
   printf("\n\nThe  string  is  : \"%s\"\n",item);
   fun(item);
   printf("\n\nThe string of changing is  : \"%s\"\n",item );
  getchar();
}

```

提示：为确保代码正常运行，请在题库编程环境的对应题目中进行测试和运行。


## 4\. 程序设计题


### 4\.1 题目要求


[![真题10-程序设计](https://img2024.cnblogs.com/blog/2881477/202411/2881477-20241107203331207-1465308833.png)](https://github.com)


### 4\.2 提供的代码



```
#include 
#include 

void  fun(char* s, char  t[])
{



}

main()
{
    char   s[100], t[100]; void NONO();
    printf("\nPlease enter string S:"); scanf("%s", s);
    fun(s, t);
    printf("\nThe result is: %s\n", t);
    NONO();
    getchar();
}

void NONO()
{/* 本函数用于打开文件，输入数据，调用函数，输出数据，关闭文件。 */
    char s[100], t[100];
    FILE* rf, * wf;
    int i;

    rf = fopen("in.dat", "r");
    wf = fopen("out.dat", "w");
    for (i = 0; i < 10; i++) {
        fscanf(rf, "%s", s);
        fun(s, t);
        fprintf(wf, "%s\n", t);
    }
    fclose(rf);
    fclose(wf);
}

```

### 4\.3 解题思路


这道题其实蛮容易的，无非就是遍历数组，再加个奇偶数的判断。


奇偶数判断前面也讲过，这里简单提一下：一个数除 2 取余等于 0，则为偶数，等于 1 则为奇数。


在函数开头要先将`t`所指的数组清空，然会遍历指针`s`所指的字符串，判断 ASCII 值为偶数则存到`t`中，其中`t[j++]`的作用和上一题一样。


题目要求将奇数的字符删除后，将剩余的字符放入`t`，实质就是把偶数的字符放入`t`，可以直接对偶数的字符操作，减少程序的复杂度。


### 4\.4 代码实现


填写完整的代码：



```
#include 
#include 

void  fun(char* s, char  t[])
{
    int i = 0,j = 0;

    for (i = 0; i < (sizeof(t) / sizeof(t[0])); i++)	// 清空数组 t，防止出现垃圾值
    {
        t[i] = 0;
    }

    for (i = 0; i < strlen(s); i++)
    {
        if ((s[i] % 2) == 0)	// 等于 0 说明是 ASCII值为偶数
        {
            t[j++] = s[i];		// 保存到 t 所指的数组中
        }
    }
}

main()
{
    char   s[100], t[100]; void NONO();
    printf("\nPlease enter string S:"); scanf("%s", s);
    fun(s, t);
    printf("\nThe result is: %s\n", t);
    NONO();
    getchar();
}

void NONO()
{/* 本函数用于打开文件，输入数据，调用函数，输出数据，关闭文件。 */
    char s[100], t[100];
    FILE* rf, * wf;
    int i;

    rf = fopen("in.dat", "r");
    wf = fopen("out.dat", "w");
    for (i = 0; i < 10; i++) {
        fscanf(rf, "%s", s);
        fun(s, t);
        fprintf(wf, "%s\n", t);
    }
    fclose(rf);
    fclose(wf);
}

```

提示：为确保代码正常运行，请在题库编程环境的对应题目中进行测试和运行。


## 5\. 后记


本篇博客到这就结束了，如果您有疑问或建议欢迎您在留言区留言。


