#Spring框架学习

##抽象工厂模式
BeanFactory类
```java
package com.toolbox.factory;

import java.io.IOException;
import java.io.InputStream;
import java.util.Properties;

public class BeanFactory {

    private  static Properties env = new Properties();

    static {
        //获取输入流
       InputStream in =  BeanFactory.class.getResourceAsStream("/ApplicationContext.properties");
        //读取文件内容封装在Properties中
        try {
            env.load(in);
            in.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    /**
     * 获取Bean
     * @param beanName
     * @return
     */
    public static Object getBean(String beanName){
        Class cls = null;
        Object obj = null;
        try {
            cls = Class.forName(env.getProperty(beanName));
            obj = cls.newInstance();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } catch (IllegalAccessException e) {
            e.printStackTrace();
        } catch (InstantiationException e) {
            e.printStackTrace();
        }
        return obj;
    }
}
```

Spring等核心就是工厂。核心类是
ApplicationContext

##Spring核心API
* ApplicationContext
>1. 作用:对象工厂 负责对象等创建
>2. 优点: 解耦

* ApplicationContext实现
>1. 非web环境：ClassPathXmlApplicationContext
>2. web环境: XmlWebApplicationContext
