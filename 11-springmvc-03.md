### 1.`HaddlerMapping`

- 根据请求获取包装handler的执行链。

- ```java
  HandlerExecutionChain getHandler(HttpServletRequest request) throws Exception;
  ```

  

### 2.`HandlerAdapter`

- 使用给定的`handler`处理请求,并返回`ModelAndView`。

- ```java
  ModelAndView handle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception;
  ```

### 3.`ViewResolver`

- 根据给定的`viewName`,解析视图。

- ```java
  View resolveViewName(String viewName, Locale locale) throws Exception;
  ```

### 4.`MultipartResolver`

- 处理文件上传。

- ```java
  MultipartHttpServletRequest resolveMultipart(HttpServletRequest request) throws MultipartException;
  ```

### 5.`HandlerExceptionResolve`

- 解析异常。

- ```java
  ModelAndView resolveException(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex);
  ```

  