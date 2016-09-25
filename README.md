# lab3

本节目标：

- 通过“星座计算”小程序，掌握 `JOptionPane` 的使用、字符串转换为数字、条件判断与逻辑表达式。
- 学习 Java Style Guide ，书写良好的代码风格。

## 星座计算

### 问题描述

通过 `JOptionPane` 输入一个字符串类型的日期，在命令行中输出这个日期对应的星座。

| 星座   | 起始日期          |
| ---- | ------------- |
| 魔羯座  | 12/22 - 1/19  |
| 水瓶座  | 1/20 - 2/18   |
| 双鱼座  | 2/19 - 3/20   |
| 牡羊座  | 3/21 - 4/20   |
| 金牛座  | 4/21 - 5/20   |
| 双子座  | 5/21 - 6/21   |
| 巨蟹座  | 6/22 - 7/22   |
| 狮子座  | 7/23 - 8/22   |
| 处女座  | 8/23 - 9/22   |
| 天秤座  | 9/23 - 10/22  |
| 天蝎座  | 10/23 - 11/21 |
| 射手座  | 11/22 - 12/21 |

新建一个 Java 文件，按顺序完成下面的三个部分，最终拼接成上述的小程序。

### 第 1 部分 - 判断日期对应的星座

假设我们已知年月日：

```java
int year = 1995;
int month = 7;
int day = 10;
```

然后使用 `if` 和 `else` 和逻辑表达式判断该日期对应的星座。以巨蟹座和狮子座为例：

```java
if ((month == 6 && day >= 22) || (month == 7 && day <= 22)) {
  // 这是巨蟹座 🦀 
} else if ((month == 7 && day >= 23) || (month == 8 && day <= 22)) {
  // 这是狮子座 🦁
} 
...
```

类似地，我们对每个星座分别做一次判断。

### 第 2 部分 - 字符串到整型的转换

事实上，我们从 `JOptionPane` 中读到的日期是字符串类型的。为了完成上一步中的星座判断，我们需要将这个字符串类型的日期转换成整型。

假设我们已知一个形如 `1995.07.10` 的日期字符串：

```java
String dateString = "1995.07.10";
```

我们需要将它转换成下面的形式：

```java
int year = 1995;
int month = 7;
int day = 10;
```
以年份为例，我们通过 `String` 的 `substring` 方法截取日期字符串中的年份子串。在这里，年份占了第 0 至 4 位。因此，通过如下的代码即可获得年份子串：

```java
// 这里的(0, 4)是一个前闭后开区间，即数学上的[0,4)位
String yearString = dateString.substring(0, 4); 
```

然后，我们通过 `Integer` 的 `parseInt` 方法将年份字符串转换成整型：

```java
int year = Integer.parseInt(yearString);
```

类似地，我们完成月和日的转换。

### 第 3 部分 - 输入输出

**请注意，在你的 Java 文件开头加上这行代码**，否则运行时 javac 将无法找到 `JOptionPane`。

```java
import javax.swing.*;
```

我们通过 `JOptionPane` 的 `showInputDialog` 方法弹出一个对话框，要求用户输入一个日期字符串：

```java
String dateString = JOptionPane.showInputDialog("输入日期");
```

规定输入的日期字符串形如 `YYYY.MM.DD`，如下所示：

![image](https://cloud.githubusercontent.com/assets/7262715/18815505/73bb0ca2-8366-11e6-9977-5817676280a9.png)

最后，在你第一部分完成的代码中插入下列语句输出结果：

```java
System.out.print("巨蟹座");
```
## Java Style Guide

> BY [超级厉害的何天成学长](https://github.com/htc550605125)

这篇 Guideline 主要参照于 [Google Java Style](https://google.github.io/styleguide/javaguide.html) ，截取了当中的一些内容进行翻译，更多的具体的代码规范请参见原文。良好的代码规范可以使代码更加美观易读，便于 debug 。团队协作中，统一的代码规范也是非常重要的。

### 文件编码

文件编码统一为 **UTF-8**。

### 类名

类名应当是 **UpperCamelCase**，就像这个词的写法一样，用英文单词直接连接，每个英文单词首字母大写。

### 变量名和类的方法名（class method）

变量名与方法名应当是 **lowerCamelCase**，和上面的类名类似，除了首字母小写。

### 包名（package）

Package name 为全小写的直接连接，例如：

```java
package com.example.deepspace;
```

不需要大写，不需要单词间加入其它字符。

类名与变量名方法名在单词的选择上也有一些规范，这里就不展开了，具体请参阅原文。

### 空格

在操作符两边需要一个空格：

```java
String a = "You need whitspace" + " " + "!!!"; 
```

在保留字（例如if，class）与变量名的两边需要一个空格，左大括号前与右大括号后也需要空格：

```java
if (a > b) {
  return;
} else {
  return;
}

switch (ch) {
  case 'a':
    return;
  case 'b':
    return;
  default:
    return;
}    
```

在多个参数的函数的申明与调用时，每个参数的逗号后需要一个空格：

```java
func(a, b, c);

public void func(int a, int b, String c)
```

在 **for** 语句中的分号后也需要一个空格：

```java
for (int i = 0; i < n; ++i)
```

在 **//** 的注释后需要一个空格：

```java
// don't know why it works
```

大段注释，格式参照：

```java
/*
 * This is          // And so           /* Or you can
 * okay.            // is this.          * even do this. */
 */
```

### 空行

在类的连续的成员（变量，方法等）前需要插入一个空行，例如：

```java
public class Main {
  public int flag;

  public static void main(String argv[]) {
    return;
  }

  private void func() {
    return;
  }
}
```

在不同功能的代码段之间也可以插入一个空格以提高清晰度，例如：

```java
public static void sortAndOutput(int[] arr) {
  for (int i = 0; i < arr.length; ++i) {
    for (int j = i + 1; j < arr.length; ++i) {
      if (arr[i] > arr[j]) {
        int t = arr[i];
        arr[i] = arr[j];
        arr[j] = t;
      }
    }
  }

  for (int i = 0; i < arr.length; ++i) {
    System.out.println(arr[i]);
  }
}
```

### 缩进与大括号的位置

左大括号放在行末，不单独另起一行，右大括号单独放一行。

使用空格（white space，ASCII 0x20），而非 TAB 符（ ‘\t’，ASCII 0x09）进行缩进。编辑器一般可以设置为按TAB键的时候转换为输入空格。块缩进使用两个空格，即，每出现一个新的代码块或者类似的结构（例如左大括号），缩进就要增加两个空格。例如：

```java
return new MyClass() {
  @Override public void method() {
    if (condition()) {
      try {
        something();
      } catch (ProblemException e) {
        recover();
      }
    }
  }
};
```

每一行尽量不要太长，如果一行长度超过 80 ，建议换行，换行后比较灵活，可以选择四个空格缩进，也可以选择和上一行对齐，例如：

```java
String a = "This is the first line and \n"
         + "this is the second line. \n"
         + "This is the third line.";

if (((thisIsTheFirstLine() && firstLineIsNotEmpty())
    || (thisIsTheSecondLine() && secondLineIsNotEmpty()) {
  return;
}
```
