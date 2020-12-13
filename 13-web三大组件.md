> - web三大组件是什么，作用，应用场景，如何使用，底层原理
> - `web.xml`的加载时机，
>   - 应用启动
> - `***-servlet.xml`什么时候其作用
>   - 在`dispatcherServlet`初始化时候
> - component-scan 如何解析
>   - [https://blog.csdn.net/javahongxi/article/details/79500991](https://blog.csdn.net/javahongxi/article/details/79500991)
> - annotation-driven的作用

### 1、`servlet`

- 处理用户请求和做出响应的一个对象。

- 编写一个实现`HttpServlet`接口的类，重写`doGet(),doPost()`,

  之后，在`web.xml`中声明该`servlet`以及该`servlet`处理的`url`。

### 2、`filter`

- 在处理请求之前，和做出响应之后，执行过滤任务的一个对象。

- 该类可以在`servlet`处理请求之前和做出响应之后做出检查和修改的操作，

  所以可以适用于以下的应用场景，应用编码，用户检查，跨与请求。。。

- 编写一个实现了`filter`接口的类，重写`init(),doFilter(),destroy()`

  之后，在`web.xml`中声明该filter,以及注册该`servlet`处理的请求类型。

### 3、`listener`

- 监听web应用中对象和对象属性的变化，并作出处理

- > ```java
  > 对象的创建和销毁，
  > 属性的添加、删除、替换
  > 
  > ServletRequestListener
  > ServletRequestAttributeListener
  >     
  > ServletContextListener
  > ServletContextAttributeListener
  >     
  > HttpSessionListener
  > HttpSessionAttributeListener
  > ```

- 