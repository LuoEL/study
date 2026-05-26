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


NumPy 基础（数组、矩阵乘法、转置、求和）

Matplotlib 基础（画点、画线、显示）

Pandas 基础（读取csv）