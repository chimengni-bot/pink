# Typora 基本操作

## 标题
输入 `#` 加一个空格，敲回车 → 一级标题
`##` 两个 # → 二级标题，以此类推

## 代码块
输入 ` ~~~html ` 敲回车即可
（`css`、`javascript` 同理）

> 显示代码行号：文件 → 偏好设置 → 代码块 → 显示行号 ✓

## 高亮引用
输入 `>` 符号后敲空格

## 文字样式
- 变色突出：用反引号包裹 `` `要变色的文字` ``
- 加粗：`Ctrl + B`

## 列表
输入 `-` 符号后敲空格

## 表格
菜单栏：段落 → 表格

## 截图自动存图
文件 → 偏好设置 → 图片插入 → Copy image to `./assets`
# 23.CSS 简介与样式表分类

## CSS 是什么

CSS（Cascading Style Sheets，层叠样式表），用来控制网页在浏览器中的显示外观。
CSS3 已被大部分现代浏览器支持，CSS4 仍在开发中。

## CSS 能做什么

- 样式美化
- 布局与定位
- 动画交互

## CSS 三种引入方式

| 类型 | 写法位置 | 特点 |
| --- | --- | --- |
| 内联样式表（行内） | 直接写在标签的 `style` 属性里 | HTML 和 CSS 混在一起，不推荐 |
| 内部样式表 | 写在 `<head>` 的 `<style>` 标签中 | 只控制当前页面，未完全脱离 HTML |
| 外部样式表 | 单独 `.css` 文件，用 `<link>` 引入 | 完全脱离结构，推荐使用 |

### 外部样式表引入方式

<link rel="stylesheet" href="文件路径">
外部样式表写在 <head> 标签内，格式：选择器 { 属性: 值; }

# 24. 类型选择器与注释

## 1. 选择器是什么

CSS 选择器是 CSS 规则的第一部分，用来选择要修改样式的 HTML 元素。

```css
/* 基本结构：选择器 + 属性（键值对形式） */
p {
  color: pink;
  font-size: 14px;
}
```

- **CSS 选择器**：选择目标标签
- **CSS 属性**：修改该标签的样式

---

## 2. 选择器分类

根据使用场景不同，选择器分为以下类型：

| 类型 | 说明 |
| --- | --- |
| 基础选择器 | 由单个选择器组成 |
| 关系选择器 | 根据元素层级关系选择 |
| 分组选择器 | 多个选择器合并书写 |
| 伪类和伪元素 | 选择特定状态或结构位置 |
| 属性选择器 | 根据属性或属性值选择 |

### 基础选择器包括

- 类型选择器
- 类选择器
- id 选择器
- 通配符选择器

---

## 3. 类型选择器

也叫**标签选择器 / 元素选择器**，选择页面中所有该类型的标签。

```css
/* 选择所有 div */
div {
  color: gold;
}

/* 选择所有 span */
span {
  color: green;
}
```

> 同名选择器有多条规则时，**后写的覆盖先写的**（就近原则 / 层叠性）。

### CSS 书写规范

1. 选择器与 `{` 之间保留 **1 个空格**
2. 属性名与属性值之间保留 **1 个空格**
3. 每个属性**单独占一行**

---

## 4. 注释

```css
/* 这里添加注释 */
```

> 快捷键：`Ctrl + /`
# 25. 类选择器

## 1.什么是类选择器

选择 1 个或多个元素，**优先级高于类型选择器**。

---

## 2.语法

```css
/* CSS：.类名 { 样式声明; } */
.pink {
  color: pink;
}
```

```html
<!-- HTML：<标签 class="类名"> -->
<ul>
  <li>猪爸爸</li>
  <li>猪妈妈</li>
  <li>乔治</li>
  <li class="pink">佩奇</li>
</ul>
```

---

## 3.注意事项

- 类名不能用**中文**，不能是**纯数字**
- 多个英文单词用 `-` 连接，如 `box-title`
- 一个标签可以有**多个类名**，中间用**空格**隔开

```html
<div class="box pink large">内容</div>
```
# 26. id 选择器与通配符选择器

## 1. id 选择器

选择 HTML 中具有特定 id 属性的唯一元素。

```css
/* CSS：#id名 { 样式声明; } */
#header {
  color: red;
}
```

```html
<!-- HTML：<标签 id="id名"> -->
<div id="header">修改样式</div>
```

- 同一页面中 id **唯一**，不能重复使用
- 主要作用：配合 JS 实现交互效果

---

## 2. 通配符选择器

选择 HTML 中**所有**标签，进行统一样式修改。

```css
* {
  margin: 0;      /* 去除所有元素的外边距 */
  padding: 0;     /* 去除所有元素的内边距 */
  box-sizing: border-box; /* 统一盒模型 */
}
```

> 特殊情况下用通配符清除所有元素的默认边距和填充，统一不同浏览器的默认样式。

---

## 3. 基础选择器总结

大部分情况下，我们使用**类选择器**。

| 选择器类型 | 语法示例 | 匹配范围 | 复用性 | 典型使用场景 | 注意事项 |
| --- | --- | --- | --- | --- | --- |
| 类型选择器 | `div { }` | 所有指定 HTML 标签元素 | 某一类型标签 | 全局样式重置、基础标签样式（如 body、p） | 避免滥用，可能导致样式冲突 |
| 类选择器 | `.nav { }` | 所有含指定 class 的元素 | 多次使用 | 多元素共享样式 | 优先使用，避免与 id 选择器冲突 |
| id 选择器 | `#header { }` | 匹配唯一含指定 id 的元素 | 唯一性 | 唯一元素标识 | 必须唯一，避免样式覆盖风险 |
| 通配符选择器 | `* { }` | 匹配所有元素 | 全局覆盖 | 全局样式重置 | 性能较差，慎用 |

# 27.画盒子案例-网页基本布局
类选择器，多类用空格隔开，通配符选择器去除浏览器边距

# 28. 关系选择器

关系选择器通过**位置关系**来选择目标元素，可以更精准地选择某些元素。

| 选择器 | 语法 | 说明 |
| --- | --- | --- |
| 后代选择器 | `.box p { }` | 选择所有后代（不限层级） |
| 子代选择器 | `.box>p { }` | 只选直接子元素（仅限一层） |
| 邻接兄弟选择器 | `h2+p { }` | 只选紧邻的下一个兄弟 |
| 通用兄弟选择器 | `h2~p { }` | 选后面所有同级兄弟 |

---

## 1. 后代选择器

选择某个元素的后代元素（不限层级，包括子元素、孙元素等）。

```css
/* 选择 div 里面所有的 p，中间用空格隔开 */
div p {
  color: pink;
}
```

```html
<div>
  <p>我是文字</p>   <!-- ✅ 被选中 -->
</div>
<p>我是文字</p>     <!-- ❌ 不被选中 -->
```

> - 父级 div 作用是限定范围，子元素 p 修改样式
> - 父级和子集都可以是任意选择器

---

## 2. 子代选择器

选择某个元素的**直接子元素**（仅限一层）。

```css
/* 选择 div 的直接子 span，用 > 隔开 */
div > span {
  color: pink;
}
```

```html
<div>
  <span>我是儿子</span>   <!-- ✅ 被选中 -->
  <p>
    <span>我是孙子</span> <!-- ❌ 不被选中 -->
  </p>
</div>
```

# 29. 关系选择器之兄弟选择器

## 1. 兄弟选择器

### 邻接兄弟选择器

只选紧跟在目标元素后面的**第一个**同级元素。

```css
h2 + p {
  color: pink;
}
```

### 通用兄弟选择器

选中目标元素后面的**所有**同级元素。

```css
h2 ~ p {
  color: pink;
}
```

---

## 2. 关系选择器总结

