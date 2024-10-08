# 拓展

## 结构体中const使用场景


```cpp
#include <iostream>
#include <string>
using namespace std;

// 定义学生结构体
struct sd
{
    string name; // 名字
    int age;     // 年龄
    int test;    // 分数
};

void nout(struct sd s)           //输出结构体变量信息的函数
{
 cout<<"姓名 "<<s.name<<endl
     <<" 年龄 "<<s.age<<endl
     <<" 分数 "<<s.test<<endl;

}

int main(void)
{
    //创建结构体变量
    struct sd s= {"张三",18,90};

    //通过函数打印结构体变量的信息
    nout(s);

    return 0;
}
```

如果我们将函数中的性参改为指针，在人数多的情况下可以减少内存空间

-  

```cpp
#include <iostream>
#include <string>
using namespace std;

// 定义学生结构体
struct sd
{
    string name; // 名字
    int age;     // 年龄
    int test;    // 分数
};

void nout(struct sd *s)           //输出结构体变量信息的函数
{
 cout<<"姓名 "<<s.name<<endl
     <<" 年龄 "<<s.age<<endl
     <<" 分数 "<<s.test<<endl;

}

int main(void)
{
    //创建结构体变量
    struct sd s= {"张三",18,90};

    //通过函数打印结构体变量的信息
    nout(&s);

    return 0;
}
```

但这样有个安全隐患如果我在
-

```cpp
void nout(struct sd *s)           //输出结构体变量信息的函数
{
 cout<<"姓名 "<<s.name<<endl
     <<" 年龄 "<<s.age<<endl
     <<" 分数 "<<s.test<<endl;

}
```

加上个
-

```cpp
void nout(struct sd *s)           //输出结构体变量信息的函数
{
    s->age = 500;
 cout<<"姓名 "<<s.name<<endl
     <<" 年龄 "<<s.age<<endl
     <<" 分数 "<<s.test<<endl;

}
```

那么全部的"年龄"都会被修改
-
所以
=
我们就得在

```cpp
void nout(struct sd *s)           //输出结构体变量信息的函数
{
 cout<<"姓名 "<<s.name<<endl
     <<" 年龄 "<<s.age<<endl
     <<" 分数 "<<s.test<<endl;
}
```

加一个
-

```cpp
void nout(const struct sd *s)
```

这样就不可修改了只能读取,只要修改就报错对于长代码来说是一个莫大的帮助