# cheris
A configuration center used eureka


简介：
   cheris是服务治理框架Eureka的server端，cheris搭配hippo-serviceGoven项目运行，hippo-serviceGoven向cheris进行服务的注册或者
   已注册服务的这侧地址和端口号进行服务调用
   
配置：
   所有的配置都放在application.properties,以下是主要的配置字段，配置形式已key-value的形式
   
   * spring.application.name = your application name ---服务名(在注册的请况下 server 默认为 EUREKA-SERVER )、
   
   * server.port= your port   ---cheris绑定的端口号
   
   * eureka.client.serviceUrl.defaultZone = http://your host:your port/eureka  ---cheris对外提供的服务注册地址
   
   * eureka.client.fetch-registry = true/false  -- 是否拉取eureka服务器注册信息(如果是server 一般都为false)
   
   * eureka.client.registerWithEureka = true/false  -- 是否注册（server端一般不用注册，除非是集群）
   
   * eureka.server.enableSelfPreservation=true/false -- 这个属性是Eureka的自用保护模式，如果你的服务突然断掉,在集群情况将
                                                     --不会有什么问题，server和client之间会试着重连，默认每次30秒，重连三次没有回应
                                                     -- server端就会把服务踢掉，但在单机情况下，会保留服务的数据模式，所以调用会出现问题,
                                                     --这时将这个属性设为false,server端将不会保留服务
   *  eureka.instance.preferIpAddress = true/false  --设为true,就会地址以IP的形式出现,不然会以hostname的形式出现
   
   以上的就是cheris的最常用的配置字段，如果还想了解详细配置，详细阅读EurekaClientConfigBean和EurekaInstanceConfigBean这两个类
   
用法：
    执行EurekaServerApplication类的main方法就OK。同时cheris还会提供一个服务注册列表的可视化界面，可以查看服务注册的详细新，
    访问url--http://your host:your port/将会出现可视化界面,访问url--http://your host:your port/eureka/apps会出现服务注册的详细信息

