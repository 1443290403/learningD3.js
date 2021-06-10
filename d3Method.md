# D3 METHOD

## 一. D3选择元素的两种方法  
   - **select()** - 通过匹配给定的CSS选择器，仅选择一个DOM元素。 如果给定的CSS选择器有多个元素，则仅选择第一个元素。  
        - select（）方法根据CSS选择器选择HTML元素。 在CSS选择器中，您可以通过以下三种方式定义和访问HTML元素  
            1. HTML元素的标记（例如div，h1，p，span等）
            2. HTML元素的类名
            3. HTML元素的ID
   - **selectAll()** - 通过匹配给定的CSS选择器来选择所有DOM元素。 如果您熟悉使用jQuery选择元素，则D3.js选择器几乎相同。 
        - selectAll（）方法用于选择HTML文档中的多个元素。 select方法选择第一个元素，但selectAll方法选择与特定选择器字符串匹配的所有元素。 如果选择匹配none，则返回空选择。 我们也可以在selectAll（）方法中链接所有附加的修改方法， append(), html(), text(), attr(), style(), classed(),等。 在这种情况下，方法将影响所有匹配元素。  

        ```javascript 
            d3.selectAll(".d3Sa").attr("style", "color: green");
            d3.selectAll(".d3Sa").text('d3sa');
        ```
## 二. D3添加DOM元素的方法  
   - **append()** - 将新元素作为当前选择中元素的最后一个子元素附加。 此方法还可以修改元素的样式，其属性，属性，HTML和文本内容。  

   - **text()** - 用于设置所选/附加元素的内容。  
## 二. D3修改DOM元素的方法  
   - **html()** - 用于设置所选/附加元素的html内容。   

   - **attr()** - 用于添加或更新所选元素的属性。  

   - **style()** - 用于设置所选元素的样式属性。  

   - **classed()** - 专门用于设置HTML元素的“class”属性。 因为，单个HTML元素可以有多个类; 在为HTML元素分配类时，我们需要小心。 此方法知道如何处理元素上的一个或多个类，并且它将具有高性能。  
        - 设置class:
     ```html
        <div></div>
     ```
     ```javascript 
        let div = document.query;
        div.classed("d3div", false);
        div.classed("d3div", true);
     ```
        - 反选class(Toggle class):将类翻转到相反的状态如果它已经存在则将其删除，如果它尚不存在则添加它您可以执行以下操作之一。
     ```javascript 
        div.classed("d3No", !div.classed("d3No"))
     ```
## 三. D3 Data Join(数据加入/数据链接)  
   <p style="text-indent:2em;">
        数据连接是D3.js中的另一个重要概念。 它与选择一起使用，使我们能够根据我们的数据集（一系列数值）操作HTML文档。 默认情况下，D3.js在其方法中为数据集提供最高优先级，并且数据集中的每个项对应于HTML元素。
   </p>  

- ### 什么是数据加入
   
   <p style="text-indent:2em;">
        数据连接使我们能够根据现有HTML文档中的数据集注入，修改和删除元素（HTML元素以及嵌入的SVG元素）。 默认情况下，数据集中的每个数据项对应于文档中的元素（图形）。
   </p>
   <p style="text-indent:2em;">
        随着数据集的变化，也可以轻松地操作相应的元素。 数据连接在我们的数据和文档的图形元素之间创建了一种紧密的关系。 数据连接使得基于数据集的元素操作变得非常简单和容易。
   </p>

- ### 数据加入如何工作？
   <p style="text-indent:2em;">
        数据连接的主要目的是使用给定的数据集映射现有文档的元素。 它根据给定的数据集创建文档的虚拟表示，并提供使用虚拟表示的方法。 让我们考虑一个简单的数据集，如下所示。
   </p>  

     ```html
        
            数据集有五个项目，因此可以映射到文档的五个元素。 让我们使用选择器的selectAll（）方法和数据连接的data（）方法将它映射到以下文档的li元素。
            现在，文档中有五个虚拟元素。 前两个虚拟元素是文档中定义的两个li元素，如下所示。
        <ul id="list">
            <li></li>
            <li></li>
        </ul>
     ```
     ```javascript 
        let dataArr = [10, 20, 30, 25, 15];  
        d3.select("#list").selectAll("li").data(dataArr).text((d)=>d);

        对于前两个li ，我们可以使用所有选择器的元素修改方法，如attr(), style(), text()等，如下所示。
        text()方法中的函数用于获取li元素映射数据。 这里， d表示第一个li元素为10，第二个li元素为20。
        接下来的三个元素可以映射到任何元素，可以使用数据连接的enter()和selector的append()方法完成。 enter()方法提供对剩余数据的访问（未映射到现有元素），append()方法用于从相应数据创建新元素。 让我们为剩余的数据项创建li 
     ```

