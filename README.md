# Apache Karaf Essentials - Managed Service Factory


To build this project use
```
    mvn install
```

This sample requires Apache Camel to be installed to Karaf. 

Use the following to install the dependency:
```
   feature:repo-add mvn:org.apache.camel.karaf/apache-camel/3.6.0/xml/features
   feature:install camel-core
   feature:install camel-blueprint
```

This sample requires Commons-Lang. 

Use the following to install the dependency:
```
   karaf@root()> install mvn:commons-lang/commons-lang/2.6
   Bundle ID: 119
   karaf@root()> start 119
   karaf@root()>
```

To deploy the project in Karaf, run the following command from its shell:
```
    bundle:install -s mvn:com.savoir/msf/1.0.0-SNAPSHOT
```

Configuration of the MSF should reside in KARAF_BASE/etc. 
Create a pair of files com.savoir.msf.hellofactory-test1.cfg and com.savoir.msf.hellofactory-test2.cfg.

Each file should contain content as below:
```
HELLO_GREETING=hello
HELLO_NAME=jamie
```

See sample/etc folder for samples.

A Camel Context will be instantiated for the MSF.
```
 karaf@root()> camel:context-list
 Context        Status              Total #       Failed #     Inflight #   Uptime
 -------        ------              -------       --------     ----------   ------
 helloContext   Started                   0              0              0   45.760 seconds
```

A route will be instantiated for each configuration provided.
Note: Until configs are available, no routes will be displayed.

Executing camel:route-list will display each configured instance
of the Hello route.
```
karaf@root()> camel:route-list
 Context        Route          Status              Total #       Failed #     Inflight #   Uptime
 -------        -----          ------              -------       --------     ----------   ------
 helloContext   Hello jamie    Started                   7              0              0   1 minute
 helloContext   Hello laura    Started                   1              0              0   5.782 seconds
karaf@root()>
```

For more help see the Apache Camel documentation

    http://camel.apache.org/
