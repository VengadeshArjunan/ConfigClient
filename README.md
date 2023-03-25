# ConfigClient

http://localhost:8888/application/default
	{"name":"application","profiles":["default"],"label":null,"version":null,"state":null,"propertySources":[{"name":"file:/E:/config/application.properties","source":{"greeting":"Hello World from Config Server","spring.datasource.url":"jdbc:mysql://localhost:3306/demodb","spring.datasource.username":"root","spring.datasource.password":"welcome","spring.jpa.hibernate.ddl-auto":"create-drop","spring.jpa.show-sql":"true","spring.jpa.properties.hibernate.dialect":"org.hibernate.dialect.MySQL8Dialect","spring.jpa.properties.hibernate.dialect.storage_engine":"innodb"}}]}
	
http://localhost:8888/config-client/default
	{"name":"config-client","profiles":["default"],"label":null,"version":null,"state":null,"propertySources":[{"name":"file:/E:/config/config-client.properties","source":{"message":"Hello! from Spring Cloud Config Server for Config Client one"}},{"name":"file:/E:/config/application.properties","source":{"greeting":"Hello World from Config Server","spring.datasource.url":"jdbc:mysql://localhost:3306/demodb","spring.datasource.username":"root","spring.datasource.password":"welcome","spring.jpa.hibernate.ddl-auto":"create-drop","spring.jpa.show-sql":"true","spring.jpa.properties.hibernate.dialect":"org.hibernate.dialect.MySQL8Dialect","spring.jpa.properties.hibernate.dialect.storage_engine":"innodb"}}]}
	
http://localhost:8888/config-client2/default
	
	{"name":"config-client2","profiles":["default"],"label":null,"version":null,"state":null,"propertySources":[{"name":"file:/E:/config/config-client2.properties","source":{"message":"Hello! from Spring Cloud Config Server for Config Client two"}},{"name":"file:/E:/config/application.properties","source":{"greeting":"Hello World from Config Server","spring.datasource.url":"jdbc:mysql://localhost:3306/demodb","spring.datasource.username":"root","spring.datasource.password":"welcome","spring.jpa.hibernate.ddl-auto":"create-drop","spring.jpa.show-sql":"true","spring.jpa.properties.hibernate.dialect":"org.hibernate.dialect.MySQL8Dialect","spring.jpa.properties.hibernate.dialect.storage_engine":"innodb"}}]}

http://localhost:8080/greeting

		Hello World from Config Server
	
E:/config/config-client2.properties
	message:Hello! from Spring Cloud Config Server for Config Client two
E:/config/config-client.properties
	message:Hello! from Spring Cloud Config Server for Config Client one
E:/config/application.properties
	greeting=Hello World from Config Server
	spring.datasource.url=jdbc:mysql://localhost:3306/demodb
	spring.datasource.username=root
	spring.datasource.password=welcome
	#spring.datasource.driver-class-name=com.mysql.jdbc.Driver
	spring.jpa.hibernate.ddl-auto=create-drop
	spring.jpa.show-sql=true
	spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQL8Dialect
	spring.jpa.properties.hibernate.dialect.storage_engine=innodb
	
	
	
When we updated the application.properties greetings in runtime it wont updated in the  configclient.
	greeting=Hello World from Config Server Updated
	
	for this we need to refresh the actuator. we used @refreshscope  this will take care of this
	
	create post method request in postman
		http://localhost:8080/actuator/refresh
		
	
	this will refresh the properties
	
	
	http://localhost:8080/greeting
	
		Hello World from Config Server Updated
		
	
