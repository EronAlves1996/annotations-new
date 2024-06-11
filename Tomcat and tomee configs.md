Launch
```
-Dcatalina.base="/home/letwe/eclipse-workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0" -Dcatalina.home="/home/letwe/servers/apache-tomee-plus-8.0.6" -Dwtp.deploy="/home/letwe/eclipse-workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/wtpwebapps" -Djava.endorsed.dirs="/home/letwe/servers/apache-tomee-plus-8.0.6/endorsed" -Dorg.apache.el.parser.COERCE_TO_ZERO=false -Dfile.encoding=UTF-8 -Xms512M -Xmx512M -DGRADETI_GACE_URL="https://hml.gace.gtiplug.com.br/gace" -Dbr.com.cabtecgti.gtimid.base_url=https://hml.gtimid.gtiplug.com.br/gti-mid -DGTI_MQTT_BROKER_URL="tcp://35.223.100.114:1883" -DtestServices=true -Duser.language=pt-BR
```

Tommee

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tomee>
  <!-- see http://tomee.apache.org/containers-and-resources.html -->

  <!-- activate next line to be able to deploy applications in apps -->
  <!-- <Deployments dir="apps" /> -->


	<!-- WMS ====================================================================== -->
	<Resource id="RFS_DS" type="DataSource">
	  jtaManaged = true
	  jdbcDriver = com.mysql.jdbc.Driver
	  jdbcUrl = jdbc:mysql://localhost:3306/gtiwms?autoReconnect=true
	  userName = root
	  password = root	
          connectionProperties = [autoReconnect=true,autoReconnectForPools=true]
          defaultAutoCommit = false
          testOnBorrow = true
          validationQuery = SELECT 1
          validationInterval = 300000
	  maxActive = 10
	  maxWait = -1
	  maxIdle = 2
	  removeAbandoned = true
	  logAbandoned = true
	  removeAbandonedTimeout = 600
	</Resource>
	<Resource id="RFS_DS_NON_MANEGED" type="DataSource">
	  jtaManaged false
	  jdbcDriver com.mysql.jdbc.Driver
	  jdbcUrl = jdbc:mysql://localhost:3306/gtiwms?autoReconnect=true
	  userName = root
	  password = root
          connectionProperties [autoReconnect=true,autoReconnectForPools=true]
          defaultAutoCommit false
          testOnBorrow true
          validationQuery SELECT 1
          validationInterval 300000
	  maxActive 10
	  maxWait -1
	  maxIdle 2
	  removeAbandoned true
	  logAbandoned true
	  removeAbandonedTimeout 600
	</Resource>
	<!-- /WMS ====================================================================== -->

</tomee>
```