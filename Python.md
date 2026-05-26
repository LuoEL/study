Python 基础（变量、列表、循环、函数）

1.注释  #注释内容 
        """注释内容"""

2.变量
        x = 10;
        y = "hello world" #直接赋值，str变量可以用单引号和双引号
        global  #全局变量关键字

3.数据类型
          文本：str
            字符串是数组
            len() #获取字符串长度
            a.strip() #方法删除开头和结尾的空白字符
            a.lower() #返回小写的字符串
            a.upper() #方法返回大写的字符串
            replace() #用另一段字符串来替换字符串
              a = "Hello, World!"
              print(a.replace("World", "Kitty"))
            split() #方法在找到分隔符的实例时将字符串拆分为子字符串
              a = "Hello, World!"
              print(a.split(",")) # returns ['Hello', ' World!']
            检查字符串中是否存在特定短语或字符，我们可以使用 in 或 not in 关键字

          数值：int float complex
            int:正数或负数
            float:包含小数的正数或负数
            complex:复数

          序列：list tuple range
            列表（List）是一种有序和可更改的集合,允许重复的成员,列表用方括号编写  thislist = ["apple", "banana", "cherry"],可以通过引用索引号来访问列表项thislist[0]
            可以使用 for 循环遍历列表项 for x in thislist:
            如需确定列表中是否存在指定的项，请使用 in 关键字
            如需确定列表中有多少项，请使用 len() 方法
            如需将项目添加到列表的末尾，请使用 append() 方法
            要在指定的索引处添加项目，请使用 insert() 方法
            remove() 方法删除指定的项目
            pop() 方法删除指定的索引（如果未指定索引，则删除最后一项）
            del 关键字也能完整地删除列表
            clear() 方法清空列表
            使用 copy() 方法来复制列表
            使用 list() 方法复制列表

            元组是有序且不可更改的集合。在 Python 中，元组是用圆括号编写的
          映射：dict
          集合：set frozenset
            集合是无序和无索引的集合。在 Python 中，集合用花括号编写

          字典：Dictionary
            字典是一个无序、可变和有索引的集合。在 Python 中，字典用花括号编写，拥有键和值
            您可以通过在方括号内引用其键名来访问字典的项目
            通过使用 items() 函数遍历键和值 
            pop() 方法删除具有指定键名的项

          布尔：bool

          二进制：bytes bytearray memotyview

          获取数据类型：type()

          随机数：random()
            import random #导入模块
            print(random.randrange(1,10)) #生成1到9的随机数

4.if
  and
  or
  pass

5.while
  continue

6.for
  for循环用于迭代序列（即列表，元组，字典，集合或字符串）
  如需循环一组代码指定的次数，我们可以使用 range() 函数
  range() 函数默认将序列递增 1，但是可以通过添加第三个参数来指定增量值：range(2, 30, 3)(起始，结束，步长)  

7.函数
  使用 def 关键字定义函数



NumPy 基础（数组、矩阵乘法、转置、求和）

1.入门
  import numpy  #导入库
  import numpy as np  #用np代替numpy

2.数组创建
  arr = np.array([1, 2, 3, 4, 5]) #arr是numpy.ndarray类型的
  arr = np.array([[1, 2, 3], [4, 5, 6]])  #二维数组
  arr = np.array([[[1, 2, 3], [4, 5, 6]], [[1, 2, 3], [4, 5, 6]]])  #三维数组
  arr.ndim，该属性返回一个整数，该整数会告诉我们数组有多少维
  arr = np.array([1, 2, 3, 4], ndmin=5) #创建一个五维数组
  arr.shape 该属性返回一个元组，每个索引具有相应元素的数量
  arr.reshape(4, 3) 最外面的维度将有 4 个数组，每个数组包含 3 个元素，把一维改为二维
  reshape(-1) 将多维数组转换为 1D 数组
  for x in np.nditer(arr):  迭代遍历数组的每个标量
  ndenumerate() 元素的相应索引

Matplotlib 基础（画点、画线、显示）
1.pypolt
  import matplotlib.pyplot as plt
  import numpy as np

  xpoints = np.array([0, 6])
  ypoints = np.array([0, 250])

  plt.plot(xpoints, ypoints)
  plt.show()

2.marker 
  来用指定的标记强调每个点
  plt.plot(ypoints, marker = 'o')
  plt.plot(ypoints, 'o:r')  marker|line|color

3.linestyle
  plt.plot(ypoints, linestyle = 'dotted') #不会额外标出点

4.标签
  font1 = {'family':'serif','color':'blue','size':20}
  font2 = {'family':'serif','color':'darkred','size':15}

  plt.title("Sports Watch Data", fontdict = font1)
  plt.xlabel("Average Pulse", fontdict = font2)
  plt.ylabel("Calorie Burnage", fontdict = font2)

5.网格
  plt.grid()
  plt.grid(axis = 'x')  #只显示x的网格

6.多图表
  subplot()
  plt.subplot(1, 2, 1)  # 图形有 1 行，2 列，这个图表是第一个图表。

7.散点图
  scatter()
  plt.scatter(x, y, color = 'hotpink', s=sizes, alpha=0.5)  #颜色|大小|透明度

8.条形图
  plt.bar(x, y, width = 0.1)  #宽度

9.直方图
  plt.hist(x)

10.饼图
  y = np.array([35, 25, 25, 15])
  mylabels = ["Apples", "Bananas", "Cherries", "Dates"]
  mycolors = ["black", "hotpink", "b", "#4CAF50"]
  plt.pie(y, labels = mylabels, colors = mycolors)  #标签
  plt.legend()  #为每个楔形添加解释列表


Pandas 基础（读取csv）