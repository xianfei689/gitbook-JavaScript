# 事件委托&事件冒泡

* 事件委托/事件代理

  * 什么时候用到？for 循环里面 多个点击事件，一次操作就可以完成，减少DOM操作次数
  * 原理：利用事件的`冒泡原理`来实现，

  ```text
    <ul>
      <li> 1</li>
      <li> 2</li>
      <li> 3</li>
      <li> 4</li>
      <li> 5</li>
    </ul>
  ```

  ```text
  // 很蠢的对每个li 标签都循环做点击事件
   window.onload= function(){
     var ul = document.querySelector('ul')
     var li = document.querySeletcor('li')
     for(var i=0;i<li.length;i++){
       li[i].onclick=function(){
         alert(123)
       }
     }
   }
  ```

* 事件冒泡

  * 什么是冒泡原理？
  * 什么是事件冒泡？

  > 事件从最深的节点开始，逐步向上传播事件，div&gt;ul&gt;li&gt;a ，给a添加事件，事件就会一层一层的往外执行，执行顺序为a-&gt;li-&gt;ul-&gt;div

  * 机制

  > 给最外面的div加点击事件，`这里理解？：它的后代都会被点击到`那么 ul li a 做点击的时候，都会冒泡到最外层div，也就是会触发。这就是事件委托，委托父级代为执行事件。反正最后都会被冒泡到？？

  * 事件冒泡和事件捕获
    * 捕获阶段`父级->子级，向里`
      * 检查最外层`html`，是否在捕获阶段注册一个`onclick`事件处理程序，如果是，则运行
      * 然后移动到下一个元素，并执行相同操作，直到实际点击的元素
      * **结论是：事件始终从html层开始？**
      * 顺序：父级——&gt;子级 、外到里
    * 冒泡阶段 `子级->父级，向外`

      * 检查实际点击元素是否在冒泡阶段注册`onclick`事件，如果是则运行
      * 然后移动到直接祖先，然后同上，直至`html`元素
      * 时间处理程序都在冒泡阶段注册 `(但可以使用addEventLisenter(,,true) 在捕获阶段注册`

      ```text
        video.onclick=function(e){
          e.stopProgation();//阻止冒泡链扩大
          video.play()//播放视频
        }
      ```

    * 事件委托`由于冒泡而被允许的概念`
      * 通过委托父级，addEventLisenter 设置在父节点上，将事件监听器气泡的影响每个子节点，而不是每个子节点都设置事件监听器

