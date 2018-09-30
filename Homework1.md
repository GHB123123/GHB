# 一.Learning of vue.js

# 1.介绍

Vue 是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。

# 2.起步

1）每个 Vue 应用都需要通过实例化 Vue 来实现。
语法格式如下：

    var vm = new Vue({
      // 选项
    })

在 Vue 构造器中有一个el 参数，它是 DOM 元素中的 id

2）如何定义数据对象。

data 用于定义属性，实例中有三个属性分别为：site、url、alexa。

methods 用于定义的函数，可以通过 return 来返回函数值。

{{ }} 用于输出对象属性和函数返回值。

当一个 Vue 实例被创建时，它向 Vue 的响应式系统中加入了其 data 对象中能找到的所有的属性。当这些属性的值发生改变时，html 视图将也会产生相应的变化。

# 3.模拟语法

1)Vue.js 使用了基于 HTML 的模板语法，允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据。所有 Vue.js 的模板都是合法的 HTML ，所以能被遵循规范的浏览器和 HTML 解析器解析。在底层的实现上，Vue 将模板编译成虚拟 DOM 渲染函数。结合响应系统，Vue 能够智能地计算出最少需要重新渲染多少组件，并把 DOM 操作次数减到最少。

2）插值

文本

数据绑定最常见的形式就是使用“Mustache”语法 (双大括号) 的文本插值。

HTML

双大括号会将数据解释为普通文本，而非 HTML 代码。为了输出真正的 HTML，你需要使用 v-html 指令。

特性

Mustache 语法不能作用在 HTML 特性上，遇到这种情况应该使用 v-bind 指令。

表达式

迄今为止，在我们的模板中，我们一直都只绑定简单的属性键值。但实际上，对于所有的数据绑定，Vue.js 都提供了完全的 JavaScript 表达式支持。

3）指令

指令 (Directives) 是带有 v- 前缀的特殊特性。指令特性的值预期是单个 JavaScript 表达式 。指令的职责是，当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM。

参数

一些指令能够接收一个“参数”，在指令名称之后以冒号表示。例如，v-bind 指令可以用于响应式地更新 HTML 特性。

修饰符

修饰符 (Modifiers) 是以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。

4）缩写

v- 前缀作为一种视觉提示，用来识别模板中 Vue 特定的特性。当你在使用 Vue.js 为现有标签添加动态行为 (dynamic behavior) 时，v- 前缀很有帮助，然而，对于一些频繁用到的指令来说，就会感到使用繁琐。同时，在构建由 Vue.js 管理所有模板的单页面应用程序 (SPA - single page application) 时，v- 前缀也变得没那么重要了。因此，Vue.js 为 v-bind 和 v-on 这两个最常用的指令，提供了特定简写：

v-bind 缩写：

    <!-- 完整语法 -->
    <a v-bind:href="url">...</a>
    <!-- 缩写 -->
    <a :href="url">...</a>

v-on 缩写：

    <!-- 完整语法 -->
    <a v-on:click="doSomething">...</a>
    <!-- 缩写 -->
    <a @click="doSomething">...</a>

# 4.条件语句

1）v-if