| 选择器 | 语法 | 选择范围 | 实例 |
| --- | --- | --- | --- |
| 后代选择器 | `A B` | 所有后代（跨层级） | `ul li { color: pink; }` |
| 子代选择器 | `A > B` | 直接子元素（仅一层） | `div>span { color: pink; }` |
| 邻接兄弟选择器 | `A + B` | 紧邻的下一个同级元素 | `h2+p {}` 标题后的第一个 p 元素 |
| 通用兄弟选择器 | `A ~ B` | A 之后的所有同级元素 | `h2~p {}` 标题后的所有 p 元素 |

# 30.综合案例-登高千古第一绝句

- 视频封面：poster ；
- 距两侧边距：padding；

# 31.字体样式-颜色、字体族、倾斜、加粗和装饰

## 字体样式

|    字体样式     |     说明     |
| :-------------: | :----------: |
|      color      | 设置字体颜色 |
|   font-family   |    字体族    |
|    font-size    |   字体大小   |
|   font-style    |   字体风格   |
|   font-weight   |   字体粗体   |
| text-decoration |   字体装饰   |

### 字体颜色 color

- 关键字 red、green、blue、pink...内置的颜色块

- 十六进制 #ffffff

- .rgb格式 p{color:rgb(255,0,0,0.3)} 透明值0～1，0完全透明，1完全不透明

### 字体族 font-family

给定一个有先后顺序的，由字体名或字体族名组成的列表来设置字体（从前到后生效）

一般指定给body标签，用逗号隔开

网页建议无衬线字体，宽度都一样

### 字体大小 font-size

比如：p{font-size=18px；} 

简写：fz18，不要忘记给单位

### 字体风格 font-style

用来打开和关闭文本italic(斜体)，通常用来改em和i标签

- normal：普通字体
- italic：倾斜字体

### 字体粗体 font-weight

html里的strong也可以加粗

可以设置和取消加粗，比如h都加粗可以取消

部分大批量文字可以利用css加粗

1.属性值

- normal：正常粗细
- bold：加粗

2.数字属性值（常用）

- 400:正常粗细
- 700:加粗
- 100～900数值都可以

### 字体装饰

最常见的有**下划线**、删除线

- none：取消文本装饰
- underline：下划线
- overline：上划线
- line-through：穿过文本的线

## 字体常用属性总览

| 属性 | 描述 | 常见取值 | 示例 |
| --- | --- | --- | --- |
| `color` | 设置文本内容的颜色 | 颜色名称（red, blue）<br>十六进制（#ff0000）<br>RGB（rgb(255,0,0)）<br>RGBA（rgba(255,0,0,0.5)） | `color: red;`<br>`color: #3366cc;` |
| `font-family` | 设置文本的字体系列 | 无衬线字体 | `font-family: "Microsoft YaHei", sans-serif;` |
| `font-size` | 设置文本的大小 | px | `font-size: 16px;` |
| `font-style` | 设置文本的样式 | normal（正常）、italic（斜体） | `font-style: normal;` |
| `font-weight` | 设置文本的粗细 | 数值（100-900）、关键字（normal, bold） | `font-weight: 400;`<br>`font-weight: 700;` |
| `text-decoration` | 设置文本的装饰效果 | none（无装饰）<br>underline（下划线）<br>overline（上划线）<br>line-through（中划线） | `text-decoration: underline;`<br>`text-decoration: line-through;` |

# 32. 文本布局-对齐、缩进、间距和行高

## 1. 文本对齐 text-align

控制文本在它所在的块级盒子内如何水平对齐。

**使用场景：**
- 文本 / 图片在盒子内水平对齐
- 文章文字两端对齐（如腾讯体育）

| 属性值 | 说明 |
| --- | --- |
| `left` | 文本左对齐（默认） |
| `right` | 文本右对齐 |
| `center` | 文本水平居中对齐 |
| `justify` | 自动改变字间距，两端对齐 |

```css
p {
  text-align: center;
}
```

---

## 2. 文本布局

### 2.1 首行缩进 text-indent

设置块级元素中文本行前空格（缩进）的长度。

- 单位为 `em`（1em = 1字符）
- 也可以用 `px`（20px = 20像素）

```css
p {
  text-indent: 2em;
}
```

---

### 2.2 字间距 letter-spacing

用于设置文本字符的间距，支持正值和负值。

```css
p {
  letter-spacing: 2px;
}
```

---

### 2.3 行高 line-height

1. 设置多文本之间的上下间距
2. 让单行文本垂直居中
3. 行高等于盒子高度，则单行文字垂直居中（行高即上下间距）

属性值：数字 `px` 或数字不带单位（当前字体大小的倍数）

```css
p {
  line-height: 1.5;
}
```
# 33. font 简写与 CSS 继承性

## 1. font 简写

font 简写属性在一个声明中设置多个字体属性。

**语法顺序（不能颠倒）：**

```css
/* font: font-style font-weight font-size/line-height font-family; */
p {
  font: italic 700 16px/1.5 "宋体";
}
```

> - `font-size` 和 `font-family` **必须写**
> - 其他可以省略，默认显示

---

## 2. CSS 的继承性

子元素自动继承父元素的某些 CSS 样式属性。

- 主要继承**文字相关**的样式属性，比如字体、颜色、文本对齐
- 子元素定义自己的样式时，**优先使用自己的样式**

```css
body {
  font-size: 16px;
  color: #333;
  font-family: "微软雅黑";
}
/* 页面内所有文字默认继承以上样式 */
```

---

# 34. Xmind 梳理知识体系（脑图）

- `Tab` 键：创建下一级
- `Enter` 键：创建同一级

# 35. 分组选择器和链接伪类选择器

## 1. 分组选择器（并级选择器）

将不同的选择器组合在一起，使用逗号分割另起一行。

**使用场景：** 多个元素具备相同样式。

```css
div,
span {
  color: pink;
}
```

---

## 2. 伪类选择器

选择元素的特定状态和结构位置，符号为冒号 `:`。

> `.nav` 是类，`:nav` 是伪类

| 类型 | 说明 | 示例 |
| --- | --- | --- |
| 状态伪类 | 根据用户交互或状态变化选择 | 鼠标经过链接、表单获得焦点等 |
| 结构伪类 | 根据元素的位置选择 | 选第5个、第10个元素，选前3个元素等 |
| 表单伪类 | 针对表单元素的状态 | 表单禁用、选中复选框等 |

---

### 2.1 链接伪类

链接伪类用于根据链接（访问、悬停、点击等）不同状态为其添加样式。

**顺序规则（LVHA）：**

```
a:link -> a:visited -> a:hover -> a:active
```

| 链接伪类 | 作用 |
| --- | --- |
| `a:link` | 未访问链接的默认样式 |
| `a:visited` | 已访问链接的样式 |
| `a:hover` | 鼠标悬停在链接上时的反馈 |
| `a:active` | 链接被点击时的瞬时状态（按下到松开） |

```css
a:link    { color: blue; }
a:visited { color: purple; }
a:hover   { color: red; }
a:active  { color: orange; }
```

> **调试技巧：** 在浏览器开发者工具中，右键元素 → `Force state` → 选择对应伪类，可强制显示伪类样式。

# 36. 用户行为伪类 - hover 和 focus

状态伪类选择器

## 1. 用户行为伪类

用户以某种方式和文档交互时应用，也叫**动态伪类**。

**使用场景：**
1. 鼠标经过元素时，修改样式
2. 表单获得焦点时

| 伪类 | 说明 |
| --- | --- |
| `:hover` | 鼠标经过元素 |
| `:focus` | 获得焦点的元素 / 表单 |

```css
/* 鼠标悬停修改样式 */
a:hover {
  color: red;
}

/* 表单获得焦点 */
input:focus {
  border-color: blue;
}
```
# 37. 结构伪类选择器与表格隔行变色

## 1. 结构伪类选择器

根据元素的位置选择目标元素。

**使用场景：** 选择第1个、最后一个或者第n个元素。

| 结构伪类 | 作用 |
| --- | --- |
| `:first-child` | 一组兄弟元素中的第一个元素 |
| `:last-child` | 一组兄弟元素中的最后一个元素 |
| `:nth-child(n)` | 一组兄弟元素列表中第n个元素 |

