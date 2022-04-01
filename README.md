# Wat heb je nodig ?

- Toegang tot dsh console           -> https://console.poc.kpn-dsh.com
- Toegang tot de docker image repo  -> https://registry.cp.kpn-dsh.com/
- Docker                            -> https://hub.docker.com/_/hello-world
- Make                              -> https://chocolatey.org/install en vervolgens voer uit 
choco install make  
- Voorbeeld config een nieuwe service op de DSH
```bash
{
	"name": "transformer-group-1",
	"image": "registry.cp.kpn-dsh.com/ordina-codestar-1/transformer:1",
	"cpus": 0.1,
	"mem": 256,
	"env": {
		"KAFKA_TOPIC_FROM": "aanpassing-vereist-stream-invoeren",
		"KAFKA_TOPIC_TO": "aanpassing-vereist-stream-invoeren",
		"API": "aanpassing-vereist-api-btc-coinbase-invoeren"
	},
	"instances": 1,
	"singleInstance": false,
	"needsToken": true,
	"user": "2036:2036"
}
```

# 1 ) Opdracht uitvoeren
- a. Print de events uit de stream "stream.training" , zie https://kafka.js.org/docs/getting-started
- b. Zoek een publieke API om de huidge bitcoin prijs mee op te halen. 
- c. Voeg de huidge bitcoin prijs toe aan elke event en schrijf deze weg naar de stream "internal.gecombineerd-ordina-codestar-1" 

# 2 ) Nieuwe image bakken en pushen.
```sh
command : docker login registry.cp.kpn-dsh.com
command : make all
```