```python
# 用于像gal那样输出文字
from colorama import init,Fore		# 导入colorama第三方库
import time		# 导入时间库
init(autoreset = True)		# 设置每次print后自动清除格式
def out(i_put):
    for ct in i_put:
        print(Fore.LIGHTWHITE_EX+ct,end='')
        time.sleep(0.1)
    time.sleep(0.4)
    print('')
```

```python
# 使用win默认程序打开图片
from PIL import Image		# 导入PIL第三方库
im=Image.open(abspath[:-len(os.path.basename(__file__))]+'example.jpg')
im.show()
```

```python
#判断字符串是否全为浮点型
def is_number(astring):
    try:
        float(astring)
    except:
        print('ValueError')
        return False
    else:
        return True
#将float改为int可判断是否为整数
```

```python
#os,sys库 笔记
a = sys.argv[0]  #获取绝对路径
name = os.path.basename(sys.argv[0])  #获取程序名称，带拓展名
path = sys.argv[0][:-len(os.path.basename(sys.argv[0]))]  #获取所在目录的绝对路径
```

```python
#解决pip下载速度慢
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple
```

### file操作

```python
open(file, mode)
'''
open(flie, mode)
函数用于打开一个文件，创建一个 file 对象，相关的方法才可以调用它进行读写。
file	文件的路径或名称
mode	字符串型参数，定义文件打开模式
		"r" - 读取，默认值。打开文件进行读取，如果文件不存在，则发生错误。
		"a" - 追加 - 打开文件进行追加，如果不存在则创建文件。
         "w" - 写入 - 打开文件进行写入，如果不存在则创建文件。
         "x" - 创建 - 创建指定的文件，如果文件存在则返回错误。
         "t" - 文本 - 默认值。文字模式。
         "b" - 二进制 - 二进制模式（例如图像）。
'''
'''
file.read([size])：size 未指定则返回整个文件，如果文件大小 >2 倍内存则有问题。
	f.read()读到文件尾时返回""(空字串)。
file.readline()：返回一行。
	file.readlines([size]) ：返回包含size行的列表, size 未指定则返回全部行。
for line in f: print line ：通过迭代器访问。
f.write("hello\n")：如果要写入字符串以外的数据,先将他转换为字符串。
f.tell()：返回一个整数,表示当前文件指针的位置(就是到文件头的字节数)。
f.seek(偏移量,[起始位置])：用来移动文件指针。
	偏移量: 单位为字节，可正可负
	起始位置: 0 - 文件头, 默认值; 1 - 当前位置; 2 - 文件尾
f.close() 关闭文件
'''
```

### OS库

```python
os.path.join()	# 路径拼接
path1 = 'user' path2 = 'desktop'
print(os.path.join(path1,path2))	# 输出user\desktop
```

```python
os.system("cmd")	#控制台指令
```

### `__repr__`与`__str__`

> `object.__repr__(self)`
> Called by the repr() built-in function to compute the “official” string representation of an object. If at all possible, this should look like a valid Python expression that could be used to recreate an object with the same value (given an appropriate environment). If this is not possible, a string of the form <...some useful description...> should be returned. The return value must be a string object. If a class defines `__repr__()` but not `__str__()`, then `__repr__()` is also used when an “informal” string representation of instances of that class is required.
> This is typically used for debugging, so it is important that the representation is information-rich and unambiguous.
>
> `object.__str__(self)`
> Called by str(object) and the built-in functions format() and print() to compute the “informal” or nicely printable string representation of an object. The return value must be a string object.
> This method differs from `object.__repr__()` in that there is no expectation that `__str__()` return a valid Python expression: a more convenient or concise representation can be used.
> The default implementation defined by the built-in type object calls `object.__repr__()`.

1. `__repr__`主要用于调试和开发，`__str__`用于为最终用户创建阅读友好的字符串。

2. `__repr__`更像是一个Python表达式，可用于重新创建具有相同值的对象（给定适当的环境）。

3. Python交互式命令行下直接输出对象默认使用 `__repr__`

   似乎还是不太清楚，举几个内置对象的例子

   ```python
   s = 'Hello World!'
   d = datetime.datetime.now()
   print(str(s)) # out: Hello World!
   print(repr(s)) # out: 'Hello World!'
   print(str(d)) # out: 2023-3-19 14:36:18.013567
   print(repr(d)) # out: datetime.dateime(2023, 3, 19, 14, 36, 18, 13567)
   ```

   
