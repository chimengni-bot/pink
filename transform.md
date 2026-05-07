# 91.第四章案例展示以及2D变换之平移translate
- 变换
- 动画
- 动效案例
## 基础变换函数 - 2D

> transform~

`transform` 是用于对元素进行 2D/3D 变换的核心属性，支持平移、旋转、缩放、倾斜等效果，且**不破坏**原有文档流布局。

| 变换类型 | 函数语法 | 核心描述 | 应用场景 |
|---|---|---|---|
| **平移** | `translate(x, y)` `translateX(x)` `translateY(y)` | 沿 X/Y 轴移动元素，参数可为像素或百分比（百分比相对于元素自身尺寸） | 微调元素位置、悬停偏移效果 |
| **旋转** | `rotate(angle)` | 以元素中心为基点顺时针旋转，需加单位 deg（负值为逆时针） | 图标旋转、卡片翻转 |
| **缩放** | `scale(sx, sy)` `scaleX(sx)` `scaleY(sy)` | X/Y 轴按比例缩放，单参数时等比例缩放（>1 放大，<1 缩小，支持百分比） | 悬停放大、焦点突出 |
| **倾斜** | `skew(x-angle, y-angle)` `skewX(angle)` `skewY(angle)` | 沿 X/Y 轴扭曲元素形状，参数为倾斜角度（支持负值） | 斜切导航栏、动态图表 |

# 92.2D变换之平移案例

## 1. 变换函数 - 2D 平移
transform: translate~

### 1.1 基本定义
平移（translate）可以沿 X 轴或 Y 轴移动元素的位置。

- 特点 ： 不改变元素的实际布局 ，移动后原位置仍保留空白（类似于相对定位）。
### 1.2 应用场景
1. 悬停元素微调 ：鼠标放入元素时进行上下或左右的轻微移动（配合 transition 过渡效果更优雅）。
2. 元素居中 ：配合绝对定位实现元素的水平和垂直绝对居中。
### 1.3 语法格式
```
/* x 和 y 轴同时移动 */
transform: translate(20px, 30px); 

/* 仅沿 X 轴移动 */
transform: translateX(50%); 

/* 仅沿 Y 轴移动 */
transform: translateY(-50%); 
```
### 1.4 重要提示
- 不影响布局 ：平移仅是视觉上的移动，不会挤压到周围的其他页面元素。
- 性能更佳 ：在实现鼠标经过元素移动的效果时，应 优先使用 transform ，而不是修改 left 或 top 属性，因为 transform 的性能表现更好（触发的是合成器处理，而不是重排）。
- 如歌单位是百分比，相对于元素的尺寸，而非父容器。

# 93.2D变换之旋转rotate

## 2. 变换函数 - 2D 旋转
transform: rotate~

### 2.1 基本定义
旋转（rotate）通过改变元素在平面或空间中的 角度 来实现视觉效果。

### 2.2 应用场景
1. 悬停动画 ：例如鼠标经过按钮时，按钮产生旋转效果。
2. 加载动画 ：利用无限循环旋转制作 Loading 效果。
### 2.3 语法格式
```
/* 旋转元素 */
transform: rotate(360deg); 
```
- 参数单位 ： deg （度）。
- 方向控制 ：正值表示 顺时针 旋转，负值表示 逆时针 旋转。
### 2.4 变换中心点 transform-origin
```
/* 设置旋转的基点 */
transform-origin: left top; 
```
- 作用 ：设置元素旋转的中心点（基点）。
- 取值方式 ：
  - 方位名词 ：如 left , top , bottom , right , center 。
  - 数值 ：支持像素（px）和百分比（%）等精准定位。

### 注意：行内元素的限制
- 布局特性影响 ：行内元素（inline）由于其布局特性（如无法直接设置宽高、盒模型限制、 transform 基准点异常等），会破坏旋转效果的稳定性和精确性。
- 解决方案 ：在使用 transform 旋转文字或图标类元素时，必须将其转换为 行内块元素（display：inline-block） 或 块级元素（block） 。
- 典型案例 ： 字体图标 （如 iconfont）在旋转前需要先进行模式转换。

# 94.2D变换之缩放scale

## 3. 变换函数 - 2D 缩放
transform: scale~

### 3.1 基本定义
缩放（scale）用于调整元素的尺寸大小。

- 特点 ： 不改变元素在文档流中的原始占位 。即使放大，也不会挤压到周围的其他盒子。
### 3.2 应用场景
1. 悬停放大 ：如鼠标经过图片、按钮时产生平滑的放大效果。
### 3.3 语法格式
```
/* 整体放大 1.5 倍 */
transform: scale(1.5); 

/* 指定 X 和 Y 轴缩放 */
transform: scale(1.5, 1); 
```
### 3.4 参数说明
- 单参数 ：同时作用于 X 轴和 Y 轴。
  - 例如： scale(2) 表示宽度和高度同时放大 2 倍。
