## BFC 块格式化上下文

### BFC是什么？

<dfn>BFC</dfn> (Block Formatting Context)是块格式化上下文，是 Web 页面的可视化CSS渲染的一部分，是块级盒子的布局过程发生的区域，也是浮动元素与其它元素交互的区域。块级盒子是什么可以了解一下[视觉格式化模型](./CSSKnowledge/视觉格式化模型.md)。具有BFC特性的元素会被生成块盒子，块级盒子里面应用了BFC提供了一个独立的容器环境，块级盒子里面的元素在独立的环境里面进行一定规则的布局，容器里面的元素不会在布局上面影响到外面的元素，并且 BFC 具有普通容器所有的一些特性。

通俗一点来讲，一但具有 BFC 的特性就会把块级元素生成块级盒子，**根据 BFC 生成的块级盒子**可以理解为一个封闭的大箱子，箱子内部的元素无论如何翻江倒海，都不会影响到外部。而外部会根据各个块级盒子的相互作用区域进行排序。

BFC 对浮动定位（float）与清除浮动（clear）都很重要。浮动定位和清除浮动时只会应用于同一个BFC内的元素。浮动不会影响其它BFC中元素的布局，而清除浮动只能清除同一BFC中在它前面的元素的浮动。外边距折叠（Margin collapsing）也只会发生在属于同一BFC的块级元素之间。

### 怎样触发BFC模型？
- 根元素`<html>`
- 浮动元素 (元素的`float`不是`none`)
- 绝对定位元素 (元素的`position`为`absolute`或`fixed`)
- 行内块元素 (元素的`display`为`inline-block`)
- 表格单元格 (元素的`display`为`table-cell`, HTML表格单元格默认为该值)
- 表格标题 (元素的`display` 为 `table-caption`, HTML表格标题默认为该值)
- 匿名表格单元格元素(`display`为`table`、`table-row`、`table-row-group`、`table-header-group`、`table-footer-group`(分别是HTML table, rouw tbody, thead, tfoot的默认属性)、`inline-table`)
- `overflow` 值不为 `visible` 的块元素
- `display` 值为 `flow-root` 的元素。
- `contain` 值为 `layout`、`content` 或 `paint` 的元素
- 弹性元素 (`display`为`flex`或`inline-flex` 元素的直接子元素)
- 网格元素 (`display`为`grid`或`inline-grid`元素的直接子元素)
- 多列容器 (元素的`column-count`或`column-width`不为auto, 包括`column-count`为1)
- `column-span`为`all`的元素始终会创建一个新的BFC，即使该元素没有包裹在一个多列容器中。


### BFC 应用场景

- 让浮动内容和周围的内容等高
- 外边距塌陷，重叠。
- display: flow-root: 不用再清除浮动，创建无副作用的BFC，使浮动周围高度不会塌陷。


### BFC 的例子
可以查看以下文章: 
[块格式化上下文](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context), [理解 CSS 布局和 BFC](https://segmentfault.com/a/1190000018677177)


### 参考链接

- [学习 BFC (Block Formatting Context)](https://juejin.im/post/59b73d5bf265da064618731d#heading-10)
- [块格式化上下文](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)
- [理解 CSS 布局和 BFC](https://segmentfault.com/a/1190000018677177)
- [10 分钟理解 BFC 原理](https://zhuanlan.zhihu.com/p/25321647)