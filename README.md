# Aurora Node Runtime
A native Node runtime library for Android.  
[Simplified Chinese](https://github.com/BuShe-LLC/NodeAurora/blob/main/README_CN.md)  

### Importing Dependencies
To enable Aurora Node Runtime in your app:

In your root-level (project-level) Gradle file (build.gradle), check that you have BuShe Developer Program's Maven repository, as well.

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
Using the BuShe Aurora Node, declare the dependencies for the Aurora Node Runtime in your app. Declare them in your module (app-level) Gradle file (usually app/build.gradle).

```groovy
dependencies {
  // ...
  // Declare the dependency for the BuShe Aurora Node
  implementation 'io.bushe.export.aurora:latest'
}
```

Sync your app to ensure that all dependencies have the necessary versions.

### Usage
- Step 1: To build the Node runtime environment. You need to import the Native Dynamic Support Library first, and we provide a way to do that:
```java
 // This function will copy the dynamic support library to the application file directory to gain execution access.
 new Linker().linker_initialize(Context context, String NativeDynamicSupportLibraryPath,
         new LinkerInterface() {
         
             @Override
             public void succeed() {
                 //TODO: Now you can create a Node process using the following function.
                 //TODO: String 'NodeAppDir' is the parent directory of your Node application, and Runtime will try to run NodeAppDir/index.js.
                 new Aurora().initialize(Context context, String NodeAppDir);
             }
             
             @Override
             public void error(String s) {
                 //TODO: Handler the error in your own way.
             }
        }
 );
```
Please note in particular that the runtime library will access the dynamic support library path you provide. and copy it to the library folder in the application's file directory (/data/user/0/PackageName/files/library/), which you can do yourself. The runtime library will check if the dynamic support library already exists before performing the copy.          

- Step 2: You can now see the full runtime stream in the Android Log.  

### Native Dynamic Support Library
You can download from [there](https://github.com/BuShe-LLC/NodeAurora/tree/main/NativeSupport).
Please take care to select the dynamic native support library for the ABI that is applicable to your device.
