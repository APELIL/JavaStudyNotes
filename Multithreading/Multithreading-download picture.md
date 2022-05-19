# Multithreading-download picture

```java
package Thread;

import org.apache.commons.io.FileUtils;

import java.io.File;
import java.io.IOException;
import java.net.URL;

public class TreadDownloadPic extends Thread{
    // 1.attributes
    String url;
    String file;
    // 2. constructor with parameter
    public TreadDownloadPic(String url, String file){
        this.url = url;
        this.file = file;
    }
    @Override
    // threading of download picture
    public void run() {
       WebDownloader webDownloader = new WebDownloader();
       webDownloader.download(url,file);
        System.out.println("download file+"+file);
    }

    public static void main(String[] args) {
        TreadDownloadPic t1 =  new TreadDownloadPic("https://www.dimondpony.com/data/logo/20211011/16433678798.png", "1.jpg");
        TreadDownloadPic t2 =  new TreadDownloadPic("https://www.dimondpony.com/data/upload/pimg/20211203/16445959621.jpg", "2.jpg");
        TreadDownloadPic t3 =  new TreadDownloadPic("https://www.dimondpony.com/data/upload/pimg/20220302/16464466573.jpg", "3.jpg");
        //call start() to use multithreading
        t1.start();
        t2.start();
        t3.start();
    }
}

class WebDownloader{
    public void download(String url, String file){
        try {
            FileUtils.copyURLToFile(new URL(url), new File(file));
        } catch (IOException e) {
            e.printStackTrace();
            System.out.println("Issue on downloading");
        }
    }

}
```