在字符串模板中，比如 Handlebars，我们得像这样写一个条件块：

    <!-- Handlebars 模板 -->
    {{#if ok}}
      <h1>Yes</h1>
    {{/if}}
    
在 Vue 中，我们使用 v-if 指令实现同样的功能：

    <h1 v-if="ok">Yes</h1>

也可以用 v-else 添加一个“else 块”：

    <h1 v-if="ok">Yes</h1>
    <h1 v-else>No</h1>

因为 v-if 是一个指令，所以必须将它添加到一个元素上。但是如果想切换多个元素呢？此时可以把一个 <template> 元素当做不可见的包裹元素，并在上面使用 v-if。最终的渲染结果将不包含 <template> 元素。
  
2）v-else

你可以使用 v-else 指令来表示 v-if 的“else 块”：

    <div v-if="Math.random() > 0.5">
      Now you see me
    </div>
    <div v-else>
      Now you don't
    </div>

v-else 元素必须紧跟在带 v-if 或者 v-else-if 的元素的后面，否则它将不会被识别。

3）v-else-if

v-else-if，顾名思义，充当 v-if 的“else-if 块”，可以连续使用。类似于 v-else，v-else-if 也必须紧跟在带 v-if 或者 v-else-if 的元素之后。

4）v-show

另一个用于根据条件展示元素的选项是 v-show 指令。用法大致一样：

    <h1 v-show="ok">Hello!</h1>

不同的是带有 v-show 的元素始终会被渲染并保留在 DOM 中。v-show 只是简单地切换元素的 CSS 属性 display。

注意！v-show 不支持 <template> 元素，也不支持 v-else。
  
5）v-if vs v-show

v-if 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。

v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。

相比之下，v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。

一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。

# 5.循环语句

1)循环使用 v-for 指令。

v-for 指令需要以 site in sites 形式的特殊语法， sites 是源数据数组并且 site 是数组元素迭代的别名。

v-for 可以绑定数据到数组来渲染一个列表,也可以用 v-for 通过一个对象的属性来迭代。

2)v-for on a <template>

类似于 v-if，你也可以利用带有 v-for 的 <template> 渲染多个元素。比如：
  
    <ul>
      <template v-for="item in items">
        <li>{{ item.msg }}</li>
        <li class="divider" role="presentation"></li>
      </template>
    </ul>

3)v-for with v-if

当它们处于同一节点，v-for 的优先级比 v-if 更高，这意味着 v-if 将分别重复运行于每个 v-for 循环中。当你想为仅有的一些项渲染节点时，这种优先级的机制会十分有用，如下：

    <li v-for="todo in todos" v-if="!todo.isComplete">
      {{ todo }}
    </li>

上面的代码只传递了未完成的 todos。

而如果你的目的是有条件地跳过循环的执行，那么可以将 v-if 置于外层元素 (或 <template>)上。如：

    <ul v-if="todos.length">
      <li v-for="todo in todos">
        {{ todo }}
      </li>
    </ul>
    <p v-else>No todos left!</p>

# 6.计算属性和侦听器

1)计算属性
模板内的表达式非常便利，但是设计它们的初衷是用于简单运算的。在模板中放入太多的逻辑会让模板过重且难以维护。例如：

    <div id="example">
      {{ message.split('').reverse().join('') }}
    </div>
    
在这个地方，模板不再是简单的声明式逻辑。你必须看一段时间才能意识到，这里是想要显示变量 message 的翻转字符串。当你想要在模板中多次引用此处的翻转字符串时，就会更加难以处理。

所以，对于任何复杂逻辑，你都应当使用计算属性。

2)计算属性 vs 侦听属性

Vue 提供了一种更通用的方式来观察和响应 Vue 实例上的数据变动：侦听属性。当你有一些数据需要随着其它数据变动而变动时，你很容易滥用 watch——特别是如果你之前使用过 AngularJS。然而，通常更好的做法是使用计算属性而不是命令式的 watch 回调。

3)计算属性的 setter

计算属性默认只有 getter ，不过在需要时你也可以提供一个 setter ：

    // ...
    computed: {
      fullName: {
        // getter
        get: function () {
          return this.firstName + ' ' + this.lastName
        },
        // setter
        set: function (newValue) {
          var names = newValue.split(' ')
          this.firstName = names[0]
          this.lastName = names[names.length - 1]
        }
      }
    }
    // ...
    
现在再运行 vm.fullName = 'John Doe' 时，setter 会被调用，vm.firstName 和 vm.lastName 也会相应地被更新。

4)侦听器

虽然计算属性在大多数情况下更合适，但有时也需要一个自定义的侦听器。这就是为什么 Vue 通过 watch 选项提供了一个更通用的方法，来响应数据的变化。当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。

# 7.事件处理

1）事件监听可以使用 v-on 指令。然而许多事件处理逻辑会更为复杂，所以直接把 JavaScript 代码写在 v-on 指令中是不可行的。因此 v-on 还可以接收一个需要调用的方法名称。除了直接绑定到一个方法，也可以在内联 JavaScript 语句中调用方法。

