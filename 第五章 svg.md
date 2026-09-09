# 114.svg基本语法使用
## SVG 图片

SVG（Scalable Vector Graphics）是一种基于 XML 的**矢量图形**标准，由 W3C 制定，支持无损缩放、交互性和动态效果。其核心特点包括：

### 核心特点

- **矢量特性**：无论放大或缩小均保持清晰。文件体积小，适合网络传输，尤其适用于高分辨率设备。
- **可编辑性**：直接通过文本编辑器修改 SVG 代码，支持颜色、形状、动画参数的实时调整。
- **交互性**：支持 JavaScript 和 CSS 控制，可实现点击、悬停等动态响应。
- **兼容性**：主流浏览器（Chrome、Firefox、Safari）均原生支持 SVG，移动端适配性强。

### SVG 组成

- `<svg>` **根元素**：SVG 图标必须包裹在 `<svg>` 标签内。
- `<path>` **路径**：通过 `d` 属性定义路径指令。
  - `M`：移动画笔到坐标点
  - `Z`：闭合路径

# 115.svg图片-描边效果以及仿北大官网效果
## SVG 图标常见 CSS 属性

SVG 是行内块元素类似，可以设置大小、移动位置、动画等。但是有自己特殊的样式属性。

| 属性 | 描述 | 取值示例 |
| --- | --- | --- |
| `fill` | 填充颜色（支持颜色值、渐变、图案）不需要改为 none | `fill: #f00;` |
| `stroke` | 定义描边颜色（支持颜色值、渐变、图案） | `stroke: #f00;` |
| `stroke-width` | 描边宽度（支持像素、百分比、px、em 等单位） | `stroke-width: 2px;` |
| `stroke-dasharray` | 虚线模式（实线长度 + 间隔长度） | `stroke-dasharray: 10;` |
| `stroke-dashoffset` | 调整虚线与间隔的起始位置 | `stroke-dashoffset: 100;` |

# 116.svg图片-利用偏移实现画心效果
## SVG 动画

### 绘制动画（"画笔"效果）总结

**最经典的应用：**

通过动画逐渐减小 `stroke-dashoffset`，让虚线模式"逆向移动"，视觉上像**画笔沿着路径绘制线条**。

**实现步骤：**

1. 计算路径总长度 L（通过 `getTotalLength()`）。
2. 设置 `stroke-dasharray: X;`
3. 初始 `stroke-dashoffset: X;`（实线段完全隐藏）。
4. 动画中逐渐将 offset 减小到 0，实线段逐渐覆盖整个路径。

### 示例代码

获取路径总长度：

```js
heart.getTotalLength()
// 2783.177734375
```

CSS 样式：

```css
.box svg {
  width: 3520px;
  stroke-dasharray: 3852;
  stroke-dashoffset: 3852;
}
```

动画关键帧：

```css
@keyframes move {
  0% {
    stroke-dashoffset: 3852;
  }
  100% {
    stroke-dashoffset: 0;
  }
}
```

# 117.svg图片-仿OPPOAI里程碑案例
# 118.svg图片-无人机动画案例
# 119.clip-path裁剪-基本语法使用
## clip-path

`clip-path` 创建复杂的裁剪形状，使元素仅显示被裁剪区域内的部分。

### 语法

`clip-path: 内置几何形。`

- 内置几何形，状如 `circle()`、`polygon()` 等。

```css
.circle {
  clip-path: circle(40% at 50% 50%);
}
```

> 不需要去记这些参数。

### 常见内置几何形

| 函数 | 说明 | 示例 |
| --- | --- | --- |
| `circle()` | 圆形裁剪 | `clip-path: circle(40% at 50% 50%);` |
| `ellipse()` | 椭圆裁剪 | `clip-path: ellipse(40% 20% at 50% 50%);` |
| `polygon()` | 多边形裁剪（任意点） | `clip-path: polygon(50% 0, 100% 100%, 0 100%);` |
| `inset()` | 矩形/内缩裁剪 | `clip-path: inset(10% 20% 10% 20% round 10px);` |
| `path()` | SVG 路径裁剪 | `clip-path: path('M0,0 L100,0 L50,100 Z');` |

