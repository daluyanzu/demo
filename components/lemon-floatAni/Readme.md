# 浮动动画组件



插件已支持 easycom 规范，直接导入即可使用



### 使用方法：

```
<floatAni :floatList="floatList"></floatAni>

floatList: ['我是人间惆怅客', '知君何事泪纵横', '断肠声里忆平生'],//传入需要浮动的内容数据即可
```



### 参数说明：

#### Props：

|    参数名    | 参数类型 | 必须 |                参数说明                 | 默认值  |   可选值   |
| :----------: | :------: | :--: | :-------------------------------------: | :-----: | :--------: |
|  floatList   |  Array   |  √   |  浮动内容数组，每次浮动为一项数组元素   |         |            |
|  showIndex   |  Number  |  ×   |         浮动开始元素下标，默认0         |         |            |
| fixPosition  |  String  |  ×   |              浮动定位位置               |  left   | left/right |
|  fixMargin   |  Number  |  ×   |      浮动 left/right 边距，单位px       |   10    |            |
|  animation   |  Number  |  ×   |       动画及数据循环总时长，单位s       |   10    |            |
|   bgColor    |  String  |  ×   |            浮动内容背景颜色             | #d70130 |            |
| beginMargin  |  Number  |  ×   | 浮动开始位置距离屏幕顶部的距离，单位 px |   400   |            |
|  endMargin   |  Number  |  ×   | 浮动结束位置距离屏幕顶部的距离，单位 px |   20    |            |
| beginOpacity |  Number  |  ×   |         浮动开始位置元素透明度          |   0.4   |            |
|  endOpacity  |  Number  |  ×   |         浮动结束位置元素透明度          |   0.9   |            |
|  textColor   |  String  |  ×   |            浮动内容文字颜色             | #ffffff |            |
|   textSize   |  Number  |  ×   |        浮动内容文字大小，单位 px        |   12    |            |

#### Methods:

| 方法名 |                   方法说明                    |
| :----: | :-------------------------------------------: |
| choose | 浮动内容被点击时，向父级传递被点击的元素index |

##### 注：组件内部实现了采取了slot，可自定义浮动内容

```
<floatAni :floatList="floatList">
自定义内容（将覆盖原本内容）
</floatAni>


<template #showTextHead>
	在内容前插入内容
</template>

<template #showTextFoot>
	在内容后插入内容
</template>
```

