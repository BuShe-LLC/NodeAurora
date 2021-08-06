# NodeAurora
Aurora Runtime: Node.js runtime for android

## 用法
Step 1: 在你的项目级 build.gradle 中的 buildscript 节点中添加 Maven 仓库：*  
```
repositories {
    maven { url 'https://maven.aurora-nature.asia' }
}
```  
* 你也可以直接在 Release 中获取 AAR 导入项目。    

Step 2: 在模块级 build.gradle 中导入包并 Sync 你的 Gradle 项目 
```
implementation 'io.bushe.export.aurora.nodejs:latest'  
```
* 或使用 implementation file() 本地导入           

Step 3: 在你想要创建一个 Node.js 环境时访问以下方法：
```java
new Aurora().initialize(@NonNull Context context, @NonNull String LibraryDir, @NonNull String NodeAppDir)
// NOTICE: LibraryDir 指定为你的 BuShe Native Support Library 路径
// NOTICE: NodeAppDir 指定为你的 Node.js App 目录，运行环境会尝试访问 NodeAppPath/index.js
```  

## 原生支持库 BuShe Native Support Library  
你可以在 [此处](https://github.com/BuShe-LLC/NodeAurora/tree/main/NativeSupport) 找到。   
我们建议你构建适用于不同 ABI 的 APK，并将支持库放在 assets 中，运行时引用。  
NOTICE: 你需要解压缩支持库。  

### 其他
源代码会在构建版本稳定时放出。

### 致谢
非常感谢以下项目对此项目的开发提供了帮助：  
[Termux](https://github.com/termux/)  
非常感谢以下开发者在百忙之中为此项目进行贡献或指导：  
@ Marek Kowalski  
@ Wiktor Sieprawski  
@ addaleax  
