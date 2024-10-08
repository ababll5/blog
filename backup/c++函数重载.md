
# 函数重载

## 函数重载概述

作用：函数名可以相同，提高复用性



函数重载满足条件：

- 同一个作用域下
- 函数名相同
- **函数参数类型不同**或者**个数不同**或者**顺序不同**



> **注意**：函数的返回值不可以作为函数重载的条件



> 示例：

```cpp
#include<iostream>
using namespace std;

//函数重载
//可以让函数名相同，提高函数的复用性

//条件
//1 同一个作用域下
//2 函数名称相同
//3 函数的参数类型不同 || 个数不同 || 顺序不同
void func()
{
    cout<<"func的调用"<<endl;
}

//类型不同
void func(int a)
{
    cout<<"func(int a)的调用!"<<endl;
}

void func(double a)
{
    cout<<"func(double a)的调用!"<<endl;
}


//顺序不同
void func(int a,double b)
{
    cout<<"func(int a,double b)的调用"<<endl;
}

void func(double a,int b)
{
    cout<<"func(double a,int b)的调用"<<endl;
}




int main()
{
    func();

    func(10);

    func(11.45);

    func(11,0.45);

    func(0.45,11);
    
    system("pause");
    return 0;
}
```



> 注意事项：
>
> > 函数的返回值不可以作为函数重载的条件



## 函数重载的注意事项

- 引用作为重载条件
- 函数重载碰到函数默认参数



```cpp
#include<iostream>
using namespace std;


//注意事项
//1 应用作为重载的条件
void func(int &a)
{
    cout<<"func(int &a)调用"<<endl;
}

void func(const int &a)
{
    cout<<"func(const int &a)调用"<<endl;
}

//2 函数重载碰到默认参数
void func2(int c,int d = 10)
{
    cout<<"func2(int a,int d)的调用"<<endl;
} 

void func2(int c)
{
    cout<<"func2(int a)的调用"<<endl;
} 

int main(void)
{
    int b = 10;
    func(b);

    const int a = 10;
    func(a);

    func(10);

    cout<<endl<<"--------------------------------"<<endl<<endl;

    // func2(10); //报错

    system("pause");
    return 0;
}
```



> 函数重载尽量不要设默认值