```css
ul li:first-child { color: pink; }   /* 第一个 li */
ul li:nth-child(2) { color: blue; }  /* 第二个 li */
ul li:last-child { color: green; }   /* 最后一个 li */
```

### nth-child(n) 的 n 取值

| 类型 | 写法 | 说明 |
| --- | --- | --- |
| 数字 | `:nth-child(3)` | 从1开始，选第3个 |
| 关键字 | `:nth-child(odd)` | 奇数行 |
| 关键字 | `:nth-child(even)` | 偶数行 |
| 公式 | `:nth-child(3n)` | 3的倍数，第3、6、9...个元素 |
| 公式 | `:nth-child(n+2)` | 第2个以及以后的元素 |
| 公式 | `:nth-child(-n+3)` | 前面3个元素 |

> 注意：公式中 n 的取值从 **0** 开始计算。

---

## 2. 表格隔行变色（斑马纹）

```css
/* 合并表格边框线 */
table {
  border-collapse: collapse;
}

/* 偶数行变色 */
tr:nth-child(even) {
  background-color: #f5f5f5;
}

/* 奇数行变色 */
tr:nth-child(odd) {
  background-color: #fff;
}
```

# 38. 表单选择器与伪元素选择器

## 1. 表单选择器

针对表单元素的状态。

| 表单伪类 | 作用 |
| --- | --- |
| `:disabled` | 表单禁用 |
| `:checked` | 选中状态，单选复选按钮 |

```css
input:disabled { opacity: 0.4; }        /* 禁用时透明度40% */
input:checked  { outline: 2px solid blue; }
```

---

## 2. 伪元素选择器

选择元素的特定部分，使用双冒号 `::`。

> `.nav` 类选择器　`:hover` 伪类选择器　`::before` 伪元素选择器

### 选择特定部分

| 伪元素选择器 | 作用 |
| --- | --- |
| `::first-line` | 选择首行 |
| `::first-letter` | 首字母 |
| `::placeholder` | 选择 input 或 textarea 占位符 |

### 插入内容

| 伪元素选择器 | 作用 |
| --- | --- |
| `::before` | 元素内插入元素，作为第一个元素 |
| `::after` | 元素内插入元素，作为最后一个元素 |

```css
div::before {
  content: "开始";
  color: red;
}

div::after {
  content: "结束";
  color: red;
}
```

> - `before` 和 `after` 是插入的**伪元素**，特性类似内联元素
> - `content` 属性**必须写**，没有内容空引号即可
> - 后期常用于小图标、各种装饰效果

---

# 39. 属性选择器

**使用场景：** 表单样式控制、图标字体控制、国际化语言适配等

| 属性选择器 | 作用 |
| --- | --- |
| `[属性]` | 匹配包含指定属性的元素 |
| `[属性=值]` | 匹配属性值**等于**指定值的元素 |
| `[属性^=值]` | 匹配属性值以指定字符**开头**的元素 |
| `[属性$=值]` | 匹配属性值以指定字符**结尾**的元素 |
| `[属性*=值]` | 匹配属性值**包含**某些字符串的元素 |

```css
[type="checkbox"] { box-sizing: border-box; }
[type="search"]   { webkit-appearance: textfield; }
[class*="iconfont"] { font-family: iconfont !important; }
[lang="en"] { font-family: "Times New Roman", serif; }
```

> 类名值不能以纯数字结尾，至少有一个英文字母。

---

# 40. CSS 三大特性 - 优先级

1. **继承性**（子继承父）
2. **层叠性**（权重相同，后面覆盖前面）
3. **优先级**（选择器的权重）

**原则：**
1. 优先级相等时，CSS 中**最后**的那个声明将被应用（层叠遵循就近原则）
2. 其余判断哪个选择器权重高，优先执行那个样式
3. 权重是4位一组，是分开的层级，**不能进位**

| 选择器类型 | 示例 | 权重值 |
| --- | --- | --- |
| `!important` | `color: red !important;` | 无限大 |
| 内联样式 | `<div style="color:red">` | (1,0,0,0) |
| ID 选择器 | `#myId` | (0,1,0,0) |
| 类 / 属性 / 伪类 | `.class`、`[type="text"]` | (0,0,1,0) |
| 类型（标签）/ 伪元素 | `div`、`::after` | (0,0,0,1) |
| 通配符 / 继承 | `*`、继承的样式 | (0,0,0,0) |

> - 权重**叠加即相加**
> - `!important` 最大，可以在锁死的权重里加
> - 继承的权重为 **0**
> - `h` 标签和链接 `a` 有浏览器默认样式，不能用继承控制，只能自己写样式

---

# 41. 盒子模型 - 组成与边框 border

## 盒子模型组成

所有元素都被一个个"盒子"包围，CSS 盒模型整体适用于**区块盒子**，包含四部分：

| 部分 | 说明 |
| --- | --- |
| 盒子内容 | 显示内容的区域，由内容或指定宽高决定大小 |
| 内边距 padding | 内容距边框之间的距离 |
| 边框 border | 边框包住内容和内边距 |
| 外边距 margin | 该盒子与其他元素之间的距离 |

### 区块盒子（block）vs 行内盒子（inline）

| | 区块盒子 | 行内盒子 |
| --- | --- | --- |
| 换行 | 会产生换行 | 不会产生换行 |
| 宽高 | width/height 可以作用 | width/height 不起作用 |
| 默认宽度 | 父元素空间的100% | — |
| 垂直边距 | 内边距、外边距和边框撑大元素 | 垂直方向内边距、外边距不起效果 |
| 水平边距 | — | 水平方向内边距、外边距会有效果 |
| 常见标签 | div、p、h、ul、table 等 | span、em、a、strong 等 |

---

## 边框 border

```css
/* 连写：边框粗细 边框样式 边框颜色（中间必须空格隔开） */
border: 1px solid #f1f1f1;

/* 单边设置 */
border-top:    1px solid pink;
border-bottom: 1px solid pink;
border-left:   1px solid pink;
border-right:  1px solid pink;
```

| 边框样式 | 描述 | 视觉效果 |
| --- | --- | --- |
| `dotted` | 点状边框 | 圆点组成的虚线 |
| `dashed` | 虚线边框 | 短线组成的虚线 |
| `solid` | 实线边框 | 单一线条 |
| `double` | 双实线 | 两条线 |

> `Alt + 上下箭头` = 移动代码行

---

# 42. 盒子模型 - 圆角边框 border-radius

```css
border-radius: 50%;   /* 圆形 */
border-radius: 20px;  /* 圆角 */
```

> **胶囊按钮：** 圆角设置为高度的一半即可实现
> `img` 也可以直接设置圆角

### 多值写法（顺时针：左上角 → 右上角 → 右下角 → 左下角）

| 写法 | 作用 |
| --- | --- |
| `border-radius: 10px;` | 四角相同 |
| `border-radius: 10px 20px;` | 左上/右下是10px，右上/左下是20px |
| `border-radius: 10px 20px 30px;` | 左上10px，右上/左下20px，右下30px |
| `border-radius: 10px 20px 30px 40px;` | 左上10px，右上20px，右下30px，左下40px |

> - 顺时针记忆
> - 多个值中间用**空格**隔开
> - 不需要圆角的设置为 `0` 即可

---

# 43. 盒子模型 - 内边距 padding

控制边框和内容区域之间距离。

```css
padding: 10px;              /* 上下左右都是10px */
padding: 10px 20px;         /* 上下10px，左右20px */
padding: 10px 20px 30px;    /* 上10px，左右20px，下30px */
padding: 10px 20px 30px 40px; /* 上10px，右20px，下30px，左40px（顺时针） */

/* 单边设置 */
padding-left: 10px;
padding-right: 10px;
padding-top: 10px;
padding-bottom: 10px;
```

---

# 44. 盒子模型 - 外边距 margin、居中对齐、折叠与塌陷

## 1. 外边距 margin

