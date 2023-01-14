# Android_Gradle_DSL_7.0.0

适用于:

```groovy
classpath 'com.android.tools.build:gradle:7.0.0'
distributionUrl=https\://services.gradle.org/distributions/gradle-7.0.2-all.zip
```

引入`Gradle`源码:

```groovy
android {
    sourceSets {
        def base = "C:\\Users\\Administrator\\.gradle\\wrapper\\dists\\gradle-6.5-all\\2oz4ud9k3tuxjg84bbf55q0tn\\gradle-6.5\\src"
        main.java.srcDirs += [
                "${base}/core",
                "${base}/core-api",
                "${base}/base-services",
                "${base}/base-services-groovy",
                "${base}/logging",
                "${base}/plugins",
                "${base}/diagnostics",
                "${base}/ide-native",
        ]
    }

    //输出gradle版本
    println(gradle.gradleVersion)
}
```

引入`Gradle插件`源码:


```groovy
def gradle = "C:\\Users\\Administrator\\.gradle\\caches\\modules-2\\files-2.1\\com.android.tools.build\\gradle\\7.0.0"
implementation fileTree(dir: gradle, include: ["*.jar", "*\\*.jar"])

def gradleApi = "C:\\Users\\Administrator\\.gradle\\caches\\modules-2\\files-2.1\\com.android.tools.build\\gradle-api\\7.0.0"
implementation fileTree(dir: gradleApi, include: ["*.jar", "*\\*.jar"])
```

最终代码:

```groovy
android {
    
    //输出gradle版本
    println(gradle.gradleVersion) //7.0.2

    def apkFolder = new File(project.rootDir.absolutePath + "/apk")//rootProject.file("/apk")
    apkFolder.mkdirs()
    println "APK输出目录:${apkFolder.absolutePath}"

    println(it) //extension 'android'
    println(it.class) //class com.android.build.gradle.internal.dsl.BaseAppModuleExtension_Decorated
    com.android.build.gradle.internal.dsl.BaseAppModuleExtension //点击跳转到目标类, 查看可操作的成员对象

    //com.android.build.gradle.AbstractAppExtension.getApplicationVariants //操作对象
    applicationVariants.all { variant ->
        println(variant) //com.android.build.gradle.internal.api.ApplicationVariantImpl_Decorated@a10a2fd
        println(variant.class) //class com.android.build.gradle.internal.api.ApplicationVariantImpl_Decorated
        com.android.build.gradle.internal.api.ApplicationVariantImpl //点击跳转到目标类, 查看可操作的成员对象

        if (variant.buildType.name != "debug") {
            //com.android.build.gradle.internal.api.ApkVariantImpl.getPackageApplicationProvider //操作对象
            //com.android.build.gradle.tasks.PackageAndroidArtifact.getOutputDirectory //操作对象
            variant.packageApplicationProvider.get().outputDirectory = apkFolder //修改输出的文件夹路径
        }

        //com.android.build.gradle.api.BaseVariant.getOutputs 操作对象
        variant.outputs.forEach {
            println(it) //ApkVariantOutputImpl_Decorated{variantOutput=VariantOutputImpl(versionCode=property(java.lang.Integer, provider(class java.lang.Integer)), versionName=property(java.lang.String, provider(class java.lang.String)), enabled=property(java.lang.Boolean, fixed(class java.lang.Boolean, true)), variantOutputConfiguration=VariantOutputConfigurationImpl(isUniversal=false, filters=[]), baseName=release, fullName=release, outputFileName=property(java.lang.String, fixed(class java.lang.String, Android_Gradle_DSL_7.0.0-release-unsigned.apk)))}
            println(it.class) //class com.android.build.gradle.internal.api.ApkVariantOutputImpl_Decorated
            com.android.build.gradle.internal.api.ApkVariantOutputImpl //点击跳转到目标类, 查看可操作的成员对象

            //com.android.build.gradle.internal.api.BaseVariantOutputImpl.setOutputFileName 操作对象
            it.outputFileName = "demo.apk" //最终修改生成的apk文件名
        }
    }
}
```


# 其他版本

[Android_Gradle_DSL_7.4.0](https://github.com/angcyo/Android_Gradle_DSL_7.4.0)

[Android_Gradle_DSL_7.2.1](https://github.com/angcyo/Android_Gradle_DSL_7.2.1)

[Android_Gradle_DSL_7.0.0](https://github.com/angcyo/Android_Gradle_DSL_7.0.0)

[Android_Gradle_DSL_4.1.0](https://github.com/angcyo/Android_Gradle_DSL_4.1.0)

[Android_Gradle_DSL_4.0.1](https://github.com/angcyo/Android_Gradle_DSL_4.0.1)

[Android_Gradle_DSL_4.0](https://github.com/angcyo/Android_Gradle_DSL_4.0)

[Android_Gradle_DSL_3.5](https://github.com/angcyo/Android_Gradle_DSL_3.5)

[Android_Gradle_DSL_3.3](https://github.com/angcyo/Android_Gradle_DSL_3.3)

[Android_Gradle_DSL_3.2](https://github.com/angcyo/Android_Gradle_DSL_3.2)
