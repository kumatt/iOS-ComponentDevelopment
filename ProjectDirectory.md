# <span id='toc_0'>iOS-ComponentDevelopment</span>

‘Podfile’ header should include:

```
source 'https://github.com/OComme/iOS-ComponentDevelopment.git'

source 'https://github.com/CocoaPods/Specs.git'
```

use private framework and cocoapods framwork

<ul>
<li>
<a href="#toc_0">iOS-ComponentDevelopment</a>
<ul>
<li>
<a href="#toc_1">让开源项目支持CocoaPods</a>
</li>
<li>
<a href="#toc_11">创建私有Spec Repo</a>
</li>
</ul>
</li>
</ul>

<span id='toc_1'></span>
## 让开源项目支持CocoaPods

以[WK-PrefixHeader](https://github.com/ZOCafe/WK-PrefixHeader)为例

### 1. cd到当前目录

```
$ cd WKPrefixHeader
```

### 2.创建一个podspec文件,命令:

```
$ pod spec create WKPrefixHeader
```

### 3.编辑 podspec文件，命令：

注意：使用文本编辑器保存的podspec文件，标点符号可能与标准格式不一样，导致编译失败，别用它!

```
$ open WKPrefixHeader.podspec
```
如果本地没有默认能打开podspec格式的工具，则该命令会失败。

此时需进入文件所在目录，选择文件打开方式。


### 4.创建之后会自动生成一个模板，里面会有详细的注释，我们只需要按需要修改这个文件即可，下边这个是测试的时候我编辑的 （如果需要更更多的配置 可以参考别的开源项目的podspec文件）：

```
Pod::Spec.new do |s|
  s.name         = "WKPrefixHeader"
  s.version      = "0.0.2"
  
  # 支持的cocoapods的版本
  # s.cocoapods_version = '>= 0.36'
  
  # 简短介绍，下面是详细介绍
  s.summary      = "something about prefix header of WKPrefixHeader."
  # s.description  = <<-DESC
  #                  DESC

  # 相对'podspec'文件位置
  s.source_files = "WKPrefixHeader/*"

  # 项目主页
  s.homepage     = "https://github.com/OComme/WK-PrefixHeader"
  # 作者信息
  s.author             = { "OComme" => "a163913692@icloud.com" }
  
  # 项目git地址,tag值与spec.verison版本一致
  # 不指定分支
  s.source       = { :git => "https://github.com/OComme/WK-PrefixHeader.git", :tag => "#{s.version}" }
  # 或指定分支
  # s.source       = { :git => "https://github.com/OComme/WK-PrefixHeader.git", branch: 'master', :tag => "#{s.version}" }
  
  # 指定为本地地址
  # podspec :path => '/Documents/PrettyKit/PrettyKit.podspec'
  
  # 许可,一般MIT,默认与spec文件在同一目录下
  s.license      = "MIT"
  # 指定许可文件
  # s.license = { :type => 'MIT', :file => 'MIT-LICENSE.txt' }
  # 指定许可文件的内容
  # s.license = { :type => 'MIT', :text => <<-LICENSE
                   Copyright 2012
                   Permission is granted to...
                 LICENSE
               }
  
  # 多媒体地址,如果地址是twitter,发布版本会有通知
  # s.social_media_url = 'https://twitter.com/cocoapods'
  # s.social_media_url = 'https://groups.google.com/forum/#!forum/cocoapods'
  
  # 单个截图
  # s.screenshot  = 'http://dl.dropbox.com/u/378729/MBProgressHUD/1.png'
  # 多个截图
  # spec.screenshots = [ 'http://dl.dropbox.com/u/378729/MBProgressHUD/1.png',
                     'http://dl.dropbox.com/u/378729/MBProgressHUD/2.png' ]
 
  # 文档说明
  # s.documentation_url = 'http://www.example.com/docs.html'
 
  # prepare_command,在pod文件下载完毕之后,执行的命令
  # 单个命令
  # s.prepare_command = 'ruby build_files.rb'
  # 多条命令
  # spec.prepare_command = <<-CMD
                        sed -i 's/MyNameSpacedHeader/Header/g' ./**/*.h
                        sed -i 's/MyNameOtherSpacedHeader/OtherHeader/g' ./**/*.h
                   CMD
                   
  # 是否过期
  # s.deprecated = true
  
  # 公有头文件
  # s.public_header_files = 'Headers/Public/*.h'
  # 私有头文件
  # s.private_header_files = 'Headers/Private/*.h'
  
  # prefix_header_contents 类似于pch,文件,多个用逗号隔开
  # s.prefix_header_contents = '#import <UIKit/UIKit.h>', '#import <Foundation/Foundation.h>'
  # 也可以这样写:
  # s.prefix_header_contents = <<-EOS
    #ifdef __OBJC__
    #import "SGExtension.h"    //SGExtension包含了所有头文件
    #endif 
  # EOS
  # end
  
  # 指定pch文件
  #s.prefix_header_file = 'iphone/include/prefix.pch'
  
  # 资源文件地址
  # s.resource_bundles = {
  #  'PodTestLibrary' => ['Pod/Assets/*.png']
  # }                                       

  # 自己的或者第三方framework,比qqSDK的TencentOpenAPI.framework
  # s.vendored_frameworks = 'MyFramework.framework','TheirFramework.framework'
  # 自己的或者第三方.a文件,比如微信SDK的.a文件
  # s.vendored_libraries = 'libProj4.a', 'libJavaScriptCore.a'
  
  # 所需的framework，多个用逗号隔开
  # s.frameworks = 'SystemConfiguration'                  
  
  # 依赖关系，该项目所依赖的其他库，如果有多个需要填写多个s.dependency
  # s.dependency 'SomeOtherPod'   
  # 指定某个平台的依赖
  # s.ios.dependency 'SomeOtherPod'
  
  # 支持的平台,如果不写默认支持所有平台
  s.platform = :ios, "8.0"//仅支持ios
  
  # 支持多个平台
  # s.ios.deployment_target = '6.0'
  # s.osx.deployment_target = '10.8'
  
  # 是否是ARC,默认true,如果不是,会自动添加-fno-objc-arc compiler flag
  s.requires_arc = true
  # 部分是ARC
  # s.requires_arc = false
  # s.requires_arc = 'Classes/Arc'   //该文件夹下是ARC,其它非ARC
  # s.requires_arc = ['Classes/*ARC.m', 'Classes/ARC.mm']

  # weak_frameworks
  # 如果在高版本的OS中调用新增的功能，并且在低版本的OS中依然能够运行,那么就要用到weak_frameworks.如果引用的某些类或者接口在低版本中并不支持，对于不支持的接口，可以在运行的时候判断，这样程序不会出错，如果不weak引用，程序在低版本下启动的时候就会崩溃掉
  # s.weak_framework = 'MessageUI'

  # ibraries 比如libz,sqlite3.0等,多个用逗号分开
  # s.libraries = 'xml2', 'z'  //z表示libz.tdb,后缀不需要,lib开头的省略lib
  
  # compiler_flags
  # s.compiler_flags = '-DOS_OBJECT_USE_OBJC=0', '-Wno-format'
end
```
### 5.创建tag，并推送到git,依次执行以下命令：
```
$ git tag 0.0.1
$ git push --tags
```

### 6.验证podspec文件 

验证基本格式：
```
$ pod lib lint WKPrefixHeader.podspec
```

验证能否提交上PodSpec目录：

```
$ pod spec lint WKPrefixHeader.podspec
```

如果当前库依赖私有类库，则在验证时需要带上类库所在的 specs的地址
```
$ pod lib lint --sources='私有仓库repo地址,https://github.com/CocoaPods/Specs'
$ pod spec lint --sources='私有仓库repo地址,https://github.com/CocoaPods/Specs'
```

### 7.如果验证不通过，会有详细的ERROR和WARING提示，根据提示依次解决，然后回到第6步重新来一遍。

有时经过多次的校验，缓存的数据影响到验证信息，需要清楚cocoapods缓存 :

查看缓存列表  ：

```
$ pod cache list
```

清除缓存列表  ：

```
$ pod cache clean WKPrefixHeader
```

注意：在重新开始之前，我们要删除远程库的tag和本地的tag，命令如下：
```
$ git tag -d 0.0.1                   //删除本地tag
$ git push origin :refs/tags/0.0.1  // 删除远程库tag
$ git push origin master
```

### 8.验证通过后，提交到CocoaPods或私有Specs。
```
$ pod trunk push WKPrefixHeader.podspec          //提交到CocoaPods
```
或

```
$ pod repo push WKSpecs WKPrefixHeader.podspec   //提交到私有Specs
```

如果当前库依赖私有类库，则在验证时需要带上类库所在的 specs的地址
```
$ pod repo push WKSpecs WKPrefixHeader.podspec --sources='私有仓库repo地址,https://github.com/CocoaPods/Specs'
```
### 9.如果是第一次提交CocoaPods，需要先执行这个命令：
```
$ pod trunk register 这里写邮箱 '这里起个名字' --description=' 这里写描述'
```
执行完成之后，会给你的邮箱里发一封邮件，去邮箱点击链接之后，再重新执行第8步即可！

<span id='toc_11'></span>
## 创建私有Spec Repo

先来说第一步，什么是Spec Repo？它是所有的Pods的一个索引，就是一个容器，所有公开的Pods都在这个里面。

它实际是一个Git仓库remote端在GitHub上，但是当你使用了Cocoapods后它会被clone到本地的~/.cocoapods/repos目录下，可以进入到这个目录看到master文件夹就是这个官方的Spec Repo了。

这个master目录的结构是这个样子的:

```
├── Specs
    └── [SPEC_NAME]
        └── [VERSION]
            └── [SPEC_NAME].podspec
```

所以我们创建一个 Git仓库，这个仓库可以创建私有的也可以创建公开的，不过既然私有的Spec Repo，还是创建私有的仓库吧。

需要注意的就是如果项目中有其他同事共同开发的话，你还要给他这个Git仓库的权限。

创建完成之后在Terminal中执行如下命令
> `$ pod repo add [Private Repo Name] [GitHub HTTPS clone URL]`

```
$ pod repo add MySpecs https://github.com/OComme/iOS-ComponentDevelopment.git
```
此时如果成功的话进入到~/.cocoapods/repos目录下就可以看到MySpecs这个目录了。至此创建私有Spec Repo完成。

## 关于文件匹配

- `*`匹配所有文件
- `c*`匹配以名字C开头的文件
- `*c`匹配以名字c结尾的文件
- `*c*`匹配所有名字包含c的文件
- `**`文件夹以及递归子文件夹
- `?`任意一个字符(注意是一个字符)
- `[set]` 匹配多个字符,支持取反
- `{p,q}` 匹配名字包括p 或者 q的文件
