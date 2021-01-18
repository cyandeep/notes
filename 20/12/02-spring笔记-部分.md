### `spring`笔记

#### 1.`AnnotationConfigRegistry`

- 用于注册注解配置的组件
- `register(annotateClass)`和`scan(basePackage)`

#### 2.`BeanPostProcessor`

- 修改创建的bean对象,比如包装对象用于代理
- `postProcessBeforeInitilazation()`和`postProcessAfterInitialization()`

#### 3.`BeanDefinitionRegistry`

- 操作持有bean定义的注册表的接口

#### 4.`BeanFactoryPostProcessor`

- 修改底层的`beanFactory`中的bean定义

#### 4.容器的启动

```java
//1.调用默认构造器，初始化reader和scanner
this();
//2.注册配置类
register(annotatedClasses);
//3.刷新容器
refresh();
```

