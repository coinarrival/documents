# Python 代码规范

|版本|日期|描述|作者|
|:--:|:--:|:--:|:--:|
|v0.1|2019年5月8日|Python 代码规范|BroInBro|

## 编码

- 文件一律使用 UTF-8 编码
- 文件头部加入 `# -*- coding:utf-8 -*-` 标识

## 代码风格

### 缩进

- 统一使用**4空格**缩进
  
### 行宽

- 每行代码尽量不超过80个字符，最长不得超过120个字符

### 引号

- ***自然语言*使用双引号** `"..."`，如错误信息
- ***机器标识*使用单引号** `'...'`，如字典的键
- ***正则表达式*使用双引号** `r"..."`
- ***文档字符串*使用三个双引号** `"""..."""`
  
### 空行

- 模块函数和类定义间空两行
- 类成员函数间空一行

```python
class A:


    def __init__(self):
        pass
    
    def hello(self):
        pass
```

### import 语句

- 分行书写

  ```python
  # Bad
  import sys, os

  # Good
  import sys
  import os
  ```

- absolute import

  ```python
  # Bad
  from ..bar import Bar

  # Good
  from foo.bar import Bar
  ```

- import 语句放在文件头部，模块说明与文档字符串之后，全局变量之前

### 空格

- 双目运算符左右各空一格 `[=, -, +=, ==, >, in, is not, and]`

  ```python
  # Bad
  i=i+1
  x+=1
  y = y*2 - 1

  # Good
  i = i + 1
  x += 1
  y = y * 2 - 1
  ```
- 函数参数列表中，逗号后有空格

  ```python
  # Bad
  def func(x,y):
      pass
  
  # Good
  def func(x, y):
      pass
  ```

- 函数参数默认值等号两边不需要加空格

  ```python
  # Bad
  def func(x, y = 1):
      pass
  
  # Good
  def func(x, y=1):
      pass
  ```

- 不要使用空格对其赋值语句

  ```python
  # Bad
  x            = 1
  temp         = x + 1
  longVariable = 1234
  
  # Good
  x = 1
  temp = x + 1
  longVariable = 1234
  ```

### 换行

- 括号内换行
  - 第二行缩进到括号起始处
    ```python
    foo = longFunc(varOne, varTwo,
                   varThree, varFour)
    ```
  - 第二行缩进4个空格，适用于括号后立即换行
    ```python
    foo = longLongLongFunc(
        varOne, varTwo, varThree,
        varFour)
    ```

- `if/for/while` 一定要换行

### 注释

#### 块注释

`#` 后空一格，段落间可空行

```python
# block comment
# block comment
#
# block comment
# block comment
```

#### 行注释

至少使用2个空格和语句隔开且`#`后空一格。禁止无意义注释

```python
# Bad(无意义)
x = x + 1  # x加一

# Good
x = x + 1  # 加粗一个像素
```

#### docstring(文档字符串)

- **公共模块，函数，类，方法**都要有docstring
- docstring 首行`"""`不换行
- 除非 docstring 只有一行，末行`"""`就要换行
  
```python
def getFoobar():
    """Return a foobar"""

def max(x, y):
    """Return max value
    x and y must be same type
    """
```

##### 函数 docstring

  对函数参数、返回值等的说明采用numpy标准, 如下所示
  ```python
  def func(arg1, arg2):
    """在这里写函数的一句话总结(如: 计算平均值).

    这里是具体描述.

    Args:
    --------
    arg1 : int
        arg1的具体描述
    arg2 : int
        arg2的具体描述

    Returns:
    --------
    int
        返回值的具体描述

    Examples:
    --------
    示例使用doctest格式, 在`>>>`后的代码可以被文档测试工具作为测试用例自动运行

    >>> a=[1,2,3]
    >>> print [x + 3 for x in a]
    [4, 5, 6]
    """
  ```

### 命名规范

- 常量使用下划线分隔的大写命名
- 其余情况采用 CamelCase 命名风格

```python
MAX_SIZE = 10

def func(varOne, varTwo):
    curSize = varOne + varTwo
    return curSize
```