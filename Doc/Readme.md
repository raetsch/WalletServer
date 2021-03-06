# Reference Doc for the Bismuth Wallet servers

What is that?

WIP

## Two kind of servers, same backend

- wallet_server
- wallet_websocket

## Available commands

### addfromalias (alias)

Takes an alias (string)

Returns matching address

### addlist (address)

Returns all transactions from `address` , last one first.  
Use with care.

### addlistlim (address, limit)

Returns the latest `limit` transactions from `address` , last one first.

### aliascheck (alias)

Takes an alias (string)

Sends back "Alias free" or "Alias registered"

## aliasesget (addresses)

Takes a list of addresses to resolve.  

Returns the list of aliases. 

### aliasget (address)

Takes an address.

Sends back the matching alias if any.

### annget

Get the current on chain announce message.

### annverget

Returns the current node version currently announced on the chain.

### balanceget (address)

Returns current balance for given `address`.

Returns  
`[balance, total_credits, total_debits, total_fees, total_rewards, balance_no_mempool]`

Ex:
`["98.34764109", "27908.23206709", "27852.10000000", "0.98335000", "43.19892400", "98.34764109000224"]`


### blocklast

Returns the current block height of the local node.

### diffget

Get current net diff from the companion node.  
Same as statusget[8].  
cached.  

Ex:  
`111.8`

### mpget

Returns the list of transactions currently in mempool.

### mpinsert (signed_transaction):

Takes a full signed transaction in the correct format (very sensitive)  
and send it for insertion into the local node mempool.

Sends back the mempool insert message (string)

### statusget

Get status info from the companion node.  
Cached for a small time.  

Returns 
`[node_address, nodes_count, nodes_list, threads_count, uptime, peers.consensus, peers.consensus_percentage, VERSION, diff, server_timestamp]`
Ex:
`["f67350e6e66fba4bc6f364a50f403a33c8b84b670d1fc762318aaa32", 17, ["51.15.46.90", "51.15.254.16", "51.15.211.156", "91.121.87.99", "176.31.245.46", "51.15.118.29", "198.245.62.30", "188.165.199.153", "46.105.43.213", "51.15.201.253", "51.15.213.94", "66.70.181.150", "91.121.77.179", "163.172.222.163", "51.15.47.212", "31.31.75.71", "127.0.0.1"], 22, 46151, 868704, 100.0, "4.2.8", [110.9695450958, 110.9695450958, 1.3199999332427979, 110.9689280571, 61.51417361117072, 37246896409942.2, 0.0006170386529355149, 868704], "1539846617.79"]`

### statusjson

Get extended status info from the companion node.  
Cached for a small time.  

Returns a json dict 
```
{"protocolversion": "mainnet0018", 
  "address": "3a33c8b84b670d1fc762318aaa32f67350e6e66fba4bc6f364a50f40", 
  "walletversion": "4.2.8", "testnet": false, "blocks": 868694, 
  "timeoffset": 0, "connections": 16, 
  "connections_list": ["198.245.62.30", "176.31.245.46", "51.15.118.29", "46.105.43.213", "51.15.213.94", "91.121.77.179", "91.121.87.99", "188.165.199.153", "127.0.0.1", "163.172.222.163", "66.70.181.150", "51.15.254.16", "51.15.201.253", "51.15.46.90", "51.15.211.156", "51.15.47.212"], 
  "difficulty": 110.9689516728, "threads": 21, "uptime": 45761, 
  "consensus": 868694, "consensus_percent": 93.75, "server_timestamp": "1539846227.82"}
```


### tokensget (address):

Takes an address.

Sends back the list of tokens and amount for that address.


