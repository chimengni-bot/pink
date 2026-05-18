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