- 双参数 ：第一个参数控制 X 轴，第二个参数控制 Y 轴。
  - 例如： scale(0.5, 1.5) 表示横向缩小 50%，纵向放大 50%。

# 95.2D变换之倾斜以及卡片折叠效果

## 4. 变换函数 - 2D 倾斜
transform: skew~

### 4.1 基本定义
倾斜（skew）用于对元素进行二维倾斜变换，通过沿 X 轴或 Y 轴扭曲元素的几何形状。

### 4.2 应用场景
1. 交互效果 ：如鼠标经过元素时产生倾斜的动态效果，增加页面的设计感。
### 4.3 语法格式
```
/* X 和 Y 轴同时倾斜 */
transform: skew(30deg, 30deg); 

/* 仅沿 X 轴倾斜 */
transform: skewX(30deg); 

/* 仅沿 Y 轴倾斜 */
transform: skewY(30deg); 
```
### 4.4 注意事项
- 单参数规则 ：如果 skew() 只写一个参数，则该参数作用于 X 轴，Y 轴默认为 0。
- 变换中心点 ：可以使用 transform-origin 属性来设置倾斜的中心点。

# 96.过渡transition完整写法
## 过渡进阶
transition~

### 1. transition 完整写法
```
/* 语法结构 */
transition: 过渡属性 持续时间 速度曲线 延迟时
间;

/* 示例：所有属性添加过渡效果，持续1秒，匀速，延
迟1秒执行 */
transition: all 1s linear 1s;
```
### 2. 速度曲线参数详解
速度曲线参数 效果描述 
ease 默认值 。慢速开始 → 加速 → 慢速结束。适合大多数自然过渡（如按钮悬停）。 
linear 匀速运动 。无加速/减速。适合机械感效果（如进度条）。
ease-in 慢速开始 → 逐渐加速。适合元素从静止启动（如弹窗出现）。
ease-out 快速开始 → 逐渐减速。适合元素退出（如关闭动画）。
ease-in-out 慢速开始和结束，中间加速。适合对称性动画（如页面切换）。 
cubic-bezier(x1,y1,x2,y2) 贝塞尔曲线 。通过四个值（0-1范围内）自定义速度曲线，实现弹跳、骤停等创意效果。

### 3. 进阶学习资源与工具
1. cubic-bezier.com ：可视化编辑贝塞尔曲线。
2. easings.net ：获取常用缓动函数的预设值。
3. 谷歌浏览器调试 ：在开发者工具的 Styles 面板中点击速度曲线图标，可实时调整和预览效果。

# 97.2D变换之复合写法以及汽车滚动案例
> transform~

在 CSS 中，transform 属性的复合写法（多个变换函数组合使用）

### 语法：

```css
transform: A() B() C();
```

### 顺序：

- 核心规则：**从右到左**的执行顺序
- 实际的执行顺序是：先执行最右侧的 `C()`，然后是 `B()`，最后是左侧的 `A()`

# 98.3D变换之左手法则以及旋转rotateXYZ
## 3D 变换与透视

> 3D~

CSS 3D 效果通过将二维元素在三维空间中进行变换，为网页添加**立体感**和动态交互体验。

### 场景：

1. 卡片翻转效果
2. 3D 幻灯片 / 轮播图
3. 数据可视化。立体图表（如 3D 柱状图）等

> 相比 JavaScript 或 WebGL，CSS 3D 利用 GPU 加速，动画更流畅，性能更高效。

---

## 三维坐标系

> x y z~

### 坐标数值：
rotateX/rotateY/rotateZ
- **X 轴** 代表左右方向。右边是正值，左边是负值
- **Y 轴** 代表上下方向。**下方是正值**，上方是负值
- **Z 轴** 代表远离/接近屏幕的方向。**接近屏幕是正值**，远离屏幕是负值
- 可以利用**左手法则**记忆
- 默认情况下，元素在二维平面上呈现，Z 轴值为 0
- 当应用 3D 变换时，元素便可以在三维空间中自由变换

# 99.3D变换之透视perspective以及旋转方向
## 透视（Perspective）

> Perspective~

在 CSS 中，透视效果（Perspective）用于模拟人眼观察 3D 空间时的近大远小效果。

### 语法：

```css
perspective: 1000px;  /* 透视效果 */

/* 同时使用多个属性 */
transform: perspective(1000px) rotateX(45deg);
```

- 数值越小，透视效果越强
- 给**父元素**添加，里面所有子元素都会添加透视效果（常用）
- 给**子元素**添加，当前元素添加透视效果

> **注意：** `perspective()` 必须作为 transform 属性的**第一个函数**（否则无效）

## 透视（Perspective）- 3D 旋转方向

> Perspective~

3D 旋转方向：还是**左手法则**

### 旋转方向判断：

