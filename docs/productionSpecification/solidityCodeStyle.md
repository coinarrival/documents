# Solidity 代码规范

|版本|日期|描述|作者|
|:--:|:--:|:--:|:--:|
|v0.1|2019年6月26日|Solidity 代码规范|快乐舔狗|

## 编码

- 文件一律使用 UTF-8 编码

## 命名

 - 合约、库、事件、枚举及结构体命名应该用大驼峰式命名法

 - 函数、参数、变量及修饰器应该用小驼峰式命名法

 - 常量应该使用全大写及下划线分割大词的方式

## 代码风格

### 缩进

- 统一使用**4空格**缩进
  
### 行宽

 - 每行不应该太长，最好在79（或99）个字符以内

 - 函数的参数应该是单独的行，且只有一个缩进

```js
thisFunctionCallIsReallyLong(
    longArgument1,
    longArgument2,
    longArgument3
);
```

### 空行

- 合约之间要有空行

```js
contract A {
    ...
}
    
    
contract B {
    ...
}
    
    
contract C {
    ...
}
```

- 函数之间应有空行

```js
contract A {
    function test1() public {
        ...
    }
    
    function test2() public {
        ...
    }
}
```

 - 没有实现的话，空行可以省去

```js
contract A {
    function test1() public;
    function test2() public;
}
```

### import 语句

 - 引入文件应该在最上方

```js
import "owned";

contract A {
    ...
}


contract B is owned {
    ...
}
```

### 函数编写规范

 - 函数的顺序：在编写函数的时候，应该让大家容易找到构造函数，回退函数，官方推荐的的函数顺序是：

    1. 构造函数

    2. 回退函数 (如果有)

    3. 外部函数（external）

    4. 公有函数(public)

    5. 内部函数(internal)

    6. 私有函数（private）

**Note:** 同一类函数时，constant函数放在后面

```js
contract A {
    // 构造函数
    function A() public {
        ...
    }

    // 回退函数
    function() public {
        ...
    }

    // 外部函数
    // ...

    // 带有constant 外部函数 
    // ...

    // 公有函数
    // ...

    // 内部函数
    // ...

    // 私有函数
    // ...
}
```