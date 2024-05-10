alias:: 组合模式

- ^^组合模式^^（Composite Pattern）是一种[[结构型设计模式]]，用于处理^^[[树]]状结构^^的数据。**它允许客户端将单个对象和组合对象（即由多个对象组成的对象）一视同仁，提供一种统一的方式来处理对象集合**。组合模式适用于处理递归结构，如文件系统、组织架构、图形界面组件等。
- ### 组合模式的组成：
	- **组件接口（Component Interface）**：
	  logseq.order-list-type:: number
		- 定义所有组件的共同接口，无论是单个对象还是组合对象。
	- **叶子节点（Leaf Nodes）**：
	  logseq.order-list-type:: number
		- 实现组件接口的单个对象，不包含子组件。
	- **组合节点（Composite Nodes）**：
	  logseq.order-list-type:: number
		- 实现组件接口的组合对象，包含子组件的集合。
		- 组合节点可以添加、删除或遍历子组件。
- ### 组合模式的关键特点：
	- **统一处理**：组合模式允许客户端**使用相同的接口来处理单个对象和组合对象**。
	- **递归结构**：组合模式适用于树状结构的数据，支持[[递归]]操作。
	- **灵活性**：组合模式可以动态添加或删除子组件，增强了系统的灵活性。
- ### 示例代码：
  以下是使用 C++ 实现组合模式的一个示例，展示了一个用于组织和管理文件夹和文件的文件系统。
  ```cpp
  #include <iostream>
  #include <vector>
  #include <string>
  #include <memory>
  
  // 组件接口
  class FileSystemComponent {
  public:
    virtual ~FileSystemComponent() {}
    virtual void display(const std::string& prefix) = 0;  // 显示文件系统结构
  };
  
  // 叶子节点：文件
  class File : public FileSystemComponent {
  private:
    std::string name;
  
  public:
    File(const std::string& n) : name(n) {}
  
    void display(const std::string& prefix) override {
        std::cout << prefix << "File: " << name << std::endl;
    }
  };
  
  // 组合节点：文件夹
  class Folder : public FileSystemComponent {
  private:
    std::string name;
    std::vector<std::shared_ptr<FileSystemComponent>> components;
  
  public:
    Folder(const std::string& n) : name(n) {}
  
    void add(const std::shared_ptr<FileSystemComponent>& component) {
        components.push_back(component);
    }
  
    void display(const std::string& prefix) override {
        std::cout << prefix << "Folder: " << name << std::endl;
        for (const auto& component : components) {
            component->display(prefix + "  ");
        }
    }
  };
  
  // 客户端代码
  int main() {
    auto rootFolder = std::make_shared<Folder>("Root");
  
    auto file1 = std::make_shared<File>("File1.txt");
    auto file2 = std::make_shared<File>("File2.txt");
    rootFolder->add(file1);
    rootFolder->add(file2);
  
    auto subFolder = std::make_shared<Folder>("SubFolder");
    auto file3 = std::make_shared<File>("File3.txt");
    subFolder->add(file3);
  
    rootFolder->add(subFolder);
  
    rootFolder->display("");  // 输出整个文件系统结构
  
    return 0;
  }
  ```
  
  在这个示例中，`FileSystemComponent` 是组件接口，`File` 是叶子节点，`Folder` 是组合节点。通过 `Folder` 的 `add` 方法，可以将 `File` 和 `Folder` 组合在一起，形成树状结构。通过 `display` 方法，可以递归地显示整个文件系统结构。
- ### 使用场景：
	- 当需要处理树状结构的数据时。
	- 当客户端需要统一处理单个对象和组合对象时。
	- 当需要递归操作对象集合时。
- ### 注意事项：
	- **过度复杂**：如果结构较简单，可能不需要组合模式。
	- **性能开销**：组合模式可能引入额外的内存和处理开销，特别是处理大规模结构时。
- 组合模式提供了一种优雅的方式来处理树状结构的数据，允许客户端在不区分单个对象和组合对象的情况下进行操作。