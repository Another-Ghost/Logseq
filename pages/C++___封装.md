public:: false

- 在 C++ 中，封装是面向对象编程的一个核心概念，指的是将数据（属性）和操作这些数据的方法（函数）捆绑在一起的做法。封装不仅隐藏了类的内部细节，还可以定义数据的修改规则，从而保证数据的安全性和完整性。
- ### 封装的主要特点
  
  1. **数据隐藏**：通过将类的成员声明为私有（`private`）或受保护（`protected`），可以隐藏类的内部实现细节，只暴露必要的操作接口给外界。
  
  2. **接口暴露**：通过公共（`public`）方法提供类的功能，而不直接操作内部数据。
  
  3. **控制访问**：可以定义公共方法来控制对私有数据的访问和修改，这些方法也称为“存取器”（getters）和“修改器”（setters）。
- ### 示例
  
  ```cpp
  class Box {
  private:
    // 私有属性，外部无法直接访问
    double length;
    double width;
    double height;
  
  public:
    // 构造函数
    Box(double l, double w, double h) : length(l), width(w), height(h) {}
  
    // 公共方法，用于计算体积
    double calculateVolume() {
        return length * width * height;
    }
  
    // 设置器和获取器
    void setLength(double l) {
        if (l > 0) length = l;
    }
    double getLength() {
        return length;
    }
  
    // ... 其他方法 ...
  };
  ```
  
  在这个例子中，`Box` 类将 `length`、`width` 和 `height` 属性封装起来，并通过公共方法 `calculateVolume`、`setLength` 和 `getLength` 提供了对这些属性的受控访问。
- ### 封装的优势
- **增强安全性**：隐藏类的内部状态和功能实现，防止外部代码直接操作内部数据，从而减少了数据被意外或恶意修改的风险。
- **易于维护和修改**：类的内部实现可以独立于它的外部接口进行修改，不会影响到使用该类的代码。
- **提高可读性和可管理性**：清晰地区分内部实现和外部接口，使得代码更易于理解和维护。
  
  封装是面向对象设计的基石之一，它强调通过接口而非实现来编程，有助于构建更加健壯、灵活和易于维护的软件。