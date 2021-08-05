# NodeAurora
Aurora Runtime: Node.js runtime for android

## 如何使用
Step 1: 在你的项目级 build.gradle 中的 buildscript 节点中添加 Maven 仓库：*  
```
    repositories {
        maven {
            url 'https://maven.aurora-nature.asia'
        }
    }
```  
* 你也可以直接在 Release 中获取 AAR 导入项目。    

Step 2: 在模块级 build.gradle 中导入包并 Sync 你的 Gradle 项目 
```
implementation io.bushe.export.aurora.nodejs
```
Step 3: 在你想要创建一个 Node.js 环境时访问以下方法：
```java
Aurora nodeRuntime = new Aurora().initialize(Context, ABI, NodeAppPath)
// NOTICE: ABI 的可用范围是：arm64-v8a, armeabi-v7a
// NOTICE: NodeAppPath 应当指定为你的 Node.js App 目录，运行环境会尝试访问 NodeAppPath/index.js
```
Steo 3: 通过 Log 获取 Node.js 运行时输出 ( TAG: Node ) 

### 其他
源代码会在构建版本稳定时放出。

### 致谢
非常感谢以下项目对此项目的开发提供了帮助：  
[Termux](https://github.com/termux/)  
非常感谢以下开发者在百忙之中为此项目进行贡献或指导：  
@ Marek Kowalski  
@ Wiktor Sieprawski  
@ addaleax  
