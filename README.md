## First Camel Route Example
This project shows a simple example of a route using Apache Camel and the Spring DSL. It has a restlet endpoint that asks for the price of a stock code. The route uses a simple content-based router that takes the stock code into account: if the stock code is NASDAQ or  DOWJONES it provides a hard coded price. Otherwise, it forwards the request to the google finance API and returns the current price to the caller. 

## Prerequisites
You must have a CXP project configured in your machine before performing this exercise. Follow the instructions on the following site: https://my.backbase.com/docs/how-to-guides/getting-your-first-launchpad-based-portal-set-up/

### Installation & Configuration

- Copy **integration-service-exercise-00** into the **services** folder of your project. You can use the git command to clone the project: ```git clone https://github.com/marciofk/integration-service-exercise-00.git```

- Include **integration-service-exercise-00** module to the build.  Open `services/pom.xml` and add **integration-service-exercise-00** in the `<modules>` section: 
	```xml
	    <modules>
	        ...	    
	        <module>integration-service-exercise-00</module>
	        ...
	    </modules>
	```	
	Re-compile **services** by executing `mvn clean install` in the **services** folder.
	
- Enable newly created module in the Portalserver application. In the `<dependencies>` section of `webapps/portalserver/pom.xml`, add the following dependency:

	```xml
	    <dependency>
	        <groupId>com.backbase.training</groupId>
	        <artifactId>integration-service-exercise-00</artifactId>
	        <version>1.0-SNAPSHOT</version>
	    </dependency>
	```

### Build & Run

- If Portalserver application is already running, stop it by pressing *Ctrl+C*. Start Portalserver application by executing `mvn jetty:run` command from the **webapps/portalserver** directory.
- Using a REST client app (e.g. Postman), test the route execution. Example to get the stock price of the HSBC Bank: http://localhost:7777/portalserver/services/rest/stock/HSBA.L/price?country=US
