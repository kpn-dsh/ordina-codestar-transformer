# Wat heb je nodig ?

- Toegang tot DSH console           -> https://console.poc.kpn-dsh.com
- Toegang tot de docker image repo  -> https://registry.cp.kpn-dsh.com/
- Docker                            -> https://hub.docker.com/_/hello-world
- Make                              -> https://chocolatey.org/install en vervolgens voer uit 
choco install make  
- Voorbeeld config een nieuwe service op de DSH
```bash
{
	"name": "transformer-group-1",
	"image": "registry.cp.kpn-dsh.com/ordina-codestar-1/transformer-group-1:1",
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

# TENANT ordina-codestar-1

# 1 ) Opdracht uitvoeren
- a. Pas de groepsnummer aan in de makefile
- b. Print de events uit de stream "stream.training" , zie https://kafka.js.org/docs/getting-started. Zorg ervoor dat deze prints zichbaar zijn in het console op de DSH.
- c. Maak een service aan op de DSH met de naam en image "transformer-group-1" <--- voeg de juiste groepsnummer toe
- d. Zoek een publieke API om de huidge bitcoin prijs mee op te halen. 
- e. Voeg de huidge bitcoin prijs toe aan elke event en schrijf deze weg naar de stream "internal.gecombineerd-ordina-codestar-1" 

- *bij elke aanpassing wordt geacht om de wijzigingen te pushen en te testen op de DSH (make all) & services restarten op de DSH*

# 2 ) Nieuwe image bakken en pushen.
- Voor de docker login heb je credentials nodig. Je kan deze terugvinden in image repository -> user profile.
```sh
command : docker login registry.cp.kpn-dsh.com
command : make all
```