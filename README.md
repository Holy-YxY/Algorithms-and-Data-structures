# Algorithms-Dstructure(C++语言描述，具备C++特性)

以下列举一些常见实用特性，更多完整特性请参阅官方文档[MSDN](https://msdn.microsoft.com/en-us/library/hh567368.aspx)
---
## Initialize List（初始化列表）
* STL容器的初始化列表:
```C++
//所有STL容器都支持，限于篇幅举例说明
std::vector<double> i_v = {1.1, 2.2, 3.3};
std::map<int, std::string> m = {{1, "a"}, {2, "b"}};
```
* 自定义类的初始化列表:
```C++
class A
{
public:
    A(const int item, const string nameItem):length(item), name(nameItem)
private:
    int length;
    string name;
};
//实例化对象
A a1(3, "Hamlet");
```
## 类型推导 Auto Type
* 类型声明方面
```c++
//过去的这种冗长的类型声明
std::map<int, std::string>::const_iterator itr = m.find(1);
//现在可以写成这样了
auto itr = m.find(1);

//编译器会自动推导出正确的类型。字面量也可以：
auto i = 1;          // int
auto d = 1.1;        // double
auto s = "hi";       // const char*
auto a = { 1, 2 };   // std:: initializer_list<int>
```
* 泛型编程方面
```c++
template<typename T, typename K>
auto add(T a, K b) {
    return a + b;
}

auto a = add(1, 2);     // int add(int, int) a -> int
auto b = add(1, 2.2);   // double add(int, double) b -> double
//注：留意第二个调用，返回值被正确地推断为double类型。
```