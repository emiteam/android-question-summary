# Android Shape的基本用法

填充：设置填充的颜色

间隔：设置四个方向上的间隔

大小：设置大小

圆角：同时设置五个属性，则Radius属性无效


```
android:Radius="20dp"                     设置四个角的半径
android:topLeftRadius="20dp"              设置左上角的半径 
android:topRightRadius="20dp"             设置右上角的半径 
android:bottomLeftRadius="20dp"           设置右下角的半径 
android:bottomRightRadius="20dp"          设置左下角的半径
```
描边：dashWidth和dashGap属性，只要其中一个设置为0dp，则边框为实现边框
```
android:width="20dp"                            设置边边的宽度 
android:color="@android:color/black"            设置边边的颜色 
android:dashWidth="2dp"                         设置虚线的宽度 
android:dashGap="20dp"                          设置虚线的间隔宽度
```
渐变：当设置填充颜色后，无渐变效果。angle的值必须是45的倍数（包括0），仅在type="linear"有效，不然会报错。android:useLevel 这个属性不知道有什么用。