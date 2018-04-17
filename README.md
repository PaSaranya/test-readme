+++
categories = ["keystone"]
date = "2018-03-29T00:00:43-05:00"
glyph = "fa-book"
summary = "Spring Externalizing Configurations"
tags = ["[pcf]","[Externalizing Configurations]"]
title = "PCF Externalizing Configurations"

+++



# Externalizing Configurations of Micro Services

The Objective of Externalizing configuration is to provide a configurable repo to manage an application’s environmental properties across all environments.

The RI covers the below scenarios

```
Loading non-secure environment properties from config server
Loading secure environment properties from Vault server
Loading updated properties from Git using Refresh endpoint
```

## Getting Started

This journey will cover how to load the non-secure environment properties from git repo through config server url and secure environment properties from Vault server. Also show how properties are refreshed using refresh endpoint in client application


## Prerequisites

```
- MyEclipse or STS IDE
- Config and Vault servers installed
- Use the below link to download the Vault Server and install it in vdi

 https://www.vaultproject.io/downloads.html

- Configure an Git repo pointed by config server
- Vault token and config server’s url to be given in client application

```

## Storing secured properties

To store secured properties of an application Vault server is used. Download the vault executable from the above link and give the below command to start the vault server in our vdi
```
	vault server -dev
```
Once the vault server starts vault token will be generated. Replace the vault token in bootstrap.yml with your generated vault token. In this app, vault server is stored with private key of git repo which is used by the config server to get connected to Git. We have also stored LDAP's url, group and user patterns to authenticate the application using username and password.

To write to vault server, refer to below syntax,
```
	vault write secret/<APP_NAME> key=value
```
Note: To store multiple key value pair, give all the key value pairs in single command
	
## Storing non-secured properties
	To store non-secured properties git repo is used which is connected through config server. We can also load the updated properties from git repo to our application by using the refresh endpoint of the client application.
	
## Build
Build the config-server application and client application using maven.


## Running the tests
1) Start the Vault and Config Server.
2) Testing can be done by using client application. 
3) Login to the below url
	http://localhost:8080/index
4) Since LDAP 




## Built With

* Java 8
* [Spring](https://spring.io/docs) - The framework used was Spring Boot version 1.5.6
* [Maven](https://maven.apache.org/) - Dependency Management

## Contributing

