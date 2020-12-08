### 前提

1. web.xml的作用是什么，什么时候起作用，如何起作用。
2. web的三大组件如何生效,如何注册。servlet listener filter

### 正文

- 注解驱动

```xml
// 作用？？？
<mvc:anotation-driven/>
```

- `DispatcherServlet`
  - 前端控制器，用于将请求分发给合适的处理器。
- `HandlerMapping`
  - 控制请求到处理器的路由。
  - `BeanNameUrlHandlerMapping`
  - `DefaultAnnotationHandlerMapping`
- `HandlerAdapter`
  - 处理请求
  - `HttpRequestHandlerAdapter`
  - `SimpleControllerHandlerAdapter`
  - `HttpRequestHandler`
  - `Controller`
  - `AnnotationMethodHandlerAdapter`
- `HandlerExceptionResolver`
  - 处理异常
  - `AnnotationMethodHandlerExceptionResolver`
  - `ResponseStatusExceptionResolver`
  - `DefaultHandlerExceptionResolver`
- `ViewResolver`
  - 解析视图，将符号视图名称解析成视图对象
  - `InternalResourceViewResolver`
- `RequestToViewNameTranslator`
  - 将请求转换成视图名称
  - `DefaultRequestToViewNameTranslator`