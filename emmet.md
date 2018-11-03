## emmet快捷键：

- 属性操作符

  - id和class

  ```
  div.test  => <div class="test"></div>
  div#pageId => <div id="pageId"></div>
  ```

  - 隐藏标签

  ```+
  .class
  =>
  <div class></div>
  em>.class
  =>
  <em><span class></span></em>
  table>.row>.col
  =>
  <table>
      <tr class="row">
          <td class="col"></td>
      </tr>
  </table>
  
  ```

  - 绑定多个类名用.符号连续起来即可

  ```+
  div.test1.test2.test3
  =>
  <div class="test1 test2 test3"></div>
  
  ```

- 嵌套操作符(Nesting operators)

   嵌套操作符用于将缩写元素放置在生成的树中,是否应放置在上下文元素的内部或附近. 

  - 子级:>
     通过>标识元素可以生成嵌套子级元素,可以配合元素属性进行连写

     ```+
    div#pageId>ul>li    =>   
    <div id="pageId">       
    <ul>          
    <li></li>       
    </ul>    
    </div>
     ```

  - 同级:+
     +字符表示生成兄弟级元素.

     ```+
    div#pageId+div.child   =>   <div id="pageId"></div>   <div class="child"></div>
     ```

  - 父级:^
     ^用于生成父级元素的同级元素,从这个^字符所在位置开始,查找左侧最近的元素的父级元素并生成其兄弟级元素.

     ```+
    <div>p.parent>span.child^ul.brother>li   => 
    <div>      
    <p class="parent"><span  class="child"></span></p>       
    <ul  class="brother">           
    <li></li>      
    </ul>    
    </div>
     ```

    - **分组操作符(Grouping)**
       分组使用()来实现缩写的分离.比如这个例子,如果不加括号那么a将作为span的子级元素生成.加上括号a将于()内的元素同级.

    ```
    div>(ul>li+span)>a
    =>
    <div>
        <ul>
            <li></li>
            <span></span>
        </ul>
        <a href=""></a>
    </div>
    ```

    - **乘法(Multiplication)**
       使用*N即可自动生成重复项.N是一个正整数.在使用时请注意*N所在位置,位置不同生成的结果不同.
       

    ```
    ul>li*3
    =>
    <ul>
        <li></li>
        <li></li>
        <li></li>
    </ul>
    ```