### 常见应用场景

- 圆形、椭圆形、三角形、菱形、五边形、六边形、星形、消息框等不规则形状
- 平行四边形按钮、斜切图片拼接（如游戏下载入口、汽车展示页）
- 鼠标悬停的裁剪动画过渡效果

### 可视化工具

`https://tools.jb51.net/static/api/css3path/index.html`

直接在网页上拖拽生成 `clip-path` 代码，不用手写坐标。

# 120.clip-path裁剪-灯光扫描文字效果
# 121.turn旋转一圈-仿华为官网花瓣旋转效果
# 122.滤镜filter的使用
## 滤镜 filter

CSS 滤镜通过 `filter` 属性实现，可对元素及其子元素进行实时图像处理，无需修改原始素材。

### 滤镜函数一览

| 滤镜函数 | 作用 | 语法示例 | 说明 |
| --- | --- | --- | --- |
| `blur()` | 高斯模糊 | `blur(5px)` | 值越大越模糊 |
| `brightness()` | 调整元素亮度 | `brightness(150%)` | 100%（或 1）为原始亮度；<100% 变暗；>100% 变亮 |
| `contrast()` | 调整元素对比度 | `contrast(200%)` | 同上 |
| `saturate()` | 调整背景饱和度 | `saturate(150%)` | 0%（无色彩）~ 100%（原饱和度）~ >100%（更高饱和） |
| `grayscale()` | 将元素转换为灰度图 | `grayscale(100%)` | 0%（或 0）为原始色彩；100%（或 1）为完全灰度 |
| `hue-rotate()` | 调整元素色相（改变颜色倾向） | `hue-rotate(90deg)` | 单位为角度 |
| `sepia()` | 将元素转换为深褐色（复古效果） | `sepia(70%)` | 0%（或 0）为原始色彩；100%（或 1）为完全深褐色 |
| `drop-shadow()` | 为元素添加投影 | `drop-shadow(5px 5px 5px #669)` | 类似 `box-shadow`，但**支持非矩形元素** |

### 使用示例

```css
/* 单个滤镜 */
.img {
  filter: blur(5px);
}

/* 多个滤镜叠加（按顺序生效） */
.img {
  filter: brightness(120%) contrast(110%) saturate(150%);
}

/* 悬停时切换滤镜（常用于图片交互） */
.img {
  filter: grayscale(100%);
  transition: filter 0.4s;
}
.img:hover {
  filter: grayscale(0);
}
```

### drop-shadow 与 box-shadow 区别

| 属性 | 适用范围 |
| --- | --- |
| `box-shadow` | 元素**矩形盒子**的阴影 |
| `filter: drop-shadow()` | 沿着元素**实际可见形状**（如 PNG 透明图、SVG）生成阴影 |

```css
/* PNG 透明小图标，想要贴合形状的阴影 */
.icon {
  filter: drop-shadow(2px 2px 4px rgba(0, 0, 0, 0.5));
}
```

### 一句话总结

`filter` 让你**不动原图**就能改变视觉效果，多个滤镜可以叠加，常用于图片悬停、视频蒙层、复古风格等场景。

# 123.背景滤镜backdrop-filter
## 背景滤镜

`backdrop-filter` 给元素**背后的区域**加滤镜，常配合半透明背景做毛玻璃。文字、图标本身保持清晰。

## 写法

```css
.bar {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px); /* Safari */
}
```

常用：`blur()`，也可组合 `brightness()` / `saturate()` 等。

## 注意

- 背景必须半透明，纯色看不出效果
- 后面要有图/视频/内容才有东西可糊
- 和 `filter` 不同：`filter` 糊的是自己，这个糊的是背后

# 124.动画时间线timeline-滚动时间线
## 动画时间线

