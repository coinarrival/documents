# JavaScript 代码规范

|版本|日期|描述|作者|
|:--:|:--:|:--:|:--:|
|v0.1|2019年5月8日|JavaScript 代码规范|BroInBro|

## 代码风格

### 缩进

- 统一使用**4空格**缩进
  
### 分号

- 所有语句必须以**分号结尾**

### 行宽

- 每行代码尽量不超过80个字符，最长不得超过120个字符

### 换行

- 在优先级更高处进行换行

  ```javascript
  // Prefer
  currentEstimate =
      calc(currentEstimate + x * currentEstimate) /
          2.0f;

  // Discourage
  currentEstimate = calc(currentEstimate + x *
    currentEstimate) / 2.0f;
  ```

- 左大括号不换行
  
  ```javascript
  // Prefer
  function func() {
      // code
  }

  // Discourage
  function func()
  {
      // code
  }
  ```

### 空格

- 双目运算符左右各空一格 `[=, -, +=, ==, >, in, is not, and]`

  ```javascript
  // Prefer
  i = i + 1;
  x += 1;
  y = y * 2 - 1;

  // Discourage
  i=i+1;
  x+=1;
  y = y*2 - 1;
  ```
- 函数参数列表中，逗号后有空格

  ```javascript
  // Prefer
  function func(x, y) {
      // code
  }

  // Discourage
  function func(x,y) {
      // code
  }
  ```

- 不要使用空格进行水平对齐

  ```javascript
  // Prefer
  x = 1;
  temp = x + 1;
  longVariable = 1234;
  {
    tiny: 42,
    longer: 123
  }
  
  // Discourage
  x            = 1;
  temp         = x + 1;
  longVariable = 1234;
  {
    tiny:   42,
    longer: 123
  }
  ```

### 引号

- 统一使用单引号

  如果字符串内包含单引号，使用模板字符串
  ```javascript
  // Prefer
  let message = `This is a 'message'.`;

  // Discourage
  let message = "This is a 'message'.";
  ```

### 注释

#### 块注释

首尾 `/* */` 单行隔开，使注释更加醒目

```javascript
/*
* block comment
* block comment
*/
```

#### 行注释

至少使用2个空格和语句隔开且 `//` 后空一格。禁止无意义注释

```javascript
// Prefer
x = x + 1;  // 加粗一个像素

// Discourage(无意义)
x = x + 1;  // x加一
```

#### 函数注释

  对函数参数、返回值等的说明如下所示
  ```javascript
  /**
   * Demonstrates function's function. This one
   * returns input.
   * @param {TYPE} arg Description for arg
   * @return {TYPE} Description for return value
   */
  function func(arg) {
      return arg;
  }
  ```

### 命名规范

- 变量使用名词，函数使用动词 + 名词，命名语义化
- 常量使用下划线分隔的大写命名
- 其余情况采用 CamelCase 命名风格

```javascript
const MAX_SIZE = 10;

function func(varOne, varTwo) {
    let curSize = varOne + varTwo;
    return curSize;
}
```

### 语言特性

- 使用 `const` 和 `let`
- 变量声明独行出现
  ```javascript
  // Prefer
  let x = 1;
  let y = 2;

  // Discourage
  let x = 1, y = 2;
  ```
- 多使用箭头函数，避免 this 问题
- 多使用模板字符串，减少字符串操作