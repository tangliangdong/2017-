---
title: Hello World
---
Welcome to [Hexo](https://hexo.io/)! This is your very first post. Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues).

## Quick Start

### Create a new post

``` bash
$ hexo new "My New Post"
$ hexo new "My New Post"
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` java
public class Book {
    int readCount = 0;
    Semaphore rmutext = new Semaphore(1);
    Semaphore wmutext = new Semaphore(1);

    public void read() throws InterruptedException {
        rmutext.acquire();
        if (readCount==0){
            wmutext.acquire();
        }
        readCount++;
        System.out.println(readCount+"个读者正在阅读");
        rmutext.release();

        Thread.sleep(1000);

        rmutext.acquire();
        readCount--;
        System.out.println("还剩 "+readCount+" 读者");

        if(readCount==0){
            wmutext.release();
        }
        rmutext.release();

    }

    public void write() throws InterruptedException {
        System.out.println("写者等待写作");
        wmutext.acquire();
        System.out.println("写者正在写文章");
        Thread.sleep(1000);
        System.out.println("写者结束写文章");
        wmutext.release();
    }
}
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)
