
# 函数提高

## 函数默认参数



在c++中，函数的形参列表中的形参是可以有默认值的

语法`返回值类型 函数名 (参数 = 默认值){}`

```cpp
#include<iostream>
using namespace std;

//函数的默认参数

//如果自己传了就用自己的，没有就用默认的
int func(int a,int b = 20,int c = 30)
{
    return a+b+c;
}

int main(void)
{
    int a = func(10,30);
    cout<<a<<endl;

    system("pause");
    return 0;
}
```



**注意事项:**

> 如果某个位置已经有了默认参数，那么从这个位置往后，从左到右都必须有默认值  

**错误示例：**

```cpp
int func(int a,int b = 10,int c){}
```



> 如果函数声明有默认参数，函数实现就不能有默认参数
>
> > 声明和实现只能有一个

**错误示例：**

```cpp
int func(int a = 10,int b =10); //声明
int func(int a = 10,int b =10){……}//实现
```



## 函数占位参数

c++中函数的形参列表里可以有占位参数，用来做占位，调用函数时必须填补该位置

语法:   `返回值类型 函数名 (数据类型){}`

在线阶段函数的占位参数意义并不大，但是后面会用到该技术

```cpp
#include<iostream>
using namespace std;

//占位参数

void func(int a,int)
{
    cout<<"hello world"<<endl;

}

int main(void)
{
    func(1145,114); //必须填int类型的数据，不然报错

    system("pause");
    return 0;
}
```



> 占位参数还可以有默认参数

```cpp
void func(int a , int = 20)
```

