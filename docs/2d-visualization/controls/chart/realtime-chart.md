# 实时趋势

实时趋势图是一种用于显示数据随时间实时变化的图表。X轴是时间轴，Y轴是数据轴。

![alt text](1.png)

**属性**

| 名称| 描述   |
|:----------|:--------------------|
| 名字     | 此控件的名称。  |
| X        | 控件左侧距画布左侧的距离，单位px。 |
| Y        | 控件顶部距画布顶部的距离，单位px。   |
| W        | 控件的宽度，单位px。    |
| H        | 控件的高度，单位px。 |
| 数据     | 设置实时趋势图的数据来源及样式。  <br>![alt text](2.png)  点击该按钮可以设置曲线的数据源和样式。  <br>![alt text](3.png) <br>- **变量**：设置线条的数据来源。  <br>点击变量栏最右侧的如下符号，可以将变量的路径直接复制到名称栏。  <br>![alt text](4.png)  <br>- **名称**：设置线条名称。<br>- **Y轴**：选择一个Y轴，作为当前变量的Y轴。<br>- **线条颜色**：设置线条的颜色。<br>- **线条类型**：设置线条的类型。 <br>- **线条样式**：设置线条的样式。 <br>- **线宽**：设置线条的粗细。 <br>- **区域填充**：设置线条和轴之间的区域背景色。 <br>- **报警线**：设置是否将变量的报警值作为一条直线显示在当前控件上。  点击报警线的设置按钮，选择需要显示的报警线，并为其设置样式。  勾选报警线的checkbox，用于在控件上启用报警线的显示。<br>- **标记样式**：设置线条连接点的样式。 <br>- **标记大小**：设置线条连接点的大小，单位px。 <br>- **小数位**：鼠标移到线条上所显示的数值的小数位数。   |
| 刷新频率 | 按此频率对控件上的数据进行刷新。     |
| 显示     |选择变量按钮：控制 **选择变量按钮** 的显示、隐藏。显示的情况下，在运行页面可以通过此按钮重新设置变量及其对应曲线的显示样式。|
| 按钮样式 |选择变量按钮：设置 **选择变量按钮** 的颜色。|
| 颜色     | 设置控件的颜色效果。<br>- **背景**：控件的整体背景色。 <br>- **栅格**：栅格的线条颜色。  <br>- **X轴**：X轴的轴线颜色。|
| 边距     | 设置实时趋势图与其选中框之间的间距。确保图表能清晰显示，并为图表元素（如时间或图例）预留足够的空间。 |
| X轴      | 设置X轴的样式。<br>- **显示栅格**：控制栅格的显示、隐藏。<br>- **时间格式**：设置X轴显示的时间的格式,可以选择系统预置的时间格式，也可以手动输入，设置的时间格式须符合Echarts的时间格式要求，详见： [https://echarts.apache.org/zh/option.html#xAxis.axisLabel.formatter](https://echarts.apache.org/zh/option.html#xAxis.axisLabel.formatter)<br>**(4.2.1及其以上版本，支持此功能)** <br>- **时间范围**：X 轴显示的时间范围。<br>- **字体**：设置X轴显示的文字的字体、字体大小、粗体、斜体、字体颜色。|   
| Y轴      | 设置Y轴的样式。 <br>- **显示栅格**：控制栅格的显示、隐藏。<br>- **启用子图**：控制主图表中是否允许嵌入另一个图表。<br>- **分度数**：设置在Y轴上插入的分割线数量。<br>- **轴**：显示轴的行列数。  <br>![alt text](5.png)  点击该按钮可以设置轴的样式。   <br>![alt text](6.png) <br>- **名称**：Y轴的名称。<br>- **自动显示范围**：Y轴的量程根据值的范围动态变化。如果选中，则将自动确定Y轴的值范围。如果未选中，则将使用最小值和最大值。  <br>选择自动后，最小值和最大值变为失效状态。 <br>- **最小值**：Y轴的最小值。 <br>- **最大值**：Y轴的最大值。 <br>- **小数位**：设置Y轴的刻度值上显示的小数位数。<br>- **显示**：控制Y轴的显示、隐藏。 <br>- **位置**：设置Y轴的显示位置。 <br>- **偏移**：设置Y轴相对于默认位置的偏移。<br>- **轴颜色**：设置Y轴的颜色。<br>- **字体**：设置Y轴坐标的字体。 <br>- **字体大小**：设置Y轴坐标的字体大小。 <br>- **字体颜色**：设置Y轴坐标的字体颜色。<br>- **字体粗细**：设置Y轴坐标的字体粗细。<br>- **字体倾斜**：设置Y轴坐标的字体倾斜。 <br>- **子图权重**：设置子图在主图表中所占的空间大小。  <br>- **子图背景**：设置子图的背景色。   |
| 图例     | 设置图例的样式。<br>- **显示**：控制图例的显示、隐藏。默认显示。<br>- **位置**：设置图例的显示位置。   <br>- **字体**：设置图例的字体、字体大小、粗体、斜体、字体颜色。|
| 右键菜单 | 在控件上设置右键菜单，可以设置菜单的背景色、边框色、字体型号、字体大小、字体颜色、加粗、倾斜。可以为右键菜单配置对应的动作，包括：导航，变量赋值，属性赋值和执行脚本。  在运行许页面，在控件上单击鼠标右键，显示右键菜单。**(4.2.2及其以上版本，支持此功能)**  |

**说明**：实时趋势控件基于Echarts 5.x版本开发，该版本上分度数存在缺陷，不按设置的数值生效，导致实时趋势图也存在此问题。请等待Echarts修复该缺陷。

**动作**

允许您基于某种条件执行特定的动作。请参阅“[动作](../../event/index.md)”页上各种动作的完整描述。

**示例1**

使用实时趋势来显示水温。

1. 在画面上插入一个实时趋势图。
2. 设置实时趋势图的属性。

| 属性 | 值   |
|:---------|:---------------|
| X轴      | 关闭栅格的显示。|
| Y轴      | 关闭栅格的显示。|
| 数据     | 绑定变量，设置曲线的样式。 <br>![alt text](7.png) <br>- **变量**：@工厂:水温 <br>- **名称**：水温    <br>- **Y轴**：水温     <br>- **线条颜色**：#6ec800   <br>- **线条类型**：折线     <br>- **线条样式**：实线   <br>- **线宽**：1   <br>- **区域填充**：未启用  <br>- **报警线**：未启用  <br>- **标记样式**：无  <br>- **标记大小**：6    <br>- **小数位**：2  |

3. 点击预览按钮进行预览。

    ![alt text](8.png)

**示例2**

使用实时趋势来显示水温，并显示水温报警线。

1. 在画面上插入一个实时趋势图。
2. 设置实时趋势图的属性。

    | 属性 | 值  |
    |:----------|:-------------------|
    | X轴      | 关闭栅格的显示。 |
    | Y轴      | 关闭栅格的显示。  |
    | 数据     | 绑定变量，设置曲线的样式。<br>![alt text](9.png) <br>- **变量**：`@Demo:temperature` <br>- **名称**：水温 <br>- **Y轴**：水温  <br>- **线条颜色**：#6ec800  <br>- **线条类型**：折线  <br>- **线条样式**：实线 <br>- **线宽**：1  <br>- **区域填充**：未开启  <br>- **报警线**：开启。选择高温报警，将线条颜色设置为红色，样式设置为虚线。  <br>![alt text](10.png) <br>- **标记样式**：无  <br>- **标记大小**：6  <br>- **小数位**：2  |

3. 点击预览按钮进行预览，红色的虚线为水温的报警线。通过报警线可以只管的判断出，在哪些时刻变量产生了报警。

    ![alt text](11.png)

**示例3**

使用实时趋势来显示水温，并可以在运行时随时添加水温参考线。

1. 在画面上插入一个实时趋势图，并绑定变量: Demo:temperature
2. 配置一个添加参考线的弹窗：AddMarkLine，用于在运行页面在趋势图上添加参考线

    ![alt text](12.png)

    点击“确定”按钮，在动作属性中设置 **按下** 动作脚本

    ```typescript

    const value = await System.Page.getPropertyValue('Value输入框1#value')
    const lineName = await System.Page.getPropertyValue('Name输入框1#text')
    const lineColor = await System.Page.getPropertyValue('Color输入框1#text')
    const lineStyle = await System.Page.getPropertyValue('Style下拉框1#selectedText')
    const lineWidth = await System.Page.getPropertyValue('Width输入框1#value')
    const model = {
        value: value,
        name: lineName,
        lineColor: lineColor,
        lineStyle: lineStyle,
        lineWidth: lineWidth
    };
    System.UI.close(model)
    ```
    
    点击“取消”按钮，在动作属性中设置 **按下** 动作脚本

    ```typescript
    System.UI.close()
    ```
 
3. 配置一个删除参考线的弹窗：DeleteMarkLine，用于在运行页面根据参考线的名称，在趋势图上删除参考线

    ![alt text](13.png)

    点击“确定”按钮，在动作属性中设置 **按下** 动作脚本

    ```typescript
    const value = await System.Page.getPropertyValue('文本输入框1#text')
    System.UI.close(value)
    ```
    
    点击“取消”按钮，在动作属性中设置 **按下** 动作脚本

    ```typescript
    System.UI.close()
    ```
 
4. 在实时趋势图上配置右键菜单

    ![alt text](14.png)

    AddMarkLine: 用于添加参考线

    RemoveMarkLine: 按照参考线名称，删除参考线

    RemoveAllMarkLine：删除所有已添加的参考线。如果不指定名称，则删除所有参考线。

    在右键菜单中，点击AddMarkLine的动作按钮，在弹出的窗口中编写如下脚本：

    ```typescript
    const popup = await System.UI.openPopup('AddMarkLine')
    console.log(popup)
    if(!popup){
        return;
    }
    const chart = await System.UI.findControl('RealTimeChart1')
    chart.addMarkLine(popup);
    ```
    
    点击DeleteMarkLine的动作按钮，在弹出的窗口中编写如下脚本：

    ```typescript
    const popup = await System.UI.openPopup('RemoveLine')
    console.log(popup)
    if(!popup){
        return;
    }
    const chart = await System.UI.findControl('RealTimeChart1')
    chart.removeMarkLine(popup);
    ```
    
    点击DeleteAllMarkLine的动作按钮，在弹出的窗口中编写如下脚本：

    ```typescript
    const chart = await System.UI.findControl('RealTimeChart1')
    chart.removeMarkLine()
    ```

5. 在运行页面上，在趋势图上右击鼠标，点击AddMarkLine，弹出AddMarkLine弹窗，设置参考参考线样式后点击 确定按钮，完成添加。

     ![alt text](15.gif)

6. 在运行页面上，在趋势图上右击鼠标，点击DeleteMarkLine，输入要删除的参考线的名称，删除该参考线。

     ![alt text](16.gif)

7. 在运行页面上，在趋势图上右击鼠标，点击DeleteAllMarkLine，删除所有添加的参考线。

     ![alt text](17.gif)







