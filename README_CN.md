# Aurora Node Runtime
适用于 Android 的原生 Node 运行时  
[English Document](https://github.com/BuShe-LLC/NodeAurora/tree/main/RADEME.md)  

### 导入依赖
若要在你的项目中使用 BuShe Aurora Node：  

在你的根项目的 Gradle 文件（build.gradle）中检查你是否启用了 BuShe Developer Program Maven 仓库。 

```groovy
buildscript {

  repositories {
    // Check that you have the following line (if not, add it):
    maven { url 'https://maven.aurora-nature.asia' } // BuShe Developer Program's Maven repository
  }

}

allprojects {
  // ...

  repositories {
    // Check that you have the following line (if not, add it):
    maven { url 'https://maven.aurora-nature.asia' } // BuShe Developer Program's Maven repository
    // ...
  }
}
```  
在模块（应用级）Gradle 文件（通常为 app/build.gradle）中声明 BuShe Aurora Node 依赖项。  

```groovy
dependencies {
  // ...
  // Declare the dependency for the BuShe Aurora Node
  implementation 'io.bushe.export.aurora:latest'
}
```

同步你的的应用以确保所有依赖项都具有所需的版本。  

### 用法
- Step 1: 为了构造 Node 运行环境，你需要先导入 Native Dynamic Support Library，我们提供了一个 API 完成：
```java
 // 此函数将复制 Native Dynamic Support Library 到你的应用的 Files 下的 library 文件夹（通常是 /data/user/0/你的应用的包名称/files/library/）.
 new Linker().linker_initialize(Context context, String NativeDynamicSupportLibraryPath,
         new LinkerInterface() {
         
             @Override
             public void succeed() {
                 //TODO: 现在你便可以使用以下API 构造一个 Node 进程
                 //TODO: 其中字符串 "NodeAppDir" 是你的 Node 应用的根目录，运行环境会尝试执行 "NodeAppDir/index.js".
                 new Aurora().initialize(Context context, String NodeAppDir);
             }
             
             @Override
             public void error(String s) {
                 //TODO: Handler the error in your own way.
             }
        }
 );
```
请特别注意，当前版本的运行环境会访问你提供的 Native Dynamic Support Library 目录，并将其复制到应用的 Files 目录的 library 目录下（通常是 /data/user/0/你的应用的包名称/files/library/），但是我们推荐你自己完成这一步骤，运行环境会自动判断是否已存在 Native Dynamic Support Library。  

- Step 2: 现在你便可以在 Android Log 中看到完整的 Node 标准输出。

### Native Dynamic Support Library
你可以在 [此处](https://github.com/BuShe-LLC/NodeAurora/tree/main/NativeSupport) 获得 Native Dynamic Support Library 的压缩文件，请在项目使用时解压缩，运行环境会直接访问目录而并非压缩文件。  
请在开发时选择适用于适用于用户的 ABI，我们建议使用拆分 APK 来优化包体积。  

### 开源
我们会在项目稳定时放出源代码以及协议。
