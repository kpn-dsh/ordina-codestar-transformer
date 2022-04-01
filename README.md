# What do you need ?

- Access to the DSH console         -> https://console.poc.kpn-dsh.com
- Access to the docker image repo  	-> https://registry.cp.kpn-dsh.com/
- Docker                            -> https://hub.docker.com/_/hello-world
- Make                              -> install -> https://chocolatey.org/install & choco install make  
- Example config of a service on the DSH
```bash
{
	"name": "transformer-group-1",
	"image": "registry.cp.kpn-dsh.com/ordina-codestar-1/transformer-group-1:1",
	"cpus": 0.1,
	"mem": 256,
	"env": {
		"KAFKA_TOPIC_FROM": "change-required",
		"KAFKA_TOPIC_TO": "change-required",
		"API": "change-required"
	},
	"instances": 1,
	"singleInstance": false,
	"needsToken": true,
	"user": "2036:2036"
}
```

# TENANT ordina-codestar-1

# 1 ) Assignments
- a. Change the group number in the makefile. e.g: "tagname=transformer-group-1" <--- add the correct group number. 

- b. Print events from the stream "internal.gecombineerd-ordina-codestar-1", see https://kafka.js.org/docs/getting-started.

- c. Create a service on the DSH with the name "transformer-group-1" <--- add the correct group number. Also change the service config on the DSH with the correct image name e.g: "image": "registry.cp.kpn-dsh.com/ordina-codestar-1/transformer-group-1:1"

- d. Search for an api to get the current bitcoin price. 

- e. Add the bitcoin price to each event and write this to another stream with the name "internal.gecombineerd-ordina-codestar-1"

- f. In this workshop there a multiple groups producing on this stream. Please make sure to add a key to the message {value="hello" ,group:"group-1"}. We can use this identifier to only print messages intended for your group.


- *It's important to push the changes to the image repository so you can test it on the DSH. Also make sure you restart the service*

# 2 ) Docker login & Make all.
- You need credentials for the command docker login. You can find your credentials in the image repo under the userprofile.
```sh
command : docker login registry.cp.kpn-dsh.com
command : make all
```