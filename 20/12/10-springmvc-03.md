> - `servlet`注册后，由服务器控制生命周期。`init()`,`service()`,`destory()`
>
> - `DispatcherServlet`的初始化工作就是创建和初始化其需要的策略接口的实现以及`web`容器
>
> - `DispatcherServlet`的使用，就是使用策略接口的实现，完成映射请求、处理请求、渲染视图、
>
>   做出响应的工作。
>

#### 接下来的事情，就是知道`DispatcherServlet`的各个策略接口是如何工作的。

### 1、`HandlerMapping`

> - `HandlerMapping`如何选择初始化实例
> - `HandlerMapping`有一个注册表，映射处理器方法和它的映射路径。那么这个注册表什么时候，怎么初始化
> - `HandlerInteceptor`什么时候初始化
> - `springmvc`是如何将策略接口的定义注册到容器中的

#### 1.1解释

获得执行链。执行链中包含处理器方法和拦截器

- 首先获得执行器。根据请求信息在注册表中查找对应的处理器方法，然后向上转型，返回`Object`。
- 封装为执行链。遍历所有的拦截器，如果该拦截器可以处理该请求，就将其加入到执行链中。

#### 1.2结构

```java
HandlerMapping
	AbstractHandlerMapping
    	AbstractHandlerMethodMapping
    		RequestMappingInfoHandlerMapping
    			RequestMappingHandlerMapping
```

> - 如何知道要实例化`RequestMappingHandlerMapping`

### 2、`HandlerAdapter`