```css
margin: 10px;
margin: 10px 20px;
margin: 10px 20px 30px;
margin: 10px 20px 30px 40px; /* 上右下左（顺时针） */

/* 单边设置 */
margin-left: 10px;
margin-right: 10px;
margin-top: 10px;
margin-bottom: 10px;
```

> - 行内元素**左右**外边距生效，**上下外边距无效**
> - 行内元素设置**宽高也无效**

---

## 2. 居中对齐

区块元素可以利用 `margin` 实现**水平居中**：

- 块级盒子必须有**宽度**
- 只需设置**左右外边距为 auto**

```css
/* 常见写法 */
.container {
  width: 1226px;
  margin-left: auto;
  margin-right: auto;
}

/* 简写 */
.w {
  margin: 0 auto;
  width: 1296px;
}
```

---

## 3. 外边距折叠

**触发条件：** 并列关系（兄弟）的区块元素，上下外边距相邻时会折叠合并。

- 两个上下外边距将合并为一个，大小等于**最大**的单个外边距

```css
.boxA { margin-bottom: 100px; }
.boxB { margin-top: 50px; }
/* 实际间距为 100px，不是150px */
```

> 这是浏览器特性，只需设置**一个盒子外边距**即可。

---

## 4. 外边距塌陷

**触发条件：** 嵌套关系（父子）的区块元素，给子盒子设置上下外边距会让父盒子塌陷移动。

**解决方案：**
1. 给父盒子添加**上边框**（父盒子本身有边框则不会出现问题）
2. 给父盒子添加**上内边距**（同理）
3. 给父盒子添加 `overflow: hidden;` 属性

---

# 45. 盒子模型 - 尺寸计算 box-sizing

除了宽度和高度增加盒子大小之外，`padding` 和 `border` 都会让盒子变大。

```css
/* 默认：width = 内容宽度，加 padding/border 后盒子变大 */
div { box-sizing: content-box; }

/* 推荐：width = 整体宽度，padding/border 向内压缩，不撑大盒子 */
div { box-sizing: border-box; }
```

# 46. 盒子模型 - 背景 background 常见属性

background 用于设置元素背景相关属性，包括背景颜色、背景图片、背景位置、背景重复方式等。

| 属性 | 作用 | 常用值 | 示例代码 |
| --- | --- | --- | --- |
| `background-color` | 设置元素背景颜色 | 颜色名称、十六进制、RGB、透明度 | `background-color: #f0f0f0;` |
| `background-image` | 设置背景图片 | `url(image.jpg)` | `background-image: url(bg.png);` |
| `background-repeat` | 控制背景图片是否重复 | `repeat`（默认）、`no-repeat`、`repeat-x`、`repeat-y` | `background-repeat: no-repeat;` |
| `background-position` | 定位背景图片位置 | x y（如 center top，或者 px、% 单位） | `background-position: center;` |
| `background-size` | 调整背景图片尺寸 | 默认 `auto`、`cover`（覆盖）、`contain`（包含）、px、% | `background-size: cover;` |
| `background-attachment` | 背景是否随页面滚动 | `scroll`（默认）、`fixed` | `background-attachment: fixed;` |

> - `background-image: url(路径)`
> - `repeat` 默认是重复的
> - 方位名词：`left`、`right`、`top`、`bottom`、`center`

---

# 47. 盒子模型 - 背景复合写法与视差滚动

## 1. 背景复合写法

```css
/* 无顺序规则 */
background: pink url(./img/bg.png) no-repeat center center;
```

> `background-attachment: fixed` — 相对于当前视口固定，用于实现视差滚动效果。

---

# 48. 盒子模型 - 背景渐变与文字渐变

## 1. 背景渐变

### 线性渐变 linear-gradient

方向可以是方位名词，也可以是 `deg`（角度），位置和色标的位置不是必须的。

```css
/* 从左到右 */
background: linear-gradient(to right, #ff6b6b, #4ecdc4);

/* 指定角度 */
background: linear-gradient(90deg, pink 0%, red 100%);

/* 多色节点 */
background-image: linear-gradient(90deg, #ff6b6b 30%, #4ecdc4 70%);
```

### 径向渐变 radial-gradient

形状和位置可控。

```css
background: radial-gradient(circle, #ff9a9e, #fad0c4);
```

| 属性/方法 | 描述 | 示例代码 |
| --- | --- | --- |
| `linear-gradient(方向, 颜色1 位置, 颜色2 位置...)` | 线性渐变（方向可控） | `linear-gradient(to right, #ff6b6b, #4ecdc4)` |
| `radial-gradient(形状, 颜色1, 颜色2...)` | 径向渐变（形状和位置可控） | `radial-gradient(circle, #ff9a9e, #fad0c4)` |

> **使用技巧：** 实际开发中 UI 设计稿可以直接复制代码，也可以利用 trae 图片自动生成。

---

## 2. 文字渐变

```css
p {
  background: linear-gradient(90deg, pink, red);
  -webkit-background-clip: text;  /* 背景裁剪，以文字的形式裁剪 */
  background-clip: text;
  -webkit-text-fill-color: transparent; /* 文本填充颜色为透明 */
}
```

> `-webkit-` 前缀是谷歌浏览器老版本的兼容性写法。

---

# 49. 盒子模型 - 阴影、过渡和初始化

## 1. 阴影 box-shadow

```css
/* x偏移  y偏移  模糊距离  扩散距离  阴影颜色 */
div {
  box-shadow: 4px 4px 10px 0 rgba(0, 0, 0, 0.2);
}
```

---

## 2. 过渡 transition

过渡效果用于元素的属性值发生变化时，**平滑地过渡**（而不是瞬间切换）。

**使用场景：**
1. 鼠标经过图片放大
2. 表单获得焦点，输入框变宽

```css
/* 语法：过渡属性 过渡时间（单位秒s） */
div {
  transition: all 0.3s;   /* all = 所有效果都过渡 */
  transition: width 0.3s, color 0.2s; /* 指定属性 */
}

input:hover {
  transition: all 0.3s;
}
```

> - 属性值中间**空格**隔开
> - 过渡属性如果都要变化可以写 `all`
> - 过渡时间单位是**秒 s**，比如 `0.2s`

---

## 3. 初始化

- 统一浏览器默认样式，消除差异
- 减少后续开发中的冗余代码
- 提高代码可维护性

```css
/* 中大型项目：推荐引入 Normalize.css */
<link rel="stylesheet" href="./css/Normalize.css">
```

---

# 50. 溢出显示省略号

## 单行文字溢出

```css
p {
  overflow: hidden;           /* 溢出隐藏 */
  text-overflow: ellipsis;    /* 文本溢出显示省略号 */
  white-space: nowrap;        /* 强制文字一行显示，不换行 */
}
```

## 多行文字溢出

```css
p {
  display: -webkit-box;           /* 旧版弹性盒子布局 */
  -webkit-box-orient: vertical;   /* 文本垂直排列 */
  -webkit-line-clamp: 3;          /* 限制显示行数 */
  overflow: hidden;               /* 隐藏溢出内容 */
  text-overflow: ellipsis;        /* 文本溢出显示省略号 */
}
```

> 多行文本溢出显示省略号：修改盒子高度为**正好显示行数的高度**。

---

# 52. 字体图标 iconfont

字体图标是一种将图标以文字形式嵌入网页的技术，允许开发者像使用文字一样通过 CSS 控制图标的样式（如颜色、大小、阴影等）。

## 优点

- **矢量缩放**：无损放大缩小
- **减少 http 请求**：一个字体图标文件可包含多个图标，比多张图片更高效
- **兼容性好**：支持所有现代浏览器，甚至部分旧版浏览器

## 使用步骤

1. 在 iconfont.cn 选好图标，下载压缩包
2. 用 `<link>` 方式引入 CSS 文件

```html
<link rel="stylesheet" href="./iconfont/iconfont.css">
```

3. 使用 `<i>` 标签调用

```html
<i class="iconfont icon-xxx"></i>
```

