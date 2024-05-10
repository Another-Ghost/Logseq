alias:: Unicode标准, The Unicode Standard, 统一码, 统一字符编码, 统一字元码

- [[Unicode标准]]是[[信息技术]]领域的业界标准，其整理、编码了世界上大部分的 *文字系统* ，使得 计算机 能以通用划一的[[字符集]]来 处理 和 显示 文字 。
- # Unicode的实现方式
	- Unicode的 *实现方式* 不同于编码方式。**一个字符的 Unicode 编码确定**。但是在实际传输过程中，由于不同系统平台的设计不一定一致，以及出于**节省空间**的目的，对Unicode编码的实现方式有所不同。
- [[私有使用区]]（PUA）: U+E000 到 U+F8FF
- ## 在[[HTML]]中使用Unicode字符
  在HTML中使用Unicode字符有多种方式，包括直接插入字符、使用HTML实体、使用十六进制代码、和Unicode代码点。
	- **直接插入Unicode字符**
	  logseq.order-list-type:: number
	  最简单的方法是直接插入Unicode字符。例如：
	  ```html
	  <p>Here is a star symbol: ★</p>
	  ```
	- **使用HTML实体**
	  logseq.order-list-type:: number
	  HTML实体是另一种引用Unicode字符的方法。这种方式在需要编码时特别有用。HTML实体以 `&` 开头，以 `;` 结尾，例如：
	  ```html
	  <p>Copyright symbol: &copy;</p> <!-- 这将显示为© -->
	  ```
	- **使用十六进制Unicode代码**
	  logseq.order-list-type:: number
	  可以使用Unicode字符的十六进制代码与HTML实体结合来显示字符。例如：
	  ```html
	  <p>Greek letter alpha: &#x03B1;</p> <!-- 这将显示为α -->
	  ```
	- **使用十进制Unicode代码**
	  logseq.order-list-type:: number
	  与使用十六进制相似，但使用十进制代码。例如：
	  ```html
	  <p>Heart symbol: &#9829;</p> <!-- 这将显示为♥ -->
	  ```
	- ### 设置HTML的字符编码
	  为了确保正确处理Unicode字符，确保在HTML文档中设置适当的字符编码。通常是UTF-8，这是最通用和广泛支持的字符编码。
	  ```html
	  <meta charset="UTF-8">
	  ```
	  在HTML的 `<head>` 部分中设置 `UTF-8` 可以确保你的文档支持Unicode字符，并正确显示它们。
- ### [[圆圈数字]]