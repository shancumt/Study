[toc]

### 1. 图形对象

图形对象：具有公共属性的元素的集合

![图形对象的层次结构](https://github.com/shancumt/Study/blob/master/Matlab/Pictures/%E5%9B%BE%E5%BD%A2%E5%8F%A5%E6%9F%84.png?raw=true)

获取图形对象句柄的函数  
|  函数   |                         功能                         |
| :-----: | :--------------------------------------------------: |
|   gcf   |     获取当前图形窗口的句柄（get current figure）     |
|   gca   |       获取当前坐标轴的句柄（get current axis）       |
|   gco   | 获取最近被选中的图形对象的句柄（get current object） |
| findobj |           按照指定属性来获取图形对象的句柄           |

图形对象的句柄由系统自动分配，每次分配的值不一定相同。在获取对象的句柄后，可以通过句柄来设置或获取对象的属性。

### 2. 图形对象的属性 

* 属性名+属性值
* 属性名用`''`括起来，不区分大小写
* 设置属性：`set(句柄，'属性名1'，性值1，'属性名2'，属性值2···)`  
  如果在调用set函数的时候忽略全部的属性名和属性值，则将显示出句柄所有的允许属性。
* 获取属性值：`V = get(句柄，'属性名')`   V是获取的属性值  
  如果在调用get函数时省略属性名，则将返回句柄所有的属性值。
* 图形对象的公共属性
	* Children属性：该属性的取值是该对象所有子对象的句柄组成的一个向量
	* Parent属性：该属性的取值是该对象的父对象的句柄
	* Tag属性：该属性的取值是一个字符串，相当于给该对象定义了一个标识符。此后，在任何程序中均可以通过`findobj()`函数来获取该标识符所对应的图形的句柄。例如：`hf = findobj(0,'tag','flag1')`
	* Type属性：表示该对象的类型，其取值不可改变。
	* UseData属性：该属性的取值是一个**矩阵**，默认是空矩阵，在程序设计时，可以将数据储存在该矩阵中，以达到**数据传输**的目的。
	* Visible属性：取值为on（缺省值）或off，用来显示或隐藏图形窗口的动态变化过程。
	* ButtonDownFcn属性：该属性的取值是一个字符串，一般是某个**M文件**或**一小段Matlab程序**，当鼠标指针位于对象之上，用户按下鼠标键时执行的字符串。
	* CreateFcn属性：
	* DeleteFcn属性等

### 3. 图像窗口对象
#### 创建图形窗口对象

* `句柄变量 = figure('属性名1',属性值1，'属性名2'，属性值2···)`  
* `figure`  
* `句柄变量 = figure`

#### 关闭图形窗口

* `close(窗口句柄)`：关闭图形窗口
* `close all`：关闭所有的图形窗口
* `clf`：清除当前图形窗口的内容，但不关闭窗口

#### 属性

* Menubar：用于控制图形窗口是否应该具有菜单条，取值为figure（缺省值）或None
* Name：它的属性取值可以是任意**字符串**，缺省值为空
* NumberTitle：决定图形窗口标题是否以“Figure No.n”为标题前缀，取值为on（缺省值）或off
* Resize：决定图形窗口建立后是否可用**鼠标改变该窗口的大小**，取值为on（缺省值）或off
* Position：定义了图形窗口对象在屏幕上的位置和大小，取值为[n1,n2,n3,n4]，其中n1和n2分别为窗口左下角的**横纵坐标值**，n3和n4分别为窗口的**宽度和高度**，单位由units属性决定
* Units：该属性的取值为：pixel（像素，缺省值），normalized（相对单位），inches（英寸），centimeters（厘米）和points（磅）
* Color：取值为一个颜色值，既可以用**字符**表示，也可以用**RGB三元组**表示，缺省值为[0.8 0.8 0.8]
* Pointer：用于设定鼠标标记的显示形式，取值为arrow（缺省值），crosshair，watch，top，topr，botl，botr，circle，cross，fleur，custom等
* KeyPressFcn：
* WindowButtonDownFcn：鼠标按下响应
* WindowButtonMotionFcn：鼠标移动响应
* WindowButtonUpFcn：鼠标释放响应

### 4. 坐标轴对象

所谓在某个图形窗口中输出图形对象，实质上指在该图形窗口中的当前坐标轴中输出图形图像。  
坐标轴对象是图形窗口的子对象，每个图形窗口中可以定义多个坐标轴对象，但是只有一个坐标轴对象是当前坐标轴对象。

#### 创建坐标轴对象
* `句柄函数 = axes('属性名1',属性值1，'属性名2'，属性值2···)`
* `axes`
* `句柄变量 = axes`
* `axes(坐标轴对象)`：将坐标轴设为当前坐标轴，且坐标轴所在的图形窗口自动成为当前图形窗口
##### 属性
* Box属性：决定当前坐标轴是否带有边框，取值为**on或off（缺省值）**
* GridLineStyle属性：定义网格线的类型，取值为**`:`,`-`,`-.`,`--`**或**`None`**
* Position属性:决定坐标轴矩形区域在图形窗口中的位置，取值为取值为[n1,n2,n3,n4]，其中n1和n2分别为窗口左下角的**横纵坐标值**，n3和n4分别为窗口的**宽度和高度**，单位由units属性决定
* Units属性：定义了`Position`属性的度量单位，该属性的取值为：pixel（像素），normalized（相对单位，缺省值），inches（英寸），centimeters（厘米）和points（磅）
* Title属性：该属性的取值是当前坐标轴标题文字对象的句柄，可以通过该属性对坐标轴标题文字队行进行操作。如改变标题颜色，`h = get(gca,'title');set(h,'color','r')`
* XLabel，YLabel，Zlabel属性：3种属性的取值分别为x，y，z轴说明文字的句柄，其操作与`Title`属性相同
* XLim，YLim，ZLim属性：3种属性的取值粉笔都是具有两个元素的数值向量，分别定义各坐标轴的上下限，缺省值为[0,1]，高层函数`axis`实际上是对这些属性的直接赋值
* XScale，YScale，ZScale属性：定义各坐标轴的刻度类型，3种属性的取值分别为`linear(缺省)`或`log`
* View属性：定义视点方向，取值为两个元素的数值向量

### 5. 底层绘图操作

#### 曲线对象
曲线对象是坐标轴对象的子对象，它既可以定义在二位坐标系中使用，也可以定义在三维坐标系中使用
##### 创建曲线对象
* `句柄对象 = line(x,y,z,'属性名1',属性值1···)` 
##### 属性
* 公共属性
* Color属性：取值为代表颜色的字符或RGB值
* LineStyle属性：定义线型
* LineWidth属性：定义线宽，缺省值为0.5磅
* Marker属性：定义数据点标记符号，缺省值为`none`
* MarkerSize属性：定义数据点标记符号的大小，缺省值为6磅
* XData、YData、ZData属性：表示曲线对象的3个坐标轴数据，取值为数值向量或矩阵

#### 曲面对象

曲线对象也是坐标轴的子对象，它定义在三位坐标系中，而坐标系可以在任何视点下
##### 创建曲面对象
* `句柄对象 = surface(x,y,z,'属性名1',属性值1···)` 
##### 属性
* 公共属性
* EdgeColor属性：定义**曲面网格线**的颜色或着色方式，取值为代表颜色的字符或RGB值还可以是`flat`、`interp`或`none`，缺省值为黑色
* FaceColor属性：定义**曲面网格片**的颜色或着色方式，取值和`EdgeColor`属性相似，缺省值为`flat`
* LineStyle属性：定义网面网格线的类型
* LineWidth属性：定义网格线的线宽，缺省值为0.5磅
* Marker属性：定义曲面数据点标记符号，缺省值为`none`
* MarkerSize属性：定义曲面数据点标记符号的大小，缺省值为6磅
* XData、YData、ZData属性：表示曲线对象的3个坐标轴数据，取值为数值向量或矩阵

#### 文本对象

##### 创建文本对象
* `句柄对象 = text(x,y,z,'说明文字','属性名1',属性值1···)`   
其中的说明文字除使用标准的ASCII字符外，还可使用[LaTeX](https://raw.githubusercontent.com/shancumt/Study/master/Markdown/lshort-zh-cn.pdf  ’LaTex语法说明‘)格式的控制字符，这样可以在图形上添加希腊字母，数学符号即公式等内容
##### 属性
* Color属性：定义文字对象的显示颜色
* String属性：定义文字标注的内容，取值为字符串或字符串矩阵
* Interpreter属性：取值为Latex或None，控制文字标注内容的解释方式，即LaTex方式或ASCII方式
* FontSize属性：定义文字对象的大小，缺省值为10磅
* Rotation属性，定义文字对象的旋转方向，取值为数值量，缺省值为0，取正值时表示逆时针方向旋转，负值时表示顺时针方向旋转。

### 参考材料

[参考ppt](https://raw.githubusercontent.com/shancumt/Study/741c6cb521e74a6c85cd5078560d1a40288f56de/Matlab/Material/MATLAB%E7%AC%AC9%E7%AB%A0%E5%9B%BE%E5%BD%A2%E5%8F%A5%E6%9F%84.pdf)

