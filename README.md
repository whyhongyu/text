称明：
==================
       1. vue里面   let vm = new Vue();   this === vm;
       2. v-..都是Vue的指令  v-on是事件指令可以简写@ 如：v-no:click => @click
       3. v-bind:是绑定指令  可以简写成：   如要给一个元素绑定一个属性data-id =>
       4. v-bind:data-id 简写成 ：data-id

指令:  
====================
         1.v-model双向绑定数据
         2.v-for循环
         3.v-show 显示与隐藏
         4.v-if显示与隐藏  （dom元素的删除添加(是否渲染)   个人理解）
         5.v-else 与 v-if 一起出现
         6.v-else-if
         7.v-bind
         8.v-on 事件
         9.v-text读取文本不能读取html标签
         10.v-html  能读取html标签
         11.v-class 类名
         12.v-style
         13.v-once  就是  加载一次  如果用到事件中就是事件只执行一次（@click.once="show"）
         14.v-cloak防闪烁
         15.v-pre  把标签内部的元素原位输出 也就是说不会解析任何指令 如 {{msg}}  大括号也会被输出

修饰符  
=====================
        在事件处理程序中调用 event.preventDefault() 或 event.stopPropagation() 是非常常见的需求。
       
        尽管我们可以在 methods 中轻松实现这点，但更好的方式是：methods 只有纯粹的数据逻辑，而不是去处理 DOM 事件细节。
       
        为了解决这个问题，Vue.js 为 v-on 提供了事件修饰符。通过由点 (.) 表示的指令后缀来调用修饰符。

            1. .stop
            2. .prevent
            3. .capture
            4. .self
            5. .once
            <!-- 阻止单击事件冒泡 -->
            
            <a v-on:click.stop="doThis"></a>
           
            <!-- 提交事件不再重载页面 -->
            
            <form v-on:submit.prevent="onSubmit"></form>
            
            <!-- 修饰符可以串联 -->
            
            <a v-on:click.stop.prevent="doThat"></a>
            
            <!-- 只有修饰符 -->
             
            <form v-on:submit.prevent></form>
            
            <!-- 添加事件侦听器时使用事件捕获模式 -->
            
            <div v-on:click.capture="doThis">...</div>
            
            <!-- 只当事件在该元素本身 (比如不是子元素) 触发时触发回调 -->
            
            <div v-on:click.self="doThat">...</div>
            
            使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 @click.prevent.self 会阻止所有的点击，
            
            而 @click.self.prevent 只会阻止元素上的点击。
            

3、声明式渲染
--------------------
      `<div id="app">
            {{ message }}
       </div>

        let app = new Vue({
            el: '#app',
            data: {
                message: 'Hello Vue!'
            }
        })
       `
    输出结果：Hello Vue!

4、是否渲染 v-if
--------------------
       `
       <div id="app-3">
         <p v-if="seen">现在你看到我了</p>
       </div>
       let app3 = new Vue({
         el: '#app-3',
         data: {
           seen: true
         }
       })
       `
       控制data里面的seen的值就能控制浏览器是否渲染，这里和display的显隐是不一样的，display是浏览器已经渲染出来了，

       只是不显示出来而已（在控制台上可以看到该元素），这里的控制是让浏览器不渲染出来，也就是看不到这个元素，控制台也看不到。

       app3.seen="true/false"   this.seen="true/false"  都可以控制;


5、循环 v-for
---------------------
       `
       <div id="app-4">
         <ol>
           <li v-for="todo in todos">
             {{ todo.text }}
           </li>
         </ol>
       </div>
       var app4 = new Vue({
         el: '#app-4',
         data: {
           todos: [
             { text: '学习 JavaScript' },
             { text: '学习 Vue' },
             { text: '整个牛项目' }
           ]
         }
       })
       `
输出结果: 1.学习 JavaScript

         2.学习 Vue
         
         3.整个牛项目

       这个指令在我们后台使用的话可以很有效的提高性能，不用操作DOM 只要控制数据就可以;

       在控制台里，输入 app4.todos.push({ text: '新项目' })，你会发现列表中添加了一个新项
       
  
6、双向绑定
------------------
       `
       <div id="app-6">
         <p>{{ message }}</p>
         <input v-model="message">
       </div>
       var app6 = new Vue({
         el: '#app-6',
         data: {
           message: 'Hello Vue!'
         }
       })
              `
       把代码放到页面上看的话就是两行文字,第一行： Hello Vue!  第二行是一个输入框，里面写着Hello Vue!

       只要第二行输入框里面的值改变了，第一行也就会改变，说的双向绑定说的很高大上。其实个人认为也就是跟

       oninput事件差不多,这是第一点;

       双向绑定在早期的时候在组件是能双向绑定的，但是后来发现AngularJS（AngularJS 1）中双向绑定太过复杂，让初学者望而却步；

       考虑到方方面面的原因之后，Vue 在不同组件间强制使用单向数据流。这使应用中的数据流更加清晰易懂。


