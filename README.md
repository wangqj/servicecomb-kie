# Apache-ServiceComb-Kie

A service for key value management in distributed system.

## Conceptions

### Key
key could indicate a configuration like "timeout",
then the value could be "3s"
or indicates a file name "app.properties", 
then the value could be content of app.properties

### labels
Each key could has labels. labels indicates a unique key.
A key "log_level" with labels "env=production" 
may saves the value "INFO" for all application log level in production environment.
A key "log_level" with labels "env=production, component=payment" 
may saves the value "DEBUG" for payment service in production environment.

it means all payment service print debug log, but for other service print info log.

so you can control your application runtime behaviors 
by setting different labels to a key.



## Components
it includes 5 components

- server: rest api service to manage kv
- client: restful client for go
- kie-template: agent can be deployed in your k8s pod 
or VM, it connects to server and writes kv into config file 
based on template language
- kiectl: CLI tool for kie
- frontend: web console for kie

## Features

TODO
- simple key name with rich labels: user can define labels for a key, 
that distinguish from key to another key.  
a key will not be stringed by fixed schema. 
labels for a key is like "env=test, service=cart, version=1.0" or "cluster=xxx"  
or "env=test, service=cart, version=1.0, ip=x.x.x.x"
- validator: value can be checked by user defined python script, 
so in runtime if someone want to change this value, 
the script will check if this value is appropriate.
- encryption web hook: value can by encrypt 
by your custom encryption service like vault.
- Long polling: client can get key value changes by long polling
- config view: by setting labels criteria, servicecomb-kie 
is able to aggregate a view to return all key values which match those labels, 
so that operator can mange key in their own understanding 
to a distributed system in separated views.
- rich value type: not only plain text, but support to be aware of ini, json,yaml,xml and java properties
- heterogeneous config server: able to fetch configuration in k8s and consul 
 even more, you can update, delete, 
 and use config view for those systems, 
 and you can integrate with your own config system to MetaConfig by 
 following standardized API and model
- consul compatible: partially compatible with consul kv management API
- kv change history: all kv changes is recorded and can be easily roll back by UI
## Quick Start

## Contact

Bugs: [issues](https://issues.apache.org/jira/browse/SCB)

## Contributing

See [Contribution guide](/CONTRIBUTING.md) for details on submitting patches and the contribution workflow.

## Reporting Issues

See reporting bugs for details about reporting any issues.