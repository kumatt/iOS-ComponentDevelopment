# iOS组件化方案

在进行组件开发之前，需要先了解[cocoapod私有Specs的创建](ProjectDirectory.md)。

依据让当前的架构适应组件化开发的要求。

这是关于[我的组件化方案架构](https://github.com/OComme/iOS-ProjectStructureDemo)

基本要求

1. 添加中间层，只让其他模块对中间层产生耦合关系，中间层不对其他模块发生耦合。
2. 在主项目中通过CocoaPods来集成，将所有组件当做二方库集成到项目中。

了解更多，请参见[关于组件化的思考和总结](Other.md)

参考自：[iOS组件化思路－大神博客研读和思考](http://www.jianshu.com/p/afb9b52143d4)


