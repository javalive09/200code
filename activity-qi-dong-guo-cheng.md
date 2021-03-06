# Activity启动过程

## **根Activity启动过程中涉及的进程**

![](.gitbook/assets/veqyvt.png)

1. launcher调用startActivity\(\) -&gt; instrumentation.execStartActivity\(\) 通过binder调用ams的startActivity\(\)。
2. ams调用Process.start\(\)并通过socket通讯调用Zygote进程。
3. Zygote进程接收到socket消息后调用Zygote. forkAndSpecialize\(\) fork Application进程然后初始化binder线程池并调用invokeStaticMain\(\)执行ActivityThread.main\(\)。
4. ActivityThread.main\(\)执行ActivityThread.attach\(\)通过binder调用ams.attachApplication\(\) -&gt; ams.attachApplicationLocked\(\)  1.通过binder调用app进程中的ApplicationThread.bindApplication\(\)并执行handleBindApplication\(\) -&gt; new Instrumentation并执行onCreate回调。2.通过binder调用app进程中ApplicationThread.scheduleLaunchActivity\(\) -&gt; handleLaunchActivity\(\)通过instrumentation调用activity生命周期的onCreate及onResume等回调。



 

## **Launcher请求AMS过程**

![](.gitbook/assets/veb67d.png)

## **AMS调用APP过程**

![](.gitbook/assets/veby0h.png)

## AMS和APP通讯

![](.gitbook/assets/vebdxd.png)

## **APP进程中ActivityThread启动Activity的过程**

![](.gitbook/assets/veqcku.png)

{% hint style="info" %}
[Android深入四大组件（六）Android8.0 根Activity启动过程（前篇）](https://liuwangshu.cn/framework/component/6-activity-start-1.html)

[Android深入四大组件（七）Android8.0 根Activity启动过程（后篇）](https://liuwangshu.cn/framework/component/7-activity-start-2.html)
{% endhint %}

