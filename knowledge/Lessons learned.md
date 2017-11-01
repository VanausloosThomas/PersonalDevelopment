# Lessons learned

## Maven
* Elk project heeft een hoofd POM.xml file. 
* 	In deze file gaan we het dependency management van heel het project regelen. Hier worden de versies (als properties!!!) van dependencies en plugins gedeclareerd als ook de exclusions van bepaalde versies.
*  Bovenaan elke hoofd POM.xml gaan we de spring.io parent pom ge bruiken:
*  ```
	 <parent>
        <groupId>io.spring.platform</groupId>
        <artifactId>platform-bom</artifactId>
        <version>Brussels-SR5</version>
        <relativePath/>
    </parent>
	```
* Deze parent pom bestaat uit allerlei dependencies en versies die reeds samen compatiebel zijn ! 
* We nemen al de versies uit de parent pom over in ons projevt (worden mee over geerfd). Als we een dependencie willen gebruiken moeten we deze wel nog vermelden in onze eigen pom files (zonder versie dan)
* Een versie voor een dependencie in een child pom overschrijft de versie die door de parent pom wordt bepaald


## Stappenplan om alle dependencies op te kuisen in een project
*  Zorg dat er enkele dependenciemanagement gebeurd in de hoofd pom
*  Er mogen geen versies in de child poms voorkomen, enkel in de hoofd pom. Hier moeten ze voorkomen als maven properties 
* ```<dependency.version>10.0.0.3Final</dependency.version> 
	  <version>${dependency.version}</version>``` 
ipv ``` <version>10.0.0.3Final</version>```
*

## Logstash
Logstash utils is een dependency van de vdab die allerlei metadata in een JSON plaatst zodat we deze beschikbaar hebben bij het zoeken in Kibana.
Voorbeelden zijn: 
* Application name
* Calling application
* ...