---
title: java多线程的4种实现方式
category: Linux
author: itgoyo
toc: true
tags: Linux
date: 2019-12-31 16:00:37
keywords:
description:
source_url:
---


1\. 继承 Thread 类，重写 run 方法（其实 Thread 类本身也实现了 Runnable 接口）

2\. 实现 Runnable 接口，重写 run 方法

3\. 实现 Callable 接口，重写 call 方法（有返回值）

4\. 使用线程池（有返回值）

1\. 继承 Thread 类，重写 run 方法

　　每次创建一个新的线程，都要新建一个 Thread 子类的对象

　　启动线程，new Thread 子类（）.start（）

　　创建线程实际调用的是父类 Thread 空参的构造器

```
public class MyThread {

    public static void main(String ards[]){
        for(int i=0;i<10;i++){
            new ExtendsThread().start();
        }
        System.out.println(Thread.currentThread().getName());
    }

}

class ExtendsThread extends Thread{
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName());
    }
}
```

2\. 实现 Runnable 接口，重写 run 方法

　　不论创建多少个线程，只需要创建一个 Runnable 接口实现类的对象

　　启动线程，new Thread（Runnable 接口实现类的对象）.start ()

 　　创建线程调用的是 Thread 类 Runable 类型参数的构造器
 　　

```language


public class MyThread {

    public static void main(String ards[]){
        Runnable implRunnable = new ImplRunnable();
        for(int i=0;i<10;i++){
            new Thread(implRunnable).start();
        }
        System.out.println(Thread.currentThread().getName());
    }

}

class ImplRunnable implements Runnable{
    private volatile  int i = 0;
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName()+"--"+ i++);

    }
}
```

3\. 实现 Callable 接口，重写 call 方法（有返回值）

　　自定义类实现 Callable 接口时，必须指定泛型，该泛型即返回值的类型

　　每次创建一个新的线程，都要创建一个新的 Callable 接口的实现类、

　　如何启动线程？

　　　　（1）创建一个 Callable 接口的实现类的对象

　　　　（2）创建一个 FutureTask 对象，传入 Callable 类型的参数

　　　　　　　　public FutureTask(Callable<V> callable){……}

　　　　（3）调用 Thread 类重载的参数为 Runnable 的构造器创建 Thread 对象

　　　　　　　　将 FutureTask 作为参数传递

　　　　　　　　public class FutureTask<V> implements RunnableFuture<V>

　　　　　　　　public interface RunnableFuture<V> extends Runnable, Future<V>

　　如何获取返回值？

　　　　调用 FutureTask 类的 get () 方法

```language



public class MyThread {

    public static void main(String ards[]) throws InterruptedException, ExecutionException{

        for(int i=0;i<10;i++){
            Callable<Integer> implCallable = new ImplCallable();
            FutureTask<Integer> futureTask = new FutureTask<Integer>(implCallable);
            new Thread(futureTask).start(); System.out.println(Thread.currentThread().getName()+"----"+futureTask.get());
        }

        System.out.println(Thread.currentThread().getName());
    }

}

class ImplCallable implements Callable<Integer>{

    @Override
    public Integer call() throws Exception {
        int result = 0;
        for(int i=0;i<10;i++){
            result += i;
        }
        System.out.println(Thread.currentThread().getName());
        return result;
    }

}

```

4\. 线程池

Executors 类
```language


/** *
 * 线程池
 * 跟数据库连接池类似
 * 避免了线程的创建和销毁造成的额外开销
 *
 * java.util.concurrent
 *
 * Executor    负责现成的使用和调度的根接口
 *    |--ExecutorService    线程池的主要接口
 *          |--ThreadPoolExecutor    线程池的实现类
 *          |--ScheduledExecutorService    接口，负责线程的调度
 *              |--ScheduledThreadPoolExecutor    (extends ThreadPoolExecutor implements ScheduledExecutorService)
 *
 *
 * Executors工具类
 * 提供了创建线程池的方法
 * */
public class ThreadPool { public static void main(String[] args){ //使用Executors工具类中的方法创建线程池
        ExecutorService pool = Executors.newFixedThreadPool(5);

        ThreadPoolDemo demo = new ThreadPoolDemo(); //为线程池中的线程分配任务,使用submit方法，传入的参数可以是Runnable的实现类，也可以是Callable的实现类
        for(int i=1;i<=5;i++){
            pool.submit(demo);
        } //关闭线程池 //shutdown ： 以一种平和的方式关闭线程池，在关闭线程池之前，会等待线程池中的所有的任务都结束，不在接受新任务 //shutdownNow ： 立即关闭线程池
 pool.shutdown();

    }
} class ThreadPoolDemo implements Runnable{ /**多线程的共享数据*/
    private int i = 0;

    @Override public void run() { while(i<=50){
            System.out.println(Thread.currentThread().getName()+"---"+ i++);
        }
    }
}

```

```language


public class ThreadPool2 { public static void main(String args[]){
        ExecutorService executorService = Executors.newFixedThreadPool(5); for(int i=0;i<5;i++){
            Future<Integer> future = executorService.submit(new Callable<Integer>() {

                @Override public Integer call() throws Exception { int result = 0; for(int i=0;i<=10;i++){
                        result += i;
                    } return result;
                }
            }); try {
                System.out.println(Thread.currentThread().getName()+"--"+future.get());
            } catch (InterruptedException | ExecutionException e) {
                e.printStackTrace();
            }
        }

        executorService.shutdown();

    }

}
```







---

<div align=center>

        发现更多更好玩的，欢迎关注我的微信公众号:<span style='color:red;'> FullStacker </span><br />
        <img src="/img/fullstacker.jpg"
            height="400px" width="400px" />
    </div>

