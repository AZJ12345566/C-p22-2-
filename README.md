# C-p22-2-
C语言学习笔记 p22 初识指针(2)
#incldue<stdio.h>
int main()
{
    //未初始化的指针变量
    int* p;//一个局部变量不初始化，里面放的一个随机值
    *p=20;
    return 0;
}

int main()
{
    //指针越界访问
    int a[10]={0};
    int i=0;
    int* p=a;
    for(i=0;i<=12;i++)
    {
        *p=i;
        p++;
        //以上两行代码可以表示为：
        *p++=i;
    }
    return 0;
}

test()
{
    int a=10;//局部变量出这个函数即被销毁，除非他是static变量
    return &a;
}
int main()
{
    //指针指向的空间被释放
    int* p=test();
    printf("%d\n",*p);
    return 0;
}
//当指针初始化时，不知道指针放什么的时候，就给它加NULL相当于(void*) 0

//指针运算
//指针+-整数
int mian()
{
    int arr[10]={1,2,3,4,5,6,7,8,9,10};
    int i=0;
    int sz=sizeof(arr)/sizeof(arr[0]);
    int* p=arr;
    for(i=0;i<10;i++)
    {
        printf("%d",*p);
        p=p+1;//也可以换成p++
    }
    return 0;
}

int main()
{
    int arr[10]={1,2,3,4,5,6,7,8,9,10};
    printf("5d\n",&arr[9]-&arr[0]);
    retrurn 0;
}//指针-指针的值是值之间的元素个数

int main()
{
    char ch[5]={0};
    int arr[10]={1,2,3,4,5,6,7,8,9,10};
    printf("%d\n",&arr[9]-&ch[0]);
    return 0;
}//如果两个指针指向的不是同一块空间，那么输出也是无法预知的

my_strlen(char* str)
{
    char* start=str;
    char* end=str;
    while(*end!='\0')
    {
        end++;
    }
    return end-start;
}
int mian()
{
    //以前笔记记过计数器和递归两种方式实现strlen
    char arr[]="bit";
    int len=my_strlen(arr);
    printf("%d\n",len);
}

//指针的关系运算
//C语言规定允许指向元素的指针与指向数组最后一个元素的那个内存位置的指针比较，但是不允许与指向第一个元素之前的那个内存位置的指针进行比较

int main()
{
    int arr[10]={0};
    printf("%p\n",arr);//地址-首元素地址
    printf("%p\n",&arr[0]);//
    printf("%p\n",&arr);
    //数组名在绝大多数情况下都是首元素地址，但有两个例外
    //1.&arr-&数组名-数组名不是首元素地址-数组名表示整个数组-&数组名取出的是整个数组的地址
    //2.sizeof(arr)-sizeof（数组名）-数组名表示的是整个数组的地址-sizeof(数组名)计算的是整个数组的大小
    return 0;
}

int main()
{
    int arr[10]={0};
    int* p=arr;
    return 0;
}//数组也是可以通过指针来访问的

//二级指针
int main()
{
    int a=10;
    int* pa=&a;
    int** ppa=&pa;//ppa就是一个二级指针
    return 0;
}

//指针数组-数组-存放指针的数组
//数组指针-指针
int main()
{
    int a=10;
    int b=20;
    int c=30;
    int* pa=&a;
    int* pb=&b;
    int* pc=&c;
    //整形数组-存放整形
    //字符数组-存放字符
    //指针数组-存放指针
    int arr[10];
    int* arr2[3]={&a,&b,&c};;//指针数组
    int i=0;
    for(i=0;i<3;i++)
    {
        printf("%d",*(arr2[i]));
    }
    return 0;
}





