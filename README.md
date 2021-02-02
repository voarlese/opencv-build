# opencv-build
下載 opencv java 後 build lib的方法

# JAVA 取得 OPENCV LIB
* 下載source code : [opencv release](https://opencv.org/releases/)

* 下載cmake (homebrew)
* 安裝 ant

## build opencv
1. 
```
cd opencv-4.1.1
cmake -S . -B build
```
會在 build 資料夾下產生build 的檔案

2. 
```
cd build
make -j8 #可開啟多核 加快編譯速度
```
這步完成後會在build/lib 內產生很多dylib元件

3. 
接下來處理java, 在build/modules/java 內的是java 相關元件
```
cd build/modules/java
make -j8
```

完成後
jar/opencv/java 內的源碼就可以拿來用囉

在java 中引入so庫
```java
import org.opencv.core.Core;

public class OpenCVExample1 {
    static {
        System.loadLibrary(Core.NATIVE_LIBRARY_NAME);
    }
}


```


java 在 run 的時候必須引入so 庫位置
```zsh
java -jar -Djava.library.path=/opencv-4.5.1/build/lib xxx.jar

```
## 參考文檔
忘了... 有人找到麻煩提醒我

