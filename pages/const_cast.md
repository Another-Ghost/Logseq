- ``` c++
  const_cast<target-type>(expression)	//返回 target-type 类型的值	
  ```
- `const_cast`用于在不同[[cv-修饰符]]间转换，可以添加或移除。
- 例如，为了将一个`const`指针传递给一个期望非`const`参数的函数：``` cpp
  // const_cast
  #include <iostream>
  using namespace std;
  
  void print (char * str)
  {
    cout << str << '\n';
  }
  
  int main () {
    const char * c = "sample text";
    print ( const_cast<char *>(c) );
    return 0;
  }
  ```
  上面的示例保证可以正常工作，因为函数 `print` **不会修改**指向的对象。
  但需要注意的是，如果去掉指向对象的`const`属性，并实际上对其进行**写操作**，会导致 *未定义行为* 。