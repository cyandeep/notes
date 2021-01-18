### 容器启动过程

#### 1.容器初始化

```java
public AnnotationConfigApplicationContext(Class<?>... annotatedClasses) {
    this();
    register(annotatedClasses);
    refresh();
}
```

1. 实例化容器。
   - 初始化`reader`和`scanner。`
2. 注册给定的bean定义
   - 将给定的被注解的类注册到容器中
3. 容器刷新

#### 2.容器刷新

```java
// 1.容器刷新前的准备工作。启动时间、激活标志、属性源的配置
prepareRefresh();

// 2.获取beanFactory -- 创建
ConfigurableListableBeanFactory beanFactory = obtainFreshBeanFactory();

// 3.为beanFactory赋值，eg.默认的ClassLoader,BeanPostProcessor,ApplicationListener... -- 赋值
prepareBeanFactory(beanFactory);
     // 以上为 beanFactory的标准初始化 即 创建和赋值

try {
    // 4.允许子容器在beanFactory的标准初始化之后修改beanFactory（模板方法）
    postProcessBeanFactory(beanFactory);

    // 5.调用容器中注册的beanFactoryPostProcessor
    invokeBeanFactoryPostProcessors(beanFactory);

    // 6.注册拦截bean创建过程的 BeanPostProcessor -- 添加到AbstractApplicationContext的一个List中
    registerBeanPostProcessors(beanFactory);

    // 7.初始化容器的消息源？
    initMessageSource();

    // 8.初始化多播器 -- 如果容器中有多播器，就是用并赋值；如果没有就使用默认的多播器
    initApplicationEventMulticaster();

    // 9.允许子容器初始化其它的特殊的bean,(模板方法)
    onRefresh();

    // 10.注册监听器
    registerListeners();

    // 11.完成beanFactory的初始化 -- 实例化所有的单例bean
    finishBeanFactoryInitialization(beanFactory);

    // 12.发布容器完成刷新的事件
    finishRefresh();
}
```

1. 容器调用注册的`beanFactoryPostProcessor`

   - 前提：

   > `BeanDefinitionRegistryPostProcessor`
   >
   > - 是`BeanFactoryPostProcessor`的扩展，允许在正式的`BeanFactoryPostProcessor`处理之前修改容器的bean定义。
   >
   > 优先级
   >
   > - `PriorityOrdered`,`Ordered`.`the rest`
   >
   > - ```java
   >   //这两个都是调用beanFactoryPostProcessor的回调接口
   >   //第一个是调用已有容器中提供beanFactoryPostProcessor
   >   //第二个是获取的（从哪里获取？）-- 猜测，调用扩展容器添加的 BeanFactoryPostProcessor
   >   invokeBeanFactoryPostProcessors(priorityOrderedPostProcessors, beanFactory);
   >   invokeBeanFactoryPostProcessors(regularPostProcessors, beanFactory);
   >   ```
   > ```
   > 
   > ```
   >
   > - ```java
   >   // 这个是获实例吗？ -- 是的，获取bean instance
   >   beanFactory.getBean(ppName, BeanFactoryPostProcessor.class)
   >   ```
   > ```
   > 
   > ```

   - 流程：

     - 先调用`BeanDefinitionRegistryPostProcessor`的回调接口

       - 根据优先级调用 

         > 为什么要有优先级调用

     - 再调用`BeanFactoryPostProcessor`的回调接口

       - 根据优先级调用

         > 为什么要有优先级调用

2. 注册`BeanPostProcessor`

   - 前提：

   ```java
   BeanPostProcessor //拦截实例的创建过程
   	MergedBeanDefinitionPostProcessor // 处理合并的beanDefinition
       InstantiationAwareBeanPostProcessor //实例化的回调接口
       DestructionAwareBeanPostProcessor	//销毁的回调接口
       
   ```

   