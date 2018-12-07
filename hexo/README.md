### hexo 

#### `docker`初始化

执行命令：
```c 
cd ./docker/
cp .env.example .env 
make start
```

`make`会执行`Makefile`里面的命令牌，具体命令参照`Makefile`文件。

#### `hexo`初始化

启动容器后，执行相关`make`命令启动容器：
```c 
cd ./docker/ 
make hexo 
```

进入容器后，执行`hexo init`，就会在`blog`目录下进行初始化，就可以在`blog`中配置主题和写博文了。


#### `Travis CI`自动部署到Github Page 

我们可以在`Github`上面配置`Travis CI`，使你文章提交到`Github`上后，自动`deploy`到对应的`Page Repository`。

可以参考`.travis.yml`文件内容，形如`${UserName}`的是配置在`Travis CI`上的名为`UserName`的环境变量。
