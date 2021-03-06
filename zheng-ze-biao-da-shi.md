# 正则表达式

## 作用

对字符串文本的操作。 检测字符串的合法性。如：电话，IP合法性。 替换字符串。 查询字符串。

## 类型

独立于编程语言的一种文本处理协议。

## 语法

### 字符串的开始和结束符号

```text
开始： ^
结束： $
```

### 字符串某个位置上的内容

#### 特殊字符

```text
\f 换页符
\n 换行符
\r 回车符
\t 制表符
```

#### 其他字符：

```text
字符集：[ ]   可能出现集合中的一个元素，属于范围的限定
字符集简写：
\d 数字字符集中的一个元素 
\D 非数字字符集中的一个元素
.  非"\n" 之外的字符集中的一个元素
\s 任意空白字符
\S 任意非空白字符
```

#### 逻辑控制

```text
^ 字符集中取非操作。[^a] 非a的字符集中的一个元素
- 字符集范围操作。 [a-z] a到z的字符集中的一个元素
| 字符取或操作。（t|w）ood  字符串为 wood 或 food
\ 转义字符
```

### 字符串位数控制

修饰前面的字符，控制前面字符出现的次数。

#### 位数控制

```text
｛3｝ 出现3次
｛3，5｝出现次数的区间，最少3次，最多5次。3次到5次之间都行。
```

#### 次数控制简写

```text
*  相当于｛0，｝
+  相当于｛1 ，｝
？ 相当于｛0，1｝
```

## 检测手机号

```text
^0?(13[0-9]|15[012356789]|18[0-9]|14[57])[0-9]{8}$
```

## 检测IP

```text
^(\d{1,2}|1\d\d|2[0-4]\d|25[0-5])\.

(\d{1,2}|1\d\d|2[0-4]\d|25[0-5])\.

(\d{1,2}|1\d\d|2[0-4]\d|25[0-5])\.

(\d{1,2}|1\d\d|2[0-4]\d|25[0-5])$
```