| 函数 | 正值方向 | 负值方向 |
|---|---|---|
| `rotateX(360deg)` | 四指指向的方向（绕 X 轴旋转） | 反方向 |
| `rotateY(360deg)` | 四指指向的方向（绕 Y 轴旋转） | 反方向 |

### 左手法则：
- 大拇指指向**坐标轴正方向**
- 四指弯曲的方向 = **正值旋转方向**
- 反之即为负值方向

# 100.3D变换之两面翻转的盒子效果
## 3D 旋转 - 两面翻转的盒子
## 语法

```css
backface-visibility: hidden;
```

## 作用

控制元素背面的可见性（默认镜像显示），常用于隐藏背面（如扑克牌翻转效果）。

## 取值

- `visible`：背面可见（默认）
- `hidden`：背面隐藏

# 101.3D变换之3D位移以及开启子元素3D空间

## 3D 位移

CSS 3D 平移函数 `translateZ()` 与 `translate3d()`。

## 语法

```css
transform: translateZ(100px);
```

## 说明

- 沿 Z 轴（垂直于屏幕方向）平移元素，实现近大远小的立体效果
- 正值元素靠近观察者（放大），负值远离观察者（缩小）
- 需父容器设置 `perspective` 属性才能生效，否则无视觉变化
- 
## 两个核心知识点

```css
/* 父元素:开启 3D 空间 */
.parent {
    transform-style: preserve-3d;
}

/* 子元素:在 3D 空间里位移 */
.child {
    transform: translate3d(0, 0, 60px);
}
```
# 102.动画animation-基本使用

## 是什么

通过定义**关键帧**实现元素动态效果的技术。

## 关键帧(Keyframe)

定义动画中**起始、转折、结束**等关键状态,中间过渡由浏览器自动补全。

## 基本用法

/* 1. 定义关键帧 */
**写法一:百分比**(适合多个关键帧)

```css
@keyframes move {
    0%   { transform: translateX(0); }
    20%  { transform: translateX(50px); }
    100% { transform: translateX(100px); }
}
```
写法二:from / to(只有起点和终点时简写)
```css
@keyframes move {
    from { transform: translateX(0); }
    to   { transform: translateX(100px); }
}
```
/* 2. 使用动画 */
```css
.box {
    animation: move 2s infinite;
}
```

# 103.动画animation-完整写法
# animation 完整写法

```css
animation: 动画名称 动画时长 速度曲线 延迟时间 播放次数 播放方向 执行完毕状态;
```

## 规则

- 动画名称、动画时长**必写**,其余可省略
- 顺序不能乱
- 写在目标元素里

## 子属性

| 子属性 | 默认值 | 说明 |
|---|---|---|
| 播放次数 | `1` | 无限循环写 `infinite` |
| 播放方向 | `normal` | `reverse`(反向)、`alternate`(交替) |
| 执行完毕状态 | `none` | `forwards`(停在最后一帧)、`backwards`(回到第一帧) |

## 示例

```css
.box { animation: move 1s infinite alternate; }
```
# animation 单写属性

| 子属性 | 默认值 | 说明 |
|---|---|---|
| `animation-timing-function` | `ease` | 速度曲线,支持 `linear`、`cubic-bezier()` 等 |
| `animation-delay` | `0s` | 延迟时间,可设负值(跳过部分动画) |
| `animation-iteration-count` | `1` | 播放次数,无限循环写 `infinite` |
| `animation-direction` | `normal` | 播放方向,`reverse`(反向)、`alternate`(交替) |
| `animation-fill-mode` | `none` | 结束后状态,`forwards` 保留最后一帧 |
| `animation-play-state` | `running` | 暂停/继续,`paused` 暂停动画 |

## 示例

```css
.box {
    animation-name: move;
    animation-duration: 1s;
    animation-iteration-count: infinite;
    animation-play-state: paused;  /* 鼠标移入时改 running */
}
```

# 104.动画animation-仿360急速浏览器首屏效果

# 105.动画animation-逐帧动画以及仿手机360逐帧案例


## 原理

像翻页书一样,把图片在**离散的步骤**间跳跃切换,而不是平滑过渡。

1. 通过改变**背景位置**移动图片,移动距离 = 图片宽度
2. 图片有 N 个图形,`steps` 就写 N

## 语法

```css
.box {
    animation: move 1s steps(8) infinite;
    /*               步数为正整数 */
}
```

- `steps(N)`:N 必须是**正整数**
- 常配合**精灵图(sprite)**实现帧动画

## 示例:精灵图奔跑动画

```css
.run {
    width: 140px;        /* 单帧宽度 */
    height: 140px;
    background: url(sprite.png) no-repeat;
    animation: run 1s steps(8) infinite;
}

@keyframes run {
    from { background-position: 0 0; }
    to   { background-position: -1120px 0; }  /* 8 帧 × 140px */
}
```

## 要点

> **steps 把动画切成 N 段跳着播,配合精灵图就是逐帧动画。**
