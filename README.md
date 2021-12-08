# CORS - Cross-Origin Resource Sharing

## Bakgrund

<img src="images/cors-fail.png">

* Anledningen till ovanstående är CORS-implementationen i webbläsare
* En domänresurs anropar annan

<img src="images/cors-fail2.png">

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
  * ```Content-type``` som inte är ```application/x-ww-form-urlencoded```, ```multipart/form-data``` eller ```text-plain````
* 
