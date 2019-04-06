#升级Spring Boot 可运行jar包的驱动程序
整合Alibaba开源的配置与服务注册nacos的时候，由于后台数据库用的是MySQL 8.0.15, 而nacos自带的JDBC Driver是5.x版本的，无法存储配置，所以需要更新驱动版本。
直接用压缩工具删除旧版本驱动再把新jar文件加进去是不行的，需要解压到本地目录，替换jar后执行：
jar -cvf0m nacos-server.jar .\META-INF\MANIFEST.MF .