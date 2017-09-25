# iOS-ComponentDevelopment

在进行组件开发之前，可先了解下[cocoapod私有Specs的创建](ProjectDirectory.md)

基本的模块构架

```
    ├── <PrefixHeader>           预编译组件
    ├── <ConnectCore>            中间模块，负责组件间的调度和消息派发。

    ├── <Business>               业务组件
    ├── <BaseFeature>            基础功能组件
    └── <BaseUI>                 基础UI组件
```

<ul>
  <li>
    基础功能组件：（类似于Networking、网络诊断等）
    <ul>
      <li>
        按功能分库，不涉及产品业务需求
      </li>
      <li>
        通过良好的接口供上层业务组件调用；
      </li>
      <li>
        不写入产品定制逻辑，通过扩展接口完成定制；
      </li> 
   </ul>
  </li>
  
  <li>
    基础UI组件：（例如下拉刷新组件、iCausel类似的组件）
    <ul>
      <li>
        产品内通用UI组件；（各个业务模块依赖使用，但需要保持好定制扩展的设计）
      </li>
      <li>
        公共通用UI组件；（不涉及具体产品的视觉设计， 目前较少）
      </li>
   </ul>
  </li>

  <li>
    产品业务组件：（例如圈子、登录等）
    <ul>
      <li>
        业务功能间相对独立，相互间没有Model共享的依赖；
      </li>
      <li>
        业务之间的逻辑Action调用只能通过RAC绑定中间组件进行跳转；
      </li>
   </ul>
  </li>
</ul>

依赖于'ReactiveCocoa'框架的组件间通信，基于'MVVM'的事件分发，构成这一组件开发的基础。

了解更多，请参见[关于组件化的思考和总结](Other.md)

参考自：[iOS组件化思路－大神博客研读和思考](http://www.jianshu.com/p/afb9b52143d4)


