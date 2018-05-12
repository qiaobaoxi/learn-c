# learn-c

## 整数

    int
    
    printf("%d",...)
    
    scanf("%d",...)

## 带小数点的数
    
    double
    
    printf("%f",...)
    
    scanf("$lf",...)
    
## 本地变量的规则

    本地变量定义的块内的
    
      它可以是定义在函数的块内
      
      也可以定义在语句的块内
      
      甚至可以随便拉一堆大括号来定义变量
      
    程序运行进入这个块之前，其中的变量不存在，离开这个块，其中的变量就消失了
    
    块外面定义的变量在里面仍然有效
    
    块里面定义了盒外面同名的变量则掩盖了外面的
    
    不能在一个块内定义同名的变量
    
    本地变量不会被默认初始化

## 没有参数时
    
    void f(void)
    
    还是
    
    void f()
      在传统c中，他表示函数的参数表未知，并不表示没有参数

## 逗号运算符

    调用函数时的逗号和逗号运算符怎么区分
    
    调用函数时的圆括号里的逗号是标点符号，不是运算符
    
    f(a,b)
    
    f((a,b))
 
## 二维数组的初始化

     int a[][5]={
       {0,1,2,3,4},
       {2,3,4,5,6},
     }
    
     列数是必须给出的，行数可以由编译器来数
    
     每行一个{}，逗号分隔
    
     最后的都好i可以存在，有古老的传统
    
     如果省略，表示补零
    
     也可以用定位（*c99 ONLY）

### 数组的大小

    sizeof给出整个数组所占据的内容的大小，单位是字节
    
    sizeof(a)/sizeof(a[0])
    
    sizeof(a[0])给出数组中单个元素的大小，于是相除就得到了数组的单元个数
    
    这样的代码，一旦修改数组中初始的数据，不需要修改便利的代码

### 数组的赋值

    int a[]={2,2,2,2,2,3,};
    
    int b[]=a;
    
    数组的变量本身是不能被赋值
    
    要把一个数组的所有元素交割另一个数组，必须采用遍历
    
###搜索内容(json)
     struct {
       int amount;
       char *name;
     } coins[]={
       {1,"penny"},
       {5,"nickel"},
       {10,"dime"},
       {25,"quarter"},
       {50,"half-dollar"}
     }
    int search(){
      
    
    }
    int main(){
      int k=13;
      int i;
      for(i=0;i<sizeof(coins)/sizeof(coins[0]);i++){
        if(k==coins[i].amount){
          printf("%s\n",coins[i].name);
        }
      }
    }
    
  ### 快速查找谋值
  
  从数组中查找某一个值方法 第一种就是for循环  有点简单方便代码少一些问题是效率低都要从起点到结尾
  
  第二种就是二分法取中间值与寻找的值对比如果
  
  ### 运算符$
  
      scanf("%d",&);里的&
    
      获得变量的地址，它的操作数必须是变量
      
      int i;printf("%x",&i);
      
      地址的大小是否与int相同取决于编辑器
      
      int i;printf("%p",&i);
      
### 指针变量

    变量的值是内存的地址
    
    普通变量的值是实际的值
    
    指针变量的值是具有实际值的变量的地址
    
    访问那个地址上的变量*
    
    *是一个单目运算符，用来访问指针的值所表示的地址上的变量
    
    可以做右值也可以做左值
    
    int k=*p;
    
    *p=k+1;
  
  ### 数组变量是特殊的指针
  
     数组变量本身表达地址，所以
     
     int a[10];int*p=a;//无需用&去地址
     
     但是数组的单元表达的是变量，需要用&取地址
     
     a===&a[0]
     
     []运算符可以对数组做，也可以对指针做：
     
     p[0]<==>a[0]
     
     云端付可以对指针做，也可以对数组做：
     
     *a=25;
     
     数组变量是const的指针，所以不能被赋值
     
     int a[]<==>int * const a=[]
     
  ### 字符类型
      
      char是一种整数，也是一种特殊的类型：字符。这是因为
      用单引号表示的字符字面量：‘a’,'1'
      ''也是一个字符
      printf和scanf里用%c老输入输出字符
   
 ### 字符串 
 
     以0（整数0）结尾的一串字符

     0或‘\0’是一样的，但是和‘0’不同

     0标志字符串的结束，但它不是字符串的一部分

     计算字符串长度的时候不包含这个0

     字符串以数组的形式存在，以数组或指针的形式访问

     更多的是以指针的形式

     string.h里有很多处理字符串的函数
 
### 字符串 变量
    
    char *str='hello';
    
    char word[]='hello';
    
    char line[10]='hello';

### 字符串

     c语言的字符串是以字符数组的形态存在
     
     不能用运算符对字符串做运算
     
     通过数组的方式可以遍历字符串
    
     唯一特殊的地方是字符串字棉量可以用来初始化字符数组
 
 ### 指针还是数组？
     
     char *str='hello'
      
     char word[]="hello"
     
       数组：这个字符串在这里
       
       作为本地变量空间自动被回收
       
       指针：这个字符串不知道在哪里
       
       处理参数
       
       东陶分配空间
       
       如果要构造一个字符串->数组
       
       如果要处理一个字符串->指针
       
 ### char*是字符串？
 
      字符串可以表达为char*的性质
      
      char*不一定是字符串
      
      本意是指向字符串的指针，可能只想的是字符的数组（就像int*一样）
      
      只有它所指的字符数组有结尾的0，才能说他所指的是字符串
      
### 字符串输入输出
     
     char string[8];
     
     scanf("%s",string);
     
     printf("%s",string);
     
### 安全的输入

    char string[8];
    
    scanf("%7s",string);
    
    在%和s之间的数字表示最多允许读入的字符的数量，这个数字应该比数组的大小小一
    
    下一次scanf从哪里开始
    
### string.h

     strlen
     
         size_t strlen(const char *s);
         
         返回s的字符串长度（不包括结尾的0);
         

     strcmp
         
         int strcmp(const char *s1,const char *s2);
         
         比较两个字符串，返回
         
         0：s1==s2 
         
         1：s1>s2 
         
         -1 ：s1<s2 
     
     strcpy
         
         char* strcpy(char * restrict dst,const char *restrictsrc)
         
         把 src的字符串拷贝到dst
         
         restrict表明src和dst不重叠
         
         返回dst
           
           为了能连接代码来
     
     strcat
         
         char * strcat(char * restrict s1,const char *restricts2);
         
         把s2拷贝到s1的后面，接成一个长的字符串
         
         返回s1
         
         s1必须具有足够的空间
     
     strchr
         
         
     
     strstr
     
  ### 安全问题
  
      strcpy和strcat都可能出现安全问题
      
      如果目的地没有足够的空间
      
 ### 安全版本
 
     char* strncpy(char * restrict dst,const char * restrictsrc,size_t n)
     
     char* strncat(char * restrict dst,const char * restrictsrc,size_t n)
     
     int strncmp(char * restrict dst,const char * restrictsrc,size_t n)
     
 ### 字符串中找字符
     
     char*strchr（const char *s，int c);
     
     char*strrchr（const char *s，int c);
     
     返回NULL表示没有找到
