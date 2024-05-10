- `<span>` 标签是HTML中的一个内联容器标签，用于将特定内容分组在一起。它没有默认的视觉样式，因此不会改变内部内容的布局或显示属性。`<span>` 通常用于：
	- **文本样式**：可以应用CSS样式，如颜色、字体、大小等，以改变`<span>`标签内文本的外观。
	- **行为控制**：`<span>`可以与JavaScript交互，以响应事件，如点击、悬停等。
	- **标记**：用于将内容标记为特殊或用于语义结构化。
- ### `<span>` 与 `<div>`
  `<span>` 与 `<div>` 的主要区别在于，它们是**内联**和**块级**元素。`<span>` 不会创建新的行，内联其余内容；而 `<div>` 是块级元素，会创建一个新行，将内容分隔开。
- ### 使用示例
	- **文本样式**：
	  logseq.order-list-type:: number
	  ```html
	  <p>This is a <span style="color:red;">red</span> word.</p>
	  ```
	  在这个示例中，`<span>`被用于将文本 "red" 标记出来，并应用了红色字体样式。
	- **交互行为**：
	  logseq.order-list-type:: number
	  ```html
	  <span onclick="alert('Clicked!')">Click me</span>
	  ```
	  在这个示例中，`<span>`绑定了一个点击事件，点击后触发弹窗。
	- **语义结构化**：
	  logseq.order-list-type:: number
	  ```html
	  <p>Price: <span class="price">$9.99</span></p>
	  ```
	  这里，`<span>`用于将价格标记为一个单独的组件，以便通过CSS或JavaScript进行操作。
- ### 常见用途
	- **局部样式**：在文本中应用局部样式，改变颜色、字体或其他CSS属性。
	- **事件绑定**：将JavaScript事件与文本部分绑定。
	- **嵌套内容**：用于结构化HTML文档，而不影响布局。
	  通过`<span>`标签，你可以在HTML中实现灵活的布局和交互功能，是一种常用的内联容器。
	  <!--Converted by ToLogseq-->