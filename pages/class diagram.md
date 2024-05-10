alias:: 类图

- ## 关系
- ### [[泛化关系]]（is a）
	- 表示为[[类]]与类之间的[[继承关系]]，[[接口]]与接口之间的[[继承关系]]，类对接口的[[实现关系]]。
	- 表示方法：
		- 用一个空心箭头+实线，箭头指向父类。
		  ![Generalization.png](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/7/19/16c098bf5e3cdad9~tplv-t2oaga2asx-jj-mark:3024:0:0:0:q75.awebp)
		  或空心箭头+虚线，如果父类是接口。
		  ![implements](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/7/19/16c098c5701ec455~tplv-t2oaga2asx-jj-mark:3024:0:0:0:q75.awebp)
- ### [[关联关系]]（has a）
	- 类与类之间的联接，它使一个类知道另一个类的属性和方法。
	- 表示方法：用 实线+箭头， 箭头指向被使用的类。
	  ![association.png](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/7/19/16c098cf6213f2b2~tplv-t2oaga2asx-jj-mark:3024:0:0:0:q75.awebp)
	- ### [[聚合关系]]
		- 是关联关系的一种，是**强的关联关系**。聚合关系是整体和个体的关系。关联关系的两个类处于同一层次上，而聚合关系两个类处于不同的层次，一个是整体，一个是部分。
		- 表示方法：空心菱形+实线+箭头，箭头指向整体。
		  ![aggregation.png](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/7/19/16c098d852bcfd9d~tplv-t2oaga2asx-jj-mark:3024:0:0:0:q75.awebp)
	- ### [[组合关系]]（contains a）
		- 是关联关系的一种，是**比[[聚合关系]]强的关系**，也称为强聚合；他体现整体与部分间的关系，此时整体与部分是不可分的，整体的生命周期结束也就意味着部分的[[生命周期]]结束。
		- 表示方法：实心菱形+实线+箭头，箭头指向整体。
		  ![composition.png](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/7/19/16c098dc8a47cebf~tplv-t2oaga2asx-jj-mark:3024:0:0:0:q75.awebp)
- ### [[依赖关系]]
	- 是类与类之间的连接，表示一个类依赖于另一个类的定义。例如如果A依赖于B，则B体现为局部变量方法的参数、或静态方法的调用。
	- 表示方法：虚线+箭头 箭头指向被依赖的一方，也就是指向局部变量。
	  ![Dependency](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/7/19/16c098c9a5e420f5~tplv-t2oaga2asx-jj-mark:3024:0:0:0:q75.awebp)
- ![UML类图示例.png](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/7/19/16c098e848db8b12~tplv-t2oaga2asx-jj-mark:3024:0:0:0:q75.awebp)
  collapsed:: true
	- ![image.png](../assets/image_1713620724212_0.png)
	- ![UML类与类之间关系.png](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/7/19/16c098ab66f35678~tplv-t2oaga2asx-jj-mark:3024:0:0:0:q75.awebp)
	- ![a71ea8d3fd1f413459d7efd3221f95cad0c85ebf.webp](../assets/a71ea8d3fd1f413459d7efd3221f95cad0c85ebf_1713620791811_0.webp)
- ## Reference
	- https://baike.baidu.com/item/%E7%B1%BB%E5%9B%BE/4670826
	- https://juejin.cn/post/6844903893327937550
	-