`animation-timeline` 用来把动画进度绑到特定事件上（滚动、视口可见性），而不是只靠时间播放。

## 滚动时间线

动画进度跟页面或容器的滚动位置走：滚多少，播到哪。

```css
.scrollbar {
  width: 0%;
  height: 3px;
  background: linear-gradient(90deg, #7c5cff, #ff7ad9);
  animation: move 2s;
  animation-timeline: scroll();
}

@keyframes move {
  0% { width: 0; }
  100% { width: 100%; }
}
```

`animation` 定义动画，`animation-timeline: scroll()` 把进度交给滚动。时长在滚动时间线下不再按秒走完。

## 注意

- `scroll()`：跟页面/容器滚动绑定
- 还可绑视口可见性（元素进场、离场）
- 参考：<https://www.porsche.cn/china/zh/models/cayenne/cayenne-models/cayenne-passion/>、<https://stripe.com/zh-us/enterprise>

# 125.动画时间线timeline-视图时间线
## 视图时间线

动画进度跟元素进入 / 离开视口的可见性走：看见多少，播到哪。

```css
.card {
  animation: fade-up 1s linear both;
  animation-timeline: view();
}

@keyframes fade-up {
  0% { opacity: 0; transform: translateY(40px); }
  100% { opacity: 1; transform: translateY(0); }
}
```

`animation-timeline: view()` 把进度交给元素在视口里的进出，滚动进场即可驱动动画。

# 126.CSS变量的定义以及使用
## 变量和函数

CSS 变量和动态函数（`calc()`、`clamp()` 等）用来做逻辑和动态计算。常见场景：主题切换、响应式、交互动画。

## 变量

CSS 变量（自定义属性）用来存值和复用，相当于一个容器。

```css
/* 定义 */
--color: #000;

/* 使用 */
color: var(--color);
background-color: var(--bgcolor);
```

`--变量名` 定义，`var(--变量名)` 取值。

## 作用域

变量在哪个范围生效：

```css
:root {              /* 全局，整页可用 */
  --color: #000;
}

.box {               /* 局部，只作用于自己和子元素 */
  --bgcolor: pink;
}

.nav {
  color: var(--color);
  background-color: var(--bgcolor);
}
```

- 全局：写在 `:root`
- 局部：写在具体选择器里，只影响该元素及其子元素

# 127.CSS计算函数calc基本使用
## CSS3 计算能力

`calc()` 做加减乘除，支持混合单位（如 `%` 和 `px`）。

```css
.box {
  width: calc(100% - 20px);              /* 父宽减固定值 */
  height: calc(var(--base-size) * 1.5);  /* 变量参与运算 */
}
```

运算符：`+` `-` `*` `/`，**符号左右必须空格**，例如 `100% - 20px`。

多行多列、绝对定位铺满时常用，如 `width: calc(100% - 100px)`。

# 128.CSS变量和计算函数修改精灵图坐标效果
## 变量 + calc 做精灵图

用 CSS 变量当序号，`calc()` 算出背景偏移，一套样式切出多帧图标。

```css
ul li {
  list-style: none;
  width: 58px;
  height: 58px;
  background: url(./img/sprite.png) no-repeat 0 calc(var(--i) * -58px);
}
```

```html
<ul>
  <li style="--i:0"></li>
  <li style="--i:1"></li>
  <li style="--i:2"></li>
  <li style="--i:3"></li>
</ul>
```

每个 `li` 只改 `--i`，背景 Y 轴按 `-58px * i` 移动，对准雪碧图对应一格。

# 129.综合案例1-动感菜单
# 130.综合案例2-滑动导航栏效果
# 131.综合案例3-炫酷导航栏上
# 132.综合案例3-炫酷导航栏下
# 133.综合案例4-滚动叠加卡片首屏以及vw和vh单位
# 134.综合案例4-滚动叠加卡片主体制作
# 135.综合案例4-滚动叠加卡片制作
# 136.综合案例4-滚动叠加卡片添加视图时间线
