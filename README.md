# Wat heb je nodig ?

- Toegang tot de docker image repo  -> https://registry.cp.kpn-dsh.com/
- Toegang tot dsh console           -> https://console.poc.kpn-dsh.com
- Docker                            -> https://hub.docker.com/_/hello-world
- Make                              -> https://chocolatey.org/install en vervolgens voer uit 
choco install make  
- Voorbeeld config voor de DSH
```bash
{
	"name": "transformer-group-1",
	"image": "registry.cp.kpn-dsh.com/ordina-codestar-1/transformer:1",
	"cpus": 0.1,
	"mem": 256,
	"env": {
		"KAFKA_TOPIC_FROM": "stream.training",
		"KAFKA_TOPIC_TO": "internal.gecombineerd-ordina-codestar-1",
		"API": "api-btc-coinbase-invoeren"
	},
	"instances": 1,
	"singleInstance": false,
	"needsToken": true,
	"user": "2036:2036"
}
```

# 1 ) Opdracht uitvoeren

# 2 ) Nieuwe image bakken en pushen.
```sh
command : docker login registry.cp.kpn-dsh.com
command : make all
```