> - `<i></i>` 常用于写字体图标
> - icon 的 CSS 包里面有类选择器的权重
> - 命名规则第一个词**必须是 iconfont**

---

# 54. CSS 精灵技术（background-position）

CSS Sprites 把多个小图标或图像合并到一张大图中，通过调整 `background-position` 属性来显示特定部分的图像技术。

```css
.icon-home {
  width: 20px;
  height: 20px;
  background: url(./sprites.png) no-repeat -40px -60px;
}
```

## 优点

- 减少 http 请求，只需请求一次
- 提升性能
- 统一管理

> 复杂的彩色小图标更适合**精灵图**，简单的单色图标更适合**字体图标**。

# 58. 弹性盒布局 - 主轴和交叉轴对齐

## 1. justify-content 定义主轴上的对齐方式

| 属性值 | 效果 | 示例 |
| --- | --- | --- |
| `flex-start` | 左对齐（默认） | 子元素靠左排列 |
| `flex-end` | 右对齐 | 子元素靠右排列 |
| `center` | 居中对齐 | 子元素居中 |
| `space-between` | 两端对齐 | 首个子元素放置于起点，末尾元素放置于终点 |
| `space-around` | 项目两侧间隔相等 | 每个子元素周围分配相同的空间 |
| `space-evenly` | 项目间隔均匀分布 | 每个子元素之间的间隔相等 |

```css
.container {
  display: flex;
  justify-content: space-between;
}
```

---

## 2. align-items 定义交叉轴上的对齐方式（单行整体对齐）

| 属性值 | 作用描述 |
| --- | --- |
| `flex-start` | 项目在交叉轴起点对齐（默认值） |
| `flex-end` | 项目在交叉轴终点对齐 |
| `center` | 项目在交叉轴居中对齐 |
| `stretch` | 项目拉伸填充整个容器高度（子项目无固定高度） |

```css
.container {
  display: flex;
  align-items: center;
}
```

---

# 59. 弹性盒布局 - 改变主轴方向 flex-direction

`flex-direction` 定义主轴方向（改变主轴方向）。

> `a` 如果给了 flex 布局，则可以直接给宽度和高度。

| 属性值 | 描述 | 示例效果 |
| --- | --- | --- |
| `row` | 默认，子元素水平主轴（从左到右）排列 | A B C（横向排列） |
| `row-reverse` | 子元素沿水平主轴反向排列（从右到左） | C B A（反向横向排列） |
| `column` | 子元素沿垂直主轴（从上到下）排列 | A / B / C（纵向排列） |
| `column-reverse` | 子元素沿垂直主轴反向排列（从下到上） | C / B / A（反向纵向排列） |

```css
.container {
  display: flex;
  flex-direction: column;
}
```

---

# 60. 弹性盒布局 - 换行 wrap 以及多行交叉轴对齐

## 1. flex-wrap 控制是否换行

| 属性值 | 排列效果 |
| --- | --- |
| `nowrap` | 不换行，全部横向排列（可能被压缩） |
| `wrap` | 换行，第一行在上方，第二行在下方 |
| `wrap-reverse` | 翻转，第一行在下方，第二行在上方（了解即可） |

```css
.container {
  display: flex;
  flex-wrap: wrap;
}
```

---

## 2. align-content 定义多行时交叉轴的对齐方式

> 仅当 `flex-wrap: wrap` 且内容换行时生效。

| 属性值 | 效果 | 示例 |
| --- | --- | --- |
| `flex-start` | 上对齐 | 子元素靠上排列 |
| `flex-end` | 下对齐 | 子元素靠下排列 |
| `center` | 居中对齐 | 子元素居中 |
| `space-between` | 两端对齐 | 首个子元素放置于起点，末尾元素放置于终点 |
| `space-around` | 项目两侧间隔相等 | 每个子元素周围分配相同的空间 |
| `space-evenly` | 项目间隔均匀分布 | 每个子元素之间的间隔相等 |

---

# 61. 弹性盒布局 - 子项目 flex 伸缩以及 gap 间距

## 1. 项目（子盒子）属性

子元素的属性用于控制自身的尺寸、顺序或对齐方式。

- `flex: 1` — 剩余空间占 1 份，并且可以伸缩盒子大小
- 数字表示剩余空间所占份数，正整数
- 优先级比 `width` 和 `height` 高

| 属性 | 作用 | 示例 |
| --- | --- | --- |
| `flex-grow` | 定义子元素剩余空间分配**放大**比例（默认 0，即不放大） | `.item { flex-grow: 1; }` |
| `flex-shrink` | 定义子元素剩余空间分配**缩小**比例（默认 1，空间不足等比缩小，0 为不缩小） | `.item { flex-shrink: 0; }` |
| `flex-basis` | 定义项目在主轴方向上的**初始大小**（默认 auto，优先级高于 width/height） | `.item { flex-basis: 200px; }` |
| `flex` | flex-grow、flex-shrink、flex-basis 的简写 | `.item { flex: 1; }` |
| `align-self` | 覆盖容器的 align-items，单独定义某一项目的交叉轴对齐方式 | `.item { align-self: center; }` |
| `order` | 定义项目的排列顺序，数值越小越靠前 | `.item { order: -1; }` |

```css
/* flex 简写 */
.item { flex: 1; }   /* = flex: 1 1 0（等比放大/收缩，初始无基准尺寸） */
.item { flex: 2; }   /* = flex: 2 1 0（等比放大/收缩，初始无基准尺寸） */
```

---

## 2. gap 间距

`gap` 简写属性用于设置行与列之间的间隔（间距）。

```css
gap: 20px;        /* 行和列之间保持 20 像素间隙 */
gap: 20px 30px;   /* 行间距是 20 像素，列间距是 30 像素 */
```

> **注意：** `gap` 写到**父元素（容器）**身上。

# 62.弹性盒布局-淘宝京东多行伸缩布局
min-width：calc(16.66666% - 16px)

# 63.弹性盒布局-瀑布流百度图片综合案例
## 垂直对齐-解决图片底部空白缝隙问题
垂直对齐 vertical-align - 解决图片底部空白缝隙问题

### 基线概念

浏览器**行内元素**（行内块元素）排版中存在用于对齐的基线（baseline）。

图片默认和文字**基线对齐**，导致图片底部出现空白缝隙。

文字的四条线：
- 顶线（top）
- 中线（middle）
- **基线（baseline）** ← 默认对齐这里
- 底线（bottom）

---

### 解决方案

**方法1：** 把图片转换为**块级元素**

```css
img {
  display: block;
}
```

**方法2：** 设置图片对齐方式**不是基线对齐**即可（垂直利器）

```css
img {
  vertical-align: top;
}
```

---

### vertical-align 属性值

| 属性值 | 效果 |
| --- | --- |
| `baseline` | 默认，基线对齐 |
| `top` | 顶部对齐 |
| `middle` | 中部对齐 |
| `bottom` | 底部对齐 |

# 64-76.小兔鲜项目
## 准备工作

### 项目目录结构

| 文件/文件夹 | 说明 |
|---|---|
| css/base.css | 初始化css文件，方便后期其他文件引用 |
| css/common.css | 公共css文件，方便后期其他文件引用 |
| css/index.css | 首页css文件 |
| iconfont/ | 字体图标 |
| images/ | 背景小图片，比如精灵图、logo等 |
| uploads/ | 产品类图片，后期更换方便存放 |
| favicon.ico | 网页favicon图标 |
| index.html | 首页html文件 |
## header
### logo（让搜索引擎更好的收录网站）
- 给用h1来提高权重
- 里面包含链接，可以点击跳转首页
- 给链接的背景图片，并且给链接添加tittle
- 链接里写网站名字，然后把文字**隐藏**
  用 `text-indent` 负值 + `overflow: hidden` 裁剪掉文字
index首页-header-entry入口（category分类+banner）
small/span都是行内元素小标签
### 单行文本溢出省略号（固定套路）
.ellipsis {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}
三个属性缺一不可：
overflow: hidden — 超出隐藏
text-overflow: ellipsis — 显示省略号
white-space: nowrap — 禁止换行
建议放在 common.css 里，哪里需要加 class="ellipsis" 复用。
## CSS 布局

> Finally here~

CSS 布局是网页设计的核心技术之一，用于控制元素在页面中的排列方式。

### 布局类型

| 类型 | 名称 |
|------|------|
| normal | 正常布局 |
| display | 模式转换布局 |
| flexbox | 弹性布局 |
| position | 定位布局 |
| grid | 网格布局 |
| column | 多列布局 |

### 使用建议

每种技术都有它们的用途，各有优缺点，相互辅助。

- **简单布局**：优先使用 Flexbox（一维）或 Grid（二维）。
- **复杂响应式布局**：使用 Grid + 媒体查询。
- **文本内容分栏**：多列布局（column-count）
- **兼容旧浏览器**：浮动布局 或 Flexbox 的降级方案。
- CSS Grid 逐渐成为主流，支持更复杂的布局场景。

# 77.定位布局-相对定位和绝对定位以及子绝父相
> position~

CSS 定位布局（position）是控制元素在页面中位置的核心技术之一。通过定位，可以实现元素脱离文档流、层叠、固定在特定位置布局效果（定位跟位置有关）

## 场景：

1. **固定导航栏**。页面滚动时导航栏始终**固定**在视口顶部。
2. **吸顶效果**。元素在滚动到某个位置后固定。
3. **弹出菜单/下拉框**。鼠标悬停时显示浮动菜单。
4. **悬浮效果**。元素悬浮在其他元素上方。
---

## position 属性值

| 值 | 名称 | 是否脱离文档流 |
|---|---|---|
| `static` | 静态定位（默认） | 否 |
| `relative` | 相对定位 | 否 |
| `absolute` | 绝对定位 | 是 |
| `fixed` | 固定定位 | 是 |
| `sticky` | 粘性定位 | 否 |

---
## 各类定位详解

### 1. 相对定位 relative
- 相对于**自身原来位置**偏移
- **不脱离**文档流，原位置仍占空间
- 常用于配合子元素绝对定位（"子绝父相"）
- 通过top、bottom、left、right属性进行偏移
- 优先执行top和left，同时有top和bottom时仅top生效

```css
.box {
  position: relative;
  top: 10px;
  left: 20px;
}
```
## 绝对定位

> erzi~ son~

CSS 绝对定位（position: absolute）核心是**脱离正常流**并基于**定位基准**进行偏移。

## 场景：

1. **弹出菜单/下拉框** — 鼠标悬停时显示浮动菜单
2. **悬浮效果** — 元素悬浮在其他元素上方

### 语法：

position: absolute;   /* 设定元素为绝对定位 */
- 元素脱离正常流，不占据空间，其他元素按原布局排列
- 相对于最近的已定位祖先元素（position 非 static）移动位置。若都无定位则相对于视口来定位
- 可以通过 top、bottom、left、right 属性进行偏移
- 优先级：若同时设置 top 和 bottom，仅 top 生效；同理 left 覆盖 right

## 定位 - 子绝父相

> erzi~ son~

定位最常用的布局技巧：**子绝父相**

### 场景：

1. **弹出菜单/下拉框** — 鼠标悬停时显示浮动菜单
2. **悬浮效果** — 元素悬浮在其他元素上方

### 为什么是子绝父相？

1. **子**元素可以悬浮其他元素上方，就不能占有位置、影响其他元素布局，所以**绝**对定位。
2. 但是子元素不能随便乱跑，要配合父元素移动位置，此时父元素需要加定位。
3. **父**元素需要占原来的位置，不能影响其他元素布局，此时**相**对定位最合适。

# 78.定位布局-小兔鲜定位模块布局

ctrl+F 查找
提高定位的层级
```css
z-index：100；
```

# 79.定位布局-轮播图效果定位的盒子垂直居中的做法

### **CSS 小技巧：巧用 `box-shadow` 代替 `border` 实现边框效果**

在开发如轮播图小圆点、按钮高亮等案例时，经常需要实现鼠标经过（hover）时增加边框的效果。

#### **1. 两种实现方式对比**

| 特性 | 使用 `border` 边框 (较麻烦) | 使用 `box-shadow` 阴影 (更简单) |
| :--- | :--- | :--- |
| **对布局的影响** | **占有空间**。增加边框会撑大盒子。 | **不占空间**。阴影悬浮在元素上方。 |
| **盒子模型** | 需要修改 `box-sizing: content-box` 来容纳边框。 | 无需修改盒子模型。 |
| **排列影响** | 盒子变大会挤压、影响后面小圆点的排列。 | **不会增加盒子大小**，从而不影响布局。 |

#### **2. 核心原理**
利用 `box-shadow` 的第四个参数（扩散半径）来模拟边框。
- 语法：`box-shadow: h-shadow v-shadow blur spread color;`
- 技巧：将前三个参数设为 `0`，调整第四个参数 `spread` 即可得到一个看起来像边框的阴影。

#### **3. 代码实现**

```css
/* 鼠标经过利用阴影实现边框效果 */
.banner .circle li:hover {
    /* 
       参数说明：
       0 0: 水平垂直偏移量为0
       0: 模糊半径为0（让边缘清晰像边框）
       4px: 扩散半径（即边框的粗细）
       rgba(255, 255, 255, 0.5): 颜色及透明度
    */
    box-shadow: 0 0 0 4px rgba(255, 255, 255, 0.5);
}
```

#### **4. 总结**
当需要实现**不影响页面布局**的边框高亮效果时，优先推荐使用 `box-shadow`。

# 80.定位布局-可爱的猫咪滚动效果案例
：：before
：：after
/* 隐藏滚动条 */
scrollbar-width：none；
/* 让谷歌或苹果浏览器隐藏滚动条 */
ul：：-webkit-scrollbar{
display:none;
}
/* 平滑滚动效果 */
scroll-behavior：smooth；

# 81.固定定位喝粘性定位
## 固定定位

> sun wukong~

CSS 固定定位（position: fixed）是一种将元素脱离文档流并始终相对于**浏览器视口**定位的布局技术。

### 场景：

1. **固定导航栏** — 页面滚动时导航栏始终**固定**在视口顶部
2. **页面广告** — 广告覆盖整个页面

### 语法：

```css
position: fixed;   /* 设定元素为固定定位 */
```

- 元素**脱离正常流**，不占据空间，其他元素按原布局排列
- 始终相对于浏览器窗口（**视口**）定位，滚动页面时位置不变
- 可以通过 `top`、`bottom`、`left`、`right` 属性进行偏移
- 优先级：若同时设置 top 和 bottom，仅 `top` 生效；同理 `left` 覆盖 `right`

## 粘性定位

> sticky~

CSS 粘性定位（position: sticky）是一种**混合定位模式**，结合了相对定位（relative）和固定定位（fixed）的特性。

### 场景：

1. **吸顶效果** — 元素在滚动到某个位置后固定
2. **表格表头固定** — 长表格滚动时表头始终可见

### 语法：

```css
position: sticky;   /* 设定元素为粘性定位 */
```

- 元素在滚动到指定位置（如 top: 10px）前为相对定位，之后转为固定定位
- **父容器**的 overflow 需为 `visible`，否则粘性定位失效
- 可以通过 `top`、`bottom`、`left`、`right` 属性进行偏移
- 须指定 top、right、bottom 或 left 四个其中之一，才可使粘性定位生效

# 82.定位布局-z-index叠放次序以及总结
## 定位布局 - 层叠顺序

> z-index~

z-index 属性用于控制元素在三维空间中的**层叠顺序**（即 Z 轴方向）。当多个元素在同一个平面（如同一行或列）重叠时，z-index 决定哪个元素显示在最上层。

### 场景：

1. 提高层级悬浮效果
2. 实现图片层叠效果

### 语法：

```css
z-index: 数值;   /* 设定层级 */
```

