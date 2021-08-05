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

# 其他版本

[Android_Gradle_DSL_7.0.0](https://github.com/angcyo/Android_Gradle_DSL_7.0.0)

[Android_Gradle_DSL_4.1.0](https://github.com/angcyo/Android_Gradle_DSL_4.1.0)

[Android_Gradle_DSL_4.0.1](https://github.com/angcyo/Android_Gradle_DSL_4.0.1)

[Android_Gradle_DSL_4.0](https://github.com/angcyo/Android_Gradle_DSL_4.0)

[Android_Gradle_DSL_3.5](https://github.com/angcyo/Android_Gradle_DSL_3.5)

[Android_Gradle_DSL_3.3](https://github.com/angcyo/Android_Gradle_DSL_3.3)

[Android_Gradle_DSL_3.2](https://github.com/angcyo/Android_Gradle_DSL_3.2)