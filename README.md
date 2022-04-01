# Algemeen

- docker image repo : https://registry.cp.kpn-dsh.com/

# 1 ) Uitvoeren
command : docker login registry.cp.kpn-dsh.com
command : make all

# 3 ) Voorbeeld config @ DSH

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