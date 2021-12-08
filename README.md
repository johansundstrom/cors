# CORS - Cross-Origin Resource Sharing

## Bakgrund

<img src="images/cors-fail.png">
fig 1

* Anledningen till ovanstående är CORS-implementationen i webbläsare
* En domänresurs anropar annan

<img src="images/cors-fail2.png">
fig 2

CORS träder in i följande fall

* Annan domän - example.com anropar api.com
* Annan subdomän - subdomän på example.com anropar api.com
* Annan port - example.com anropar example.com:3000
* Annat protokoll - https://example.com anropar http://example.com

## Bakom skynket

* Response kommer fram men webbläsaren ger inte JavaScript tillstånd att nå responsen

### preflight

* Icke-enkla requests startar en mekanism som kallas *preflight*
* Exempel på icke-enkla requests är...
  * requests som inkluderar cookies
  * ```Content-type``` som inte är ```application/x-ww-form-urlencoded```, ```multipart/form-data``` eller ```text-plain```
* *preflight* sänder en ```OPTIONS``` request till servern och får response
* I figur 1 har preflight inhämtat response men får inte tillgång till resultatet

## Lösning

### 1 - Tillgång till client- och server kod

* Ange en vitlista i ```Access-Control-Allow-Origin``` headern på servern

### 2 - Tillgång till client kod med inte server kod

* Använd proxyserver
