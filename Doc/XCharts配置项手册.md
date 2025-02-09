# 配置项手册

[返回首页](https://github.com/monitor1394/unity-ugui-XCharts)  
[XChartsAPI接口](XChartsAPI.md)  
[XCharts问答](XCharts问答.md)

* [Theme](#Theme)  
* [Title](#Title)  
* [Legend](#Legend)  
* [Tooltip](#Tooltip)  
* [DataZoom](#DataZoom)  
* [Grid](#Grid)  
* [XAxis](#XAxis)  
* [Series](#Series)  
* [Settings](#Settings)

## `Theme`

---
主题组件。主题用来配置图表的全局配色等其他参数。

相关参数：

* `theme`：内置主题类型。有`Default`、`Light`、`Dark`三种可选内置主题。
* `font`：所有文字的通用字体。
* `backgroundColor`：图表背景颜色。
* `titleTextColor`：主题的主标题文字颜色。
* `titleSubTextColor`：主题的副标题文字颜色。
* `legendTextColor`：图例的激活时文字颜色。
* `legendUnableColor`：图例的非激活时文字颜色。
* `axisTextColor`：坐标轴的文字颜色。
* `axisLineColor`：坐标轴的轴线颜色。
* `axisSplitLineColor`：坐标轴的分割线颜色，默认和轴线颜色一致。
* `tooltipBackgroundColor`：提示框的背景颜色。
* `tooltipFlagAreaColor`：提示框的阴影指示器的颜色。
* `tooltipTextColor`：提示框的文字颜色。
* `tooltipLabelColor`：提示框的十字指示器坐标轴标签的背景颜色。
* `tooltipLineColor`：提示框的指示线的颜色。
* `dataZoomTextColor`：区域缩放的文字颜色。
* `dataZoomLineColor`：区域缩放的线条颜色。
* `dataZoomSelectedColor`：区域缩放的选中区域颜色。
* `colorPalette`：调色盘颜色列表。如果系列没有设置颜色，则会依次循环从该列表中取颜色作为系列颜色。

相关接口：

* `GetColor(int index)`：获得调色盘对应系列索引的颜色值。
* `GetColorStr(int index)`：获得指定系列索引的十六进制颜色值字符串。
* `GetColor(string hexColorStr)`：将字符串颜色值转成Color。

## `Title`

---
标题组件，包含主标题和副标题。

相关参数：

* `show`：是否显示标题组件。
* `text`：主标题文本，支持使用 `\n` 换行。
* `textFontSize`：主标题文字的字体大小。
* `subText`：副标题文本，支持使用 `\n` 换行。
* `subTextFontSize`：副标题文字的字体大小。
* `itemGap`：主副标题之间的间距。
* `location`：标题显示位置 `Location` 。 `Location` 的参数如下：
  * `align`：对齐方式。有以下对齐方式。
    * `TopLeft`：左上角对齐。
    * `TopRight`：右上角对齐。
    * `TopCenter`：置顶居中对齐。
    * `BottomLeft`：左下对齐。
    * `BottomRight`：右下对齐。
    * `BottomCenter`：底部居中对齐。
    * `Center`：居中对齐。
    * `CenterLeft`：中部靠左对齐。
    * `CenterRight`：中部靠右对齐。
  * `left`：离容器左侧的距离。
  * `right`：离容器右侧的距离。
  * `top`：离容器上侧的距离。
  * `bottom`：离容器下侧的距离。

## `Legend`

---
图例组件。图例组件展现了不同系列的标记，颜色和名字。可以通过点击图例控制哪些系列不显示。

相关参数：

* `show`：是否显示图例组件。
* `selectedMode`：选择模式。控制是否可以通过点击图例改变系列的显示状态。默认开启图例选择，可以设成 `None` 关闭。有以下三种选择方式：
  * `Multiple`：多选。
  * `Single`：单选。
  * `None`：无法选择。
* `orient`：布局方式是横还是竖。
  * `Horizonal`：水平。
  * `Vertical`：垂直。
* `location`：图例的显示位置 `Location` 。 `Location` 的参数如下：
  * `align`：对齐方式。有以下对齐方式。
    * `TopLeft`：左上角对齐。
    * `TopRight`：右上角对齐。
    * `TopCenter`：置顶居中对齐。
    * `BottomLeft`：左下对齐。
    * `BottomRight`：右下对齐。
    * `BottomCenter`：底部居中对齐。
    * `Center`：居中对齐。
    * `CenterLeft`：中部靠左对齐。
    * `CenterRight`：中部靠右对齐。
  * `left`：离容器左侧的距离。
  * `right`：离容器右侧的距离。
  * `top`：离容器上侧的距离。
  * `bottom`：离容器下侧的距离。
* `itemWidth`：每个图例项的宽度。
* `itemHeight`：每个图例项的高度。
* `itemGap`：图例每项之间的间隔。横向布局时为水平间隔，纵向布局时为纵向间隔。
* `itemFontSize`：图例项的字体大小。
* `formatter`：图例内容字符串模版格式器。支持用 `\n` 换行。模板变量为图例名称 `{name}`
* `data`：图例的数据数组。数组项通常为一个字符串，每一项代表一个系列的 `name`（如果是饼图，也可以是饼图单个数据的 `name`）。如果 `data` 没有被指定，会自动从当前系列中获取。指定 `data` 时里面的数据项和 `serie` 匹配时才会生效。

相关接口：

* `ClearData()`：清空数据。
* `ContainsData(string name)`：是否包括指定名字的图例。
* `RemoveData(string name)`：移除指定名字的图例。
* `AddData(string name)`：添加图例项。
* `GetData(int index)`：获得指定索引的图例。
* `GetIndex(string legendName)`：获得指定图例的索引。

## `Tooltip`

---

提示框组件。

相关参数：

* `show`：是否显示提示框组件。
* `type`：提示框指示器类型。指示器类型有：
  * `Line`：线性指示器。
  * `Shadow`：阴影指示器。
  * `None`：无指示器。
  * `Corss`：十字准星指示器。坐标轴显示Label和交叉线。
* `formatter`：提示框内容字符串模版格式器。支持用 `\n` 或 `<br/>` 换行。其中变量 `{a}`, `{b}`, `{c}`, `{d}` 在不同图表类型下代表数据含义为：
  * 折线（区域）图、柱状（条形）图、K线图 : `{a}`（系列名称），`{b}`（类目值），`{c}`（数值）, `{d}`（无）。
  * 散点图（气泡）图 : `{a}`（系列名称），`{b}`（数据名称），`{c}`（数值数组）, `{d}`（无）。
  * 地图 : `{a}`（系列名称），`{b}`（区域名称），`{c}`（合并数值）, `{d}`（无）。
  * 饼图、仪表盘、漏斗图: `{a}`（系列名称），`{b}`（数据项名称），`{c}`（数值）, `{d}`（百分比）。
* `fixedWidth`：固定宽度。当同时设置 `fixedWidth` 和 `minWidth` 时，`fixedWidth` 比 `minWidth` 优先级高。
* `fixedHeight`：固定高度。当同时设置 `fixedHeight` 和 `minHeight` 时，`fixedHeight` 比 `minHeight` 优先级高。
* `minWidth`：最小宽度。当同时设置 `fixedWidth` 和 `minWidth` 时，`fixedWidth` 比 `minWidth` 优先级高。
* `minHeight`：最小高度。当同时设置 f`ixedHeight` 和 `minHeight` 时，`fixedHeight` 比 `minHeight` 优先级高。

## `DataZoom`

---

区域缩放组件。用于区域缩放，从而能自由关注细节的数据信息，或者概览数据整体，或者去除离群点的影响。

相关参数：

* `show`：是否显示缩放区域。
* `type`：区域缩放类型：
  * `Inside`：内置于坐标系中，使用户可以在坐标系上通过鼠标拖拽、鼠标滚轮、手指滑动（触屏上）来缩放或漫游坐标系。
  * `Slider`：有单独的滑动条，用户在滑动条上进行缩放或漫游。
* `filterMode`：数据过滤类型：
  * `Filter`：当前数据窗口外的数据，被 过滤掉。即 会 影响其他轴的数据范围。每个数据项，只要有一个维度在数据窗口外，整个数据项就会被过滤掉。
  * `WeakFilter`：当前数据窗口外的数据，被 过滤掉。即 会 影响其他轴的数据范围。每个数据项，只有当全部维度都在数据窗口同侧外部，整个数据项才会被过滤掉。
  * `Empty`：当前数据窗口外的数据，被 设置为空。即 不会 影响其他轴的数据范围。
  * `None`：不过滤数据，只改变数轴范围。
* `orient`：布局方式是横还是竖。
  * `Horizonal`：水平。
  * `Vertical`：垂直。
* `xAxisIndex`：控制哪一个 `x` 轴。
* `yAxisIndex`：控制哪一个 `y` 轴。
* `showDataShadow`：是否显示数据阴影。数据阴影可以简单地反应数据走势。
* `showDetail`：是否显示 `detail`，即拖拽时候显示详细数值信息。
* `zoomLock`：是否锁定选择区域（或叫做数据窗口）的大小。如果设置为 `true` 则锁定选择区域的大小，也就是说，只能平移，不能缩放。
* `realtime`：拖动时，是否实时更新系列的视图。如果设置为 `false`，则只在拖拽结束的时候更新。
* `backgroundColor`：组件的背景颜色。
* `bottom`：组件离容器下侧的距离。
* `height`：组件高度。
* `rangeMode`：取值类型是取绝对值还是百分比。
  * `Percent`：百分比。
* `start`：数据窗口范围的起始百分比。范围是：0 ~ 100。
* `end`：数据窗口范围的结束百分比。范围是：0 ~ 100。
* `scrollSensitivity`：缩放区域组件的敏感度。值越高每次缩放所代表的数据越多。

## `Grid`

---

网格组件。直角坐标系内绘图网格，单个 `grid` 内最多可以放置上下两个 `X` 轴，左右两个 `Y` 轴。可以在网格上绘制折线图，柱状图，散点图（气泡图）。目前最多只能存在一个 `grid` 组件。

相关参数：

* `show`：是否显示直角坐标系网格组件。
* `left`：组件离容器左侧的距离。
* `right`：组件离容器右侧的距离。
* `top`：组件离容器顶部的距离。
* `bottom`：组件离容器底部的距离。
* `backgroundColor`：背景颜色。

## `XAxis`

---

直角坐标系 `grid` 中的 `X` 轴。单个 `grid` 组件最多只能放上下两个 `X` 轴。两个 `X` 轴存储在 `xAxises` 中。

相关参数：

* `show`：是否显示 `X` 轴。默认 `xAxises[0]` 为 `true`，`xAxises[1]` 为 `false`。
* `type`：坐标轴类型。默认为 `Category`。有以下两种类型：
  * `Value`：数值轴，用于连续数据。
  * `Category`：类目轴，适用于离散的类目数据，为该类型时必须通过 `data` 设置类目数据。
* `minMaxType`：坐标轴刻度最大最小值显示类型。默认为 `Default`。有以下三种类型：
  * `Default`：0-最大值。
  * `MinMax`：最小值-最大值。
  * `Custom`：自定义的最小值-最大值。
* `min`：设定的坐标轴刻度最小值，当 `minMaxType` 为 `Custom` 时有效。
* `max`：设定的坐标轴刻度最大值，当 `minMaxType` 为 `Custom` 时有效。
* `splitNumber`：坐标轴的分割段数。默认为 `5`。当 `splitNumber` 设为 `0` 时，表示绘制所有的类目数据。
* `interval`：强制设置坐标轴分割间隔。无法在类目轴中使用。设置改值时 `splitNumber` 无效。
* `splitLineType`：分割线类型。默认为 `Dashed`。有以下五种类型：
  * `None`：不显示分割线。
  * `Solid`：实线。
  * `Dashed`：虚线。
  * `Dotted`：点线。
  * `DashDot`：点划线。
  * `DashDotDot`：双点划线。
* `boundaryGap`：坐标轴两边是否留白。默认为 `true`。
* `maxCache`：类目数据中可缓存的最大数据量。默认为0没有限制，大于0时超过指定值会移除旧数据再插入新数据。
* `data`：类目数据，在类目轴（`type: 'Category'`）中有效。

相关接口：

* `ClearData()`：清空类目数据。
* `IsCategory()`：是否为类目轴。
* `IsValue()`：是否为数值轴。
* `AddData(string category, int maxDataNumber)`：添加一个类目到类目数据列表。

## `YAxis`

---

直角坐标系 `grid` 中的 `Y` 轴。单个 `grid` 组件最多只能放左右两个 `Y` 轴。两个 `Y` 轴存储在 `yAxises` 中。

相关参数：

* `show`：是否显示 `Y` 轴。默认 `yAxises[0]` 为 `true`，`yAxises[1]` 为 `false`。
* `type`：坐标轴类型。默认为 `Value`。有以下两种类型：
  * `Value`：数值轴，用于连续数据。
  * `Category`：类目轴，适用于离散的类目数据，为该类型时必须通过 `data` 设置类目数据。
* `minMaxType`：坐标轴刻度最大最小值显示类型。默认为 `Default`。有以下三种类型：
  * `Default`：0-最大值。
  * `MinMax`：最小值-最大值。
  * `Custom`：自定义的最小值-最大值。
* `min`：设定的坐标轴刻度最小值，当 `minMaxType` 为 `Custom` 时有效。
* `max`：设定的坐标轴刻度最大值，当 `minMaxType` 为 `Custom` 时有效。
* `splitNumber`：坐标轴的分割段数。默认为 `5`。
* `interval`：强制设置坐标轴分割间隔。无法在类目轴中使用。设置改值时 `splitNumber` 无效。
* `splitLineType`：分割线类型。默认为 `Dashed`。支持以下五种类型：
  * `None`：不显示分割线。
  * `Solid`：实线。
  * `Dashed`：虚线。
  * `Dotted`：点线。
  * `DashDot`：点划线。
  * `DashDotDot`：双点划线。
* `boundaryGap`：坐标轴两边是否留白。默认为 `false`。
* `data`：类目数据，在类目轴（`type: 'Category'`）中有效。

相关接口：

* `ClearData()`：清空类目数据。
* `IsCategory()`：是否为类目轴。
* `IsValue()`：是否为数值轴。
* `AddData(string category, int maxDataNumber)`：添加一个类目到类目数据列表。

## `Series`

---

系列列表。每个系列通过 type 决定自己的图表类型。

相关参数：

* `show`：系列是否显示在图表上。
* `type`：系列的图表类型。有以下几种类型：
  * `Line`：折线图。
  * `Bar`：柱状图。
  * `Pie`：饼图。
  * `Radar`：雷达图。
  * `Scatter`：散点图。
  * `EffectScatter`：带有涟漪特效动画的散点图。
* `name`：系列名称。用于 `tooltip` 的显示，`legend` 的图例筛选。
* `stack`：数据堆叠。同个类目轴上系列配置相同的 `stack` 值后，后一个系列的值会在前一个系列的值上相加。
* `axisIndex`：使用的坐标轴轴的 `index`，在单个图表实例中存在多个坐标轴轴的时候有用。
* `radarIndex`：雷达图所使用的 `radar` 组件的 `index`。
* `minShow`：系列显示数据的最小索引。
* `maxShow`：系列显示数据的最大索引。
* `maxCache`：系列中可缓存的最大数据量。默认为`0`没有限制，大于0时超过指定值会移除旧数据再插入新数据。
* `sampleDist`采样的最小水平像素距离，默认为`0`时不采样。当两个数据点间的水平像素距离小于该值时，开启采样，保证两点间的水平像素距离不小于该值。
* `sampleType`：采样类型。当`sampleDist`大于`0`时有效。支持以下五种采样类型：
  * `Peak`：取峰值。当过滤点的平均值大于等于`sampleAverage`时，取最大值；反之取最小值。
  * `Average`：取过滤点的平均值。
  * `Max`：取过滤点的最大值。
  * `Min`：取过滤点的最小值。
  * `Sum`：取过滤点之和。
* `sampleAverage`：设定的采样平均值。当 `sampleType` 为 `Peak` 时，用于和过滤数据的平均值做对比是取最大值还是最小值。默认为`0`时会实时计算所有数据的平均值。
* `areaStyle`：区域填充样式 `AreaStyle`。`AreaStyle`参数如下:
  * `show`：是否显示区域填充。
  * `origin`：区域填充的起始位置 `AreaOrigin`。有以下三种填充方式：
    * `Auto`：填充坐标轴轴线到数据间的区域。
    * `Start`：填充坐标轴底部到数据间的区域。
    * `End`：填充坐标轴顶部到数据间的区域。
  * `color`：区域填充的颜色，默认取 `serie` 对应的颜色。如果 `toColor` 不是默认值，则表示渐变色的起点颜色。
  * `toColor`：区域填充的渐变色的终点颜色。
  * `opacity`：图形透明度。支持从 0 到 1 的数字，为 0 时不绘制该图形。
* `symbol`：标记的图形 `SerieSymbol`：
  * `type`：标记类型。支持以下六种类型：
    * `EmptyCircle`：空心圆。
    * `Circle`：实心圆。
    * `Rect`：正方形。
    * `Triangle`：三角形。
    * `Diamond`：菱形。
    * `None`：不显示标记。
  * `sizeType`：标记图形的大小获取方式。支持以下三种类型：
    * `Custom`：自定义大小。
    * `FromData`：通过 `dataIndex` 从数据中获取，再乘以一个比例系数 `dataScale` 。
    * `Callback`：通过回调函数 `sizeCallback` 获取。
  * `size`：标记的大小。
  * `selectedSize`：被选中的标记的大小。
  * `dataIndex`：当 `sizeType` 指定为 `FromData` 时，指定的数据源索引。
  * `dataScale`：当 `sizeType` 指定为 `FromData` 时，指定的倍数系数。
  * `selectedDataScale`：当 `sizeType` 指定为 `FromData` 时，指定的高亮倍数系数。
  * `sizeCallback`：当 `sizeType` 指定为 `Callback` 时，指定的回调函数。
  * `selectedSizeCallback`：当 `sizeType` 指定为 `Callback` 时，指定的高亮回调函数。
  * `color`：标记图形的颜色，默认和系列一致。
  * `opacity`：图形标记的透明度。
  * `startIndex`：开始显示图形标记的索引。
  * `interval`：显示图形标记的间隔。0表示显示所有标签，1表示隔一个隔显示一个标签，以此类推。
  * `forceShowLast`：是否强制显示最后一个图形标记。默认为 `false`。
* `lineType`：折线图样式类型。支持以下十种类型：
  * `Normal`：普通折线图。
  * `Smooth`：平滑曲线。
  * `SmoothDash`：平滑虚线。
  * `StepStart`：阶梯线图：当前点。
  * `StepMiddle`：阶梯线图：当前点和下一个点的中间。
  * `StepEnd`：阶梯线图：下一个拐点。
  * `Dash`：虚线。
  * `Dot`：点线。
  * `DashDot`：点划线。
  * `DashDotDot`：双点划线。
* `lineStyle`：线条样式`LineStyle`。`LineStyle`参数如下：
  * `show`：是否显示线条。在折线图中无效。
  * `type`：线条类型。支持以下五种类型：
    * `None`：不显示分割线。
    * `Solid`：实线。
    * `Dashed`：虚线。
    * `Dotted`：点线。
    * `DashDot`：点划线。
    * `DashDotDot`：双点划线。
  * `color`：线条颜色。默认和 `serie` 一致。
  * `width`：线条宽。
  * `opacity`：线条的透明度。支持从 0 到 1 的数字，为 0 时不绘制该图形。
* `barWidth`：柱条的宽度，不设时自适应。支持设置成相对于类目宽度的百分比。
* `barGap`：不同系列的柱间距离。为百分比（如 `'0.3f'`，表示柱子宽度的 `30%`）。如果想要两个系列的柱子重叠，可以设置 `barGap` 为 `'-1f'`。这在用柱子做背景的时候有用。在同一坐标系上，此属性会被多个 `'bar'` 系列共享。此属性应设置于此坐标系中最后一个 `'bar'` 系列上才会生效，并且是对此坐标系中所有 `'bar'` 系列生效。
* `barCategoryGap`：同一系列的柱间距离，默认为类目间距的20%，可设固定值。在同一坐标系上，此属性会被多个 `'bar'` 系列共享。此属性应设置于此坐标系中最后一个 `'bar'` 系列上才会生效，并且是对此坐标系中所有 `'bar'` 系列生效。
* `pieClickOffset`：鼠标点击时是否开启偏移，一般用在PieChart图表中。
* `pieRoseType`：是否展示成南丁格尔图，通过半径区分数据大小。
* `pieSpace`：饼图项间的空隙留白。
* `pieCenter`：饼图的中心点。
* `pieRadius`：饼图的半径。`radius[0]` 表示内径，`radius[1]` 表示外径。
* `label`：图形上的文本标签 `SerieLabel`，可用于说明图形的一些数据信息，比如值，名称等。`SerieLabel` 的参数如下：
  * `show`：是否显示文本标签。
  * `position`：标签的位置。折线图时强制默认为 `Center`，支持以下 `5` 种位置：
    * `Outside`：饼图扇区外侧，通过视觉引导线连到相应的扇区。只在饼图种可用。
    * `Inside`：饼图扇区内部。只在饼图可用。
    * `Center`：在中心位置（折线图，柱状图，饼图）。
    * `Top`：顶部（柱状图）。
    * `Bottom`：底部（柱状图）。
  * `formatter`：标签内容字符串模版格式器。支持用 `\n` 换行。模板变量有：`{a}`：系列名；`{b}`：数据名；`{c}`：数据值；`{d}`：百分比。示例：`{b}:{c}`。
  * `offset`：距离图形元素的偏移。
  * `color`：自定义文字颜色，默认和系列的颜色一致。
  * `backgroundColor`：标签的背景色，默认无颜色。
  * `backgroundWidth`：标签的背景宽度。一般不用指定，不指定时则自动是文字的宽度。
  * `backgroundHeight`：标签的背景高度。一般不用指定，不指定时则自动是文字的高度。
  * `rotate`：标签的旋转。
  * `paddingLeftRight`：标签文字和边框的左右边距。
  * `paddingTopBottom`：标签文字和边框的上下边距。
  * `fontSize`：标签文字的字体大小。
  * `fontStyle`：标签文字的字体风格。
  * `line`：是否显示视觉引导线。在 `label` 位置 设置为 `'Outside'` 的时候会显示视觉引导线。
  * `lineType`：视觉引导线类型。支持以下几种类型：
    * `BrokenLine`：折线。
    * `Curves`：曲线。
    * `HorizontalLine`：水平线。
  * `lineColor`：视觉引导线自定义颜色。
  * `lineWidth`：视觉引导线的宽度。
  * `lineLength1`：视觉引导线第一段的长度。
  * `lineLength2`：视觉引导线第二段的长度。
  * `border`：是否显示边框。
  * `borderWidth`：边框宽度。
  * `borderColor`：边框颜色。
* `highlightLabel`：高亮时的文本标签配置 `SerieLabel`。参数同上。
* `animation`：起始动画 `Animation`。`Animation`的参数如下：
  * `enable`：是否开起始画效果。
  * `easing`：动画的缓动效果。支持以下动画效果：
    * `Linear`：线性效果。
  * `duration`：设定的动画时长，单位毫秒。
  * `threshold`：是否开启动画的阈值，当单个系列显示的图形数量大于这个阈值时会关闭动画。
  * `delay`：动画延时，单位毫秒。
* `lineArrow`：折线图的箭头 `LineArrow`。`LineArrow`的参数如下：
  * `show`：是否显示箭头。
  * `position`：箭头显示位置。支持以下两种位置：
    * `End`：末端显示。最后一个数据上显示箭头。
    * `Start`：起始端显示。第一个数据上显示箭头。
  * `width`：箭头宽。
  * `height`：箭头长。
  * `offset`：箭头偏移。默认箭头的中心点和数据坐标点一致，可通过 `offset` 调整偏移。
  * `dent`：箭头的凹度。
* `data`：系列中的数据项 `SerieData` 数组。`SerieData` 可以设置`1`到`n`维数据。`SerieData`的相关参数如下：
  * `name`：数据项名称。
  * `selected`：该数据项是否被选中。
  * `showIcon`：是否显示图标。
  * `iconImage`：图标的图片。
  * `iconColor`：图标颜色。
  * `iconWidth`：图标宽。
  * `iconHeight`：图标高。
  * `iconOffset`：图标偏移。

相关接口：

## Settings

---

全局配置。

* `large`：
* `minShowDataNumber`：图表所显示数据的最小索引。
* `maxShowDataNumber`：图表所显示数据的最大索引。
* `maxCacheDataNumber`：图表每个系列中可缓存的最大数据量。默认为0没有限制，大于`0`时超过指定值会移除旧数据再插入新数据。
* `lineSmoothStyle`：平滑折线图的平滑系数。
* `sampleDist`：采样的最小像素距离，默认为`0`时不采样。当两个数据点间的像素距离小于改值时，开启采样，保证两点间的像素距离不小于改值。

[返回首页](https://github.com/monitor1394/unity-ugui-XCharts)  
[XChartsAPI接口](XChartsAPI.md)  
[XCharts问答](XCharts问答.md)
