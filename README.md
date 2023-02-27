# Prohashing JS
Simple implementation of the Prohashing WAMP interface

## Installation
```npm install prohashing```

## Dependencies
* Autobahn|JS - https://github.com/crossbario/autobahn-js/
* ws - https://github.com/websockets/ws

## Config
* ```apiKey``` Your Prohashing API Key
* ```degug``` True or False on whether or not to output debugging information
* ```subscribe``` Either "all" (for all events) or an array containing the events you want to subscribe to.  
Options are : ```['miners', 'profitability', 'systemStatus', 'blocks']``` .  See the API Documentation https://prohashing.com/help.html for full details on each.

## Usage
```javascript
const prohashing = require("prohashing")
const connection = new prohashing({ 
	apiKey: "7b10effd1b66a2f14fbb6130a4fd3b629ae6355f198607224903b5d62fc76718", 
	debug: false ,
	subscribe : ['systemStatus', 'miners']
})

connection.on("minerStatus", (update) => {
	console.log("MINER UPDATE")
	console.log(update)
})

connection.on("balanceStatus", (update) => {
	console.log("BALANCE UPDATE")
   	console.log(update)
})

connection.on("connected", (details, session) => {
	console.log("Connected to Prohashing WAMP")
})

connection.on("block", (block) => {
	console.log("BLOCK UPDATE")
	console.log(block)
})

connection.on("systemStatus", (status) => {
	console.log("STATUS", status)
})
```
