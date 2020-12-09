### 1、`DispatcherServlet`

#### 继承结构

```java
Servlet
    GenericServlet
    	HttpServlet
    		HttpServletBean  //从这开始，由springframework实现
    			FrameworkServlet
    				DispatcherServlet
```



#### 1.1 前端控制器的策略接口和默认实现

```properties
org.springframework.web.servlet.LocaleResolver=org.springframework.web.servlet.i18n.AcceptHeaderLocaleResolver

org.springframework.web.servlet.ThemeResolver=org.springframework.web.servlet.theme.FixedThemeResolver

org.springframework.web.servlet.HandlerMapping=org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping,\
	org.springframework.web.servlet.mvc.annotation.DefaultAnnotationHandlerMapping

org.springframework.web.servlet.HandlerAdapter=org.springframework.web.servlet.mvc.HttpRequestHandlerAdapter,\
	org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter,\
	org.springframework.web.servlet.mvc.annotation.AnnotationMethodHandlerAdapter

org.springframework.web.servlet.HandlerExceptionResolver=org.springframework.web.servlet.mvc.annotation.AnnotationMethodHandlerExceptionResolver,\
	org.springframework.web.servlet.mvc.annotation.ResponseStatusExceptionResolver,\
	org.springframework.web.servlet.mvc.support.DefaultHandlerExceptionResolver

org.springframework.web.servlet.RequestToViewNameTranslator=org.springframework.web.servlet.view.DefaultRequestToViewNameTranslator

org.springframework.web.servlet.ViewResolver=org.springframework.web.servlet.view.InternalResourceViewResolver

org.springframework.web.servlet.FlashMapManager=org.springframework.web.servlet.support.SessionFlashMapManager
```

#### 1.2前端控制器的初始化过程

```JAVA
1.PropertiesLoaderUtils.loadProperties(resource);//加载默认的策略实现 -- 加载DispatcherServlet后
2.//DispatcherServlet的实例化
3,Servlet.init(ServletConfig config)//在servlet实例化之后，由servlet容器调用，用于servlet的初始化
---
HttpServletBean.init()//设置bean属性，并调用子类的初始化方法
    FrameworkServlet.initServletBean()//创建并初始化WebApplicationContext
    	initWebApplicationContext()//创建并初始化WebApplicationContext
    		createWebApplicationContext(WebApplicationContext parent)//通过反射，调用无参构造器实例化webApplicationContext,默认xmlWebApplicationContext,要么是定制的context class
---
    
```



> - `FrameworkServlet`实现了`ApplicationContextAware`接口，但是没有加入到容器中，spring容器时如何管理并回调其中的方法。
> - spring容器启动过程，在什么时机回调`ApplicationContextAware`的回调接口

#### 1.3前端控制器的拦截请求，分发请求的过程

> - `<servlet-mapping>/</servlet-mapping>`拦截的是什么请求
>
> - `HandlerExecutionChain`,保存什么，干什么的,和`HandlerAdapter`有什么区别
> - 为什么要有一个适配器`HandlerAdapter`
> - `HandlerAdapter`接口的继承结构
> - `HandlerInterceptor`

```java
Servlet.service(ServletRequest req, ServletResponse res)//由tomcat调用，用于处理请求并作出响应
---
HttpServlet.service(ServletRequest req, ServletResponse res)//请求过来后，从这里开始，将servletRequest强  转为httpServletRequest
    service(HttpServletRequest req, HttpServletResponse resp)//根据请求类型，转调do***()
    	FrameworkServlet.processRequest(HttpServletRequest request, HttpServletResponse response)//处理请求，发布事件
---			
DispatcherServlet.doService(HttpServletRequest request, HttpServletResponse response)//设置请求的属性，以及分发请求
    doDispatch(HttpServletRequest request, HttpServletResponse response)//分发请求的真正实现
    	getHandler(HttpServletRequest request)//通过handlerMapping获取这个请求的handler
    	getHandlerAdapter(Object handler)//决定当前请求的处理器适配器
    	ha.handle(HttpServletRequest request, HttpServletResponse response, Object handler)//处理请求
	    render(ModelAndView mv, HttpServletRequest request, HttpServletResponse response)//渲染视图
```