2）事件修饰符

在事件处理程序中调用 event.preventDefault() 或 event.stopPropagation() 是非常常见的需求。尽管我们可以在方法中轻松实现这点，但更好的方式是：方法只有纯粹的数据逻辑，而不是去处理 DOM 事件细节。

为了解决这个问题，Vue.js 为 v-on 提供了事件修饰符。之前提过，修饰符是由点开头的指令后缀来表示的。

.stop

.prevent

.capture

.self

.once

.passive

注意！使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 v-on:click.prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击。

3）按键修饰符

在监听键盘事件时，我们经常需要检查常见的键值。Vue 允许为 v-on 在监听键盘事件时添加按键修饰符。

记住所有的 keyCode 比较困难，所以 Vue 为最常用的按键提供了别名。

全部的按键别名：

.enter

.tab

.delete (捕获“删除”和“退格”键)

.esc

.space

.up

.down

.left

.right

可以通过全局 config.keyCodes 对象自定义按键修饰符别名。

4）系统修饰键

可以用如下修饰符来实现仅在按下相应按键时才触发鼠标或键盘事件的监听器：

.ctrl

.alt

.shift

.meta

5）鼠标按钮修饰符

.left

.right

.middle

这些修饰符会限制处理函数仅响应特定的鼠标按钮。




# 二.Comprision of Vue、React and Angular

# 1.Angular特性：

1)由自己实现一套模板编译规则，数据变化依赖脏检查。

2）基本属性包括：数据双向绑定、基本模板指令、自定义指令、表单验证、路由操作、依赖注入、过滤器、内置服务、自定义服务、组件、模块。

3）运行效率较低，数据变更检测方式。

4）学习angular会迫使你学习特有的预发，上手成本很大，代码看起来很干净。

5）依赖注入，即一个对象将依赖项提供给另一个对象（客户端）的模式。导致更多的灵活性和更干净的代码。

6）Angular 最适合单页应用（SPA），因为它可能太臃肿而不能用于微服务。

7）框架比较臃肿，每次用啥功能要引入一大堆东西Angular错误提示不够清晰明显，对于初级开发者，很难看懂Angular的错误提示，而且定位bug很难。

8）面向对象编程的思想，Angular由后端开发人员设计的前端框架。

# 2.React特性:

1）单向绑定，先更新model,然后渲染UI元素，数据在一个方向流动，使得调试更加容易。

2）代码冗余，各种生命周期太麻烦，刚开始接触好难记。

3）用了虚拟DOM。

4）更适合大型应用和更好的可测试性Web端和移动端原生APP通吃。

5）更大的生态系统，更多的支持和好用的工具。

# 3.Vue特性

1）模板和渲染函数的弹性选择

2）简单的语法和项目配置

3）更快的渲染速度和更小的体积四

# 4.Vue与Angular的区别:

相同点：

1)都支持指令：内置指令和自定义指令。

2)都支持过滤器：内置过滤器和自定义过滤器。

3)都支持双向数据绑定。

4)都不支持低端浏览器。

不同点：

1)更简单易用

2)更灵活

3)性能更突出 

# 5.Vue与React的区别:

相同点：

1)两者都需要编译后使用。

2)都提供合理的钩子函数，可以让开发者定制化地去处理需求。

3)都不内置列数AJAX，Route等功能到核心包，而是以插件的方式加载。

4)都使用了virtual DOM。 

5)提供了响应式和组件化的视图组件. 

6)将注意力集中在核心库，而将其他功能如路由和全局状态管理交给相关的库。

不同点：

1)性能更好

2)更易学更简单

3)优化更好

# 三.总结

现在， Vue 还没有 React (由 Facebook 维护) 或者 Angular 2 (受到 Google 的支持) 流行。不过，许多开发者都已经转向 Vue 了。Laravel 社区也在考虑将它作为可选用的前端框架之一。 

总之，Vue 给 React & Angular 的弊病提供了一道良方，也为人们提供了一种更加简单和轻松的方法来编写代码。 