- **值类型**：整数（正数、负数、零）或 auto。数值越大，层级越高
- **默认值**：auto（等同于未设置，后出现的元素覆盖前者）
- **生效条件**：仅对定位元素（position 值为 relative、absolute、fixed 或 sticky）有效

## 定位总结

> summarize~

### 对比表格

| 定位类型 | 脱离文档流 | 定位基准 | 层叠控制 | 典型场景 |
|---|---|---|---|---|
| static | 否 | 默认文档流 | 无 | 普通元素布局 |
| relative | 否 | 自身正常位置 | 支持 | 微调元素、子绝父相 |
| absolute | 是 | 最近定位祖先 / 视口 | 支持 | 弹窗、下拉菜单、悬浮元素 |
| fixed | 是 | 视口 | 支持 | 固定导航栏、返回顶部按钮 |
| sticky | 否 | 视口或滚动祖先 | 支持 | 吸顶导航栏、侧边栏固定 |

### 定位属性：

- `position` — static / relative / absolute / fixed / sticky
- **偏移属性** — `top` / `right` / `bottom` / `left` 控制元素偏移量
- `z-index` — 控制层叠顺序，数值越大层级越高

### 常见组合：

- **固定导航栏**：`position: fixed` + `z-index`
- **弹窗**：`position: fixed` + 居中技巧 + 高 `z-index`
- **吸顶效果**：`position: sticky` + `top`

# 83.网格布局-grid布局介绍以及网格轨道
## CSS 布局

> Finally here~

CSS 布局是网页设计的核心技术之一，用于控制元素在页面中的排列方式。

### 布局类型

| 类型 | 名称 |
|------|------|
| normal | 正常布局 |
| display | 模式转换布局 |
| flexbox | 弹性布局 |
| position | 定位布局 |
| grid | 网格布局 |
| column | 多列布局 |

### 使用建议

每种技术都有它们的用途，各有优缺点，相互辅助。

- **简单布局**：优先使用 Flexbox（一维）或 Grid（二维）。
- **复杂响应式布局**：使用 Grid + 媒体查询。
- **文本内容分栏**：多列布局（column-count）
- **兼容旧浏览器**：浮动布局 或 Flexbox 的降级方案。
- CSS Grid 逐渐成为主流，支持更复杂的布局场景。

## 网格布局

> CSS Grid Layout

网格布局是一种**二维布局**模型，允许开发者通过定义行（rows）和列（columns）来精确控制网页元素的位置和尺寸。

> 实际开发大部分是**两者混用**的：
> 1. **Flexbox**：适合快速实现一维布局、动态内容对齐。比如单行布局
> 2. **Grid**：适合构建复杂页面框架，提供更强大的二维控制能力。比如多列或者响应式等

---

### Grid 概念总结

> you know~

| 概念 | 说明 |
|---|---|
| 容器 | 设置了 `display: grid` 的父元素 |
| 项目 | 容器内的直接子元素 |
| 行 | 水平方向的轨道 |
| 列 | 垂直方向的轨道 |
| 单元格 | 行和列的交叉区域 |

- **flex** = 单行布局
- **grid** = 多行多列布局
- 开发常见：单行布局用 flex，多行或响应式用 grid
- 网格布局的核心：创建好网格并放入各类元素

---

### 2. 网格容器

> grid

容器（父盒子）设置 `display: grid`（块级）或者 `display: inline-grid`（行内）

> 与弹性盒子不同的是，在定义网格后，网页并不会马上发生变化。因为 `display: grid` 的声明只创建了一个只有一列的网格。

---

### 3. 网格轨道

> grid tracks

网格轨道（Grid Tracks）决定了网格容器的基础布局结构，为子元素提供放置的位置。

#### 绘制网格：

- `grid-template-columns` — 定义网格中的列
- `grid-template-rows` — 定义网格中的行

#### 属性值：
- 有几个属性值代表创建几列/行
- 长度单位，比如 100px

```css
grid-template-columns: 200px 200px 200px;
/* 定义三列，每列宽度为 200px */

grid-template-rows: 200px 200px 200px;
/* 定义三行，每行高度为 200px */
```
## 4. 网格轨道 - 对齐方式

> justify-content、align-content

- `justify-content` 是控制**列轨道**（Column Tracks）在容器内水平分布
- `align-content` 是控制**行轨道**（Row Tracks）在容器内垂直分布

| 属性值 | 水平方向效果 | 垂直方向效果 |
|---|---|---|
| start（默认值） | 左对齐 | 顶部对齐 |
| end | 右对齐 | 底部对齐 |
| center | 水平居中对齐 | 垂直居中对齐 |
| space-around | 两侧留出相等的空白，项目周围空间均匀分布 | 上下留出相等的空白，项目周围空间均匀分布 |
| space-between | 首尾项目贴边 | 上下项目贴边 |
| space-evenly | 项目间、首尾与边界的空白相等 | 项目间、首尾与边界的空白相等 |

# 84.网格布局-fr单位以及gap和repeat函数
## 3. 网格轨道

> grid tracks

绘制网格（网格轨道）：`grid-template-columns` / `grid-template-rows` 属性值

| 属性值 | 说明 | 示例 | 应用场景 |
|---|---|---|---|
| 固定长度 | 使用 px、em 等固定单位定义列宽 | `grid-template-columns: 100px 200px` | 需要精确控制列宽的固定布局 |
| 百分比 | 按容器宽度百分比分配列宽 | `grid-template-columns: 30% 70%` | 响应式布局中按比例划分列 |
| fr 单位 | 分配轨道剩余空间的比例（1fr 表示一份，总和为容器剩余空间），fr 是 fraction 缩写，意思分数 | `grid-template-columns: 1fr 2fr` | 需要自适应比例分配的布局 |
| auto | 列宽由内容自动撑开 | `grid-template-columns: auto 100px` | 内容宽度不确定时的灵活布局 |
| repeat() 函数 | 简化重复的列定义 | `grid-template-columns: repeat(3, 1fr)`（等效于 1fr 1fr 1fr） | 多列等宽布局 |
| minmax() 函数 | 定义列宽的最小值和最大值 | `grid-template-columns: minmax(100px, 1fr)` | 响应式布局中限制列宽范围 |

## 5. 网格间距

> gap

`gap` 简写属性用于设置行与列之间的间隙（网格间距）

### 使用场景：
1. 让元素之间保留间隙

### 语法：

```css
gap: 20px;        /* 行和列之间保持 20 像素间隙 */
gap: 20px 30px;   /* 行间距是 20 像素，列间距是 30 像素 */
```

### 注意：gap 是简写形式，也可以分开写

```css
column-gap: 30px;  /* 列间距 */
row-gap: 20px;     /* 行间距 */
```

---

## repeat() 函数

### 语法：

```css
repeat(次数, 轨道尺寸)
/* 或 */
repeat(自动填充, 轨道尺寸)
```

### 1. 固定次数：

```css
grid-template-columns: repeat(3, 1fr);
/* 等效于 1fr 1fr 1fr，创建 3 列等宽布局 */
```
# 85.网格布局-auto fill自动填充完成响应式效果

### 2. 自动填充：适用于响应式布局中"列数随容器宽度变化"的场景

- `auto-fill`：尽可能多地创建列
- `auto-fit`：尽可能拉伸列填满容器（会合并空白，列宽不小于 minmax 的最小值）

```css
grid-template-columns: repeat(auto-fill, 200px);
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
```

---

## minmax() 函数

### 语法：

```css
minmax(最小值, 最大值)

/* 示例 */
minmax(200px, 1fr)
/* 列宽最小 200px，最大占满剩余空间 */
```
```css
grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
```

> 每列最小 100px，最大均分剩余空间，列数根据容器宽度自动增减。

# 86.网格布局-网格线以及练习网格的小游戏网站
### repeat() 函数 - auto-fill 与 auto-fit 区别

当容器空间远远大于所有子元素大小时：

