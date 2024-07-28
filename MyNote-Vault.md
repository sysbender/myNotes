# MyNote-Vault

## MyNote-Vault

* install
* manageing vault server
* managing access and secrets in hashiCorp Vault
* Integrat CICD

Vault Associate Certified

## install

### 0. Conceptual Architecture

* authentication - method -
* Policy - acl - control what to do on a path
* Secrets - engine - what we need to protect
* audit - record

client type

* user
* app
* machine

flow

* authenticate to API
* token - identify , action

### 1. running the dev instance

```
choco install valut

#linux - add repo, install, 

vault server -dev

#ps
$env:VAULT_ADDR="http://127.0.0.1:8200"

vault login   # new version caches root tokey, don't need login

```

development mode

* localhost without ssl
* in-memory storage
* unsearled with token cached
* UI enabled
* Key/Value secrets engine enabled

#### vault cli:

vault command subcommand vault command help valut path-help path

```
# env
VAULT_ADDR
VAULT_TOKEN : go to cache
VAULT_SKIP_VERIFY
VAULT_FORMAT : json


```

### 2. designing a deployment

deployment models

#### logical architecture

api => TLS certificate storage => Encryption key => master key => unseal key(outside)

#### component

compute : machine, OS, network: client/storage , load balancer storage : certificate : TLS certificate (private,self-sign, public)

monitor - backup

* key shares
* server configuration
* distributed key shares
* auto unseal

#### configuration

HCL/JSON, multiple, restart to load config

* single value
* blocks
  * listener
  * storage
    * object -
    * db
    * kv -consule \*
    * file
    * memory
    * integrated storage(Raft) \*
      *
        * local storage
      * HA
      * Replicated
  * seal - auto unseal
  * telemetry -send info to exteral monitoring service
  * service registration - register vault to consul/k8s

```
storage "consul"{
    address ="127.0.0.1:8500"
    path= "vault"
}

storage "raft"{
    path ="/opt/vault/data"
    node_id ="vault-0"
    retry_join {
        leader_tls_servername ="vault-0.local"
        leader_api_addr ="https://vault-0.local:8200"
        cert...
    }
}



```

* single
  * general
    * ui
    * disable\_mlock
    * log\_level
    * log\_format
    * ma

### 3. deploying vault server

prerequisites:

* registered public domain
* openssl installed

tasks:

* prepare requests
* validate with DNS
* Generate PFX files

### 4. configuring high availability

### 5. managing encryption and seal keys

### 6. configuring authentication and secrets

### 7. setting up auditing and monitoring