1. **auto-fill** — 留有空白空间
2. **auto-fit** — 会拉伸盒子占满父容器空间

---

## 6. 网格线

> grid line~

如何实现**元素跨越**多个网格单元？

> 网格线分为**列线**（垂直）和**行线**（水平），编号从 1 开始。

### 实现语法 1：指定开始线和结束线

```css
/* 跨列：grid-column: 开始线编号 / 结束线编号 */
/* 跨行：grid-row:    开始线编号 / 结束线编号 */

grid-column: 1 / 3;   /* 从第 1 列到第 3 列 */
grid-row: 1 / 3;      /* 从第 1 行到第 3 行 */
```

### 实现语法 2：指定开始线 + span 跨越数量

```css
/* 跨列：grid-column: 开始线编号 / span 跨单元格数量 */
/* 跨行：grid-row:    开始线编号 / span 跨单元格数量 */

grid-column: 1 / span 2;   /* 从 1 线开始，跨 2 个单元格 */
grid-row: 1 / span 2;      /* 从 1 线开始，跨 2 个单元格 */
```

> **注意：** 该属性要加到**项目（子元素）**身上。

# 87.网格布局-auto flow自动填充以及object fit自动缩放
## 7. 网格填充方式

> grid-auto-flow

`grid-auto-flow` 决定网格容器中子元素**排列填充**方式

### 语法：

```css
/* 1. 默认值 */
grid-auto-flow: row;
/* 子元素按先行后列顺序填充，优先填满一行后换行 */

/* 2. 按列填充 */
grid-auto-flow: column;
/* 子元素按先列后行顺序填充，优先填满一列后换列 */
```

### 场景：

B 站、蔚来布局中有些子元素是按照列方式显示。
## object-fit

`object-fit` 是 CSS 中用于控制替换元素（如 `<img>`、`<video>`、`<iframe>` 等加载外部资源的元素）内容如何适应其容器尺寸的属性。

| 值 | 描述 |
|---|---|
| fill | 默认值。拉伸内容以完全填充容器，不保持宽高比，可能导致内容变形（最常用但需谨慎） |
| contain | 保持内容固有宽高比，缩放至完全适应容器内部（内容全部可见），容器可能有空白（类似"适应"模式） |
| cover | 保持内容固有宽高比，缩放至覆盖容器（内容可能部分被裁剪），容器无空白（类似"填充"模式） |

### 配合：

`object-position`：控制内容在容器内的对齐位置（如 `center` 居中、`top left` 左上角），常与 `object-fit` 搭配使用（例如 cover 时调整裁剪区域）。

# 88.网格布局-项目对齐方式以及必看总结
## 8. 项目对齐方式

> justify-items、align-items

在 CSS Grid 布局中，控制元素在网格内的对齐方式。

### 语法：

```css
justify-items: 水平对齐方式;   /* 水平方向（行轴）*/
align-items: 垂直对齐方式;     /* 垂直方向（列轴）*/
place-items: 水平+垂直方式;    /* 简写 */
```

> 为了提高可读性和兼容性，提倡使用前面两种方式。

**场景：** 元素在网格内对齐。

---

## 网格布局 - 总结

> grid

### 1. 创建网格轨道

```css
display: grid;

/* 创建列轨道 */
grid-template-columns: 100px 100px 100px;

/* 创建行轨道 */
grid-template-rows: 100px 100px 100px;

/* 列轨道两端对齐 */
justify-content: space-between;

/* 行轨道两端对齐 */
align-content: space-between;
```

### 2. 项目对齐方式

```css
/* 水平对齐方式 */
justify-items: start;
justify-items: end;
justify-items: center;
justify-items: stretch;
```

### 3. gap 网格间隙

```css
gap: 20px;
```

### 4. grid-auto-flow 自动填充

```css
grid-auto-flow: row;   /* 默认 */
```

### 5. 响应式布局

核心代码：

```css
grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
/* 每列最小 210px，自动计算列数，剩余空间均分 */
```

# 89.多列布局
## 多列布局

多列布局用于将元素的内容**自动分割**为指定数量的垂直列。

### 场景：

1. **长文章分栏** — 文章自动分列，中间有间隙，也可以做响应式
2. **图片瀑布流**

### 属性：

| 属性 | 作用 | 示例值 |
|---|---|---|
| `column-count` | 根据容器宽度和 column-count 值，**自动分配列宽** | `column-count: 3` 分为 3 列 |
| `column-gap` | 列之间的间距 | `20px`、`normal`（默认 1em） |
| `column-rule` | 列间的分隔线样式（颜色、宽度、样式） | `column-rule: 1px solid #ccc` |

> 核心是前两个：`column-count` 和 `column-gap`
### 注意：

1. 底部子元素被"**切断**"
   - 原因：`column-count` 的本质是将内容按垂直方向**自动分割到多列**（类似报纸排版），内容会优先填满一列后再流入下一列

### 解决方案：

```css
break-inside: avoid-column;
/* 强制元素不跨列分割（默认 auto，允许跨列）*/
/* 给子元素添加 */
```
# 90.常见鼠标样式以及CSS属性书写顺序
## cursor 鼠标样式

在 CSS 中，`cursor` 属性用于控制**鼠标指针**在元素上的**显示样式**，通过改变光标形态可以向用户传递交互提示（如"可点击""不可选中"等），从而提升界面交互体验。

| 值 | 描述 |
|---|---|
| `default` | 默认箭头（通常是系统默认的箭头光标） |
| **`pointer`** | 手型（指尖朝下的小手），常用于可点击元素（如链接 `<a>`、按钮 `<button>`） |
| `text` | I 型竖线（类似文本输入光标），用于可编辑文本区域（如 `<textarea>`、contenteditable 元素） |
| `wait` | 等待（旋转圆圈或沙漏），表示操作进行中（如加载、提交时） |
| `help` | 帮助（带问号的箭头），提示用户需要帮助（如提示信息区域） |
| **`not-allowed`** | 禁止（圆圈带斜线），表示操作不可用（如禁用的按钮） |
| `grab` | 抓取（手型带抓取动作），表示可拖动（如可拖拽的元素） |
| `grabbing` | 抓取中（手型收紧），表示正在拖动（配合 grab 使用） |
| `zoom-in` | 放大（+ 号），表示放大操作（如图片预览时） |
| `zoom-out` | 缩小（- 号），表示缩小操作（如图片预览时） |
| `move` | 拖放的小十字架 |

## CSS 属性书写顺序

合理的属性顺序应遵循「**布局 → 盒模型 → 视觉 → 交互 → 其他**」的逻辑，核心目标是让代码更易读、易维护。实际开发中可根据项目需求微调，但保持团队**一致性**是关键！

| 顺序 | 常见属性列表 |
|---|---|
| **布局相关** | `display`（显示类型）、`visibility`（可见性）、`position`（定位方式）、`top/right/bottom/left`（定位偏移）、`float`（浮动）、`clear`（清除浮动）、`overflow`（溢出处理）、`z-index`（层叠顺序）、`clip`（裁剪） |
| **盒模型** | `box-sizing`（盒模型计算方式）、`width/min-width/max-width`（宽度）、`height/min-height/max-height`（高度）、`margin`（外边距）、`padding`（内边距）、`border`（边框）、`outline`（轮廓，可选） |
| **视觉样式** | `color`（文本颜色）、`background`（背景）、`font`（字体合写）、`font-size`（字号）、`font-family`（字体系列）、`line-height`（行高）、`text-align`（文本对齐）、`text-indent`（首行缩进）、`letter-spacing`（字间距）、`white-space`（空白处理） |
| **交互与动画** | `cursor`（鼠标指针）、`opacity`（透明度）、`transition`（过渡）、`animation`（动画）、`transform`（变换，如旋转、缩放） |
| **其他（特殊/低频）** | `filter`（滤镜）、`clip-path`（裁剪路径）、`backdrop-filter`（背景滤镜）、`will-change`（优化提示）、`touch-action`（触摸行为）、`scroll-behavior`（滚动行为） |

