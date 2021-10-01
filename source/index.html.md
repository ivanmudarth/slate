--- 

title: Cohesity REST API 

language_tabs: 
   - shell 

toc_footers: 
   - <a href='#'>Sign Up for a Developer Key</a> 
   - <a href='https://github.com/lavkumarv'>Documentation Powered by lav</a> 

includes: 
   - errors 

search: true 

--- 

# Introduction 

Cohesity API provides a RESTful interface to access the various data management operations on Cohesity cluster and Helios. 

**Version:** 2.0 

# Authentication 

|apiKey|*API Key*|
|---|---| 

# /ACTIVE-DIRECTORIES
## ***GET*** 

**Summary:** Get the list of Active Directories.

**Description:** Get the list of Active Directories.

### HTTP Request 
`***GET*** /active-directories` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| domainNames | query | Filter by a list of Active Directory domain names. | No | array |
| ids | query | Filter by a list of Active Directory Ids. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Protection Groups which were created by all tenants which the current user has permission to see. If false, then only Protection Groups created by the current user will be returned. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create an Active Directory.

**Description:** Create an Active Directory.

### HTTP Request 
`***POST*** /active-directories` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create an Active Directory. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /ACTIVE-DIRECTORIES/{ID}
## ***GET*** 

**Summary:** Get an Active Directory by id.

**Description:** Get an Active Directory by id.

### HTTP Request 
`***GET*** /active-directories/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies id of an Active Directory. | Yes | long |
| includeCentrifyZones | query | Specifies whether to include Centrify Zones of the Active Directory in response. | No | boolean |
| includeDomainControllers | query | Specifies whether to include Domain Controllers of the Active Directory in response. | No | boolean |
| includeSecurityPrincipals | query | Specifies whether to include Security Principals of the Active Directory in response. | No | boolean |
| prefix | query | Specifies a prefix, only security principals with name or sAMAccountName having this prefix (ignoring cases) will be returned. This field is appliciable and mandatory if 'includeSecurityPrincipals' is set to true. | No | string |
| objectClass | query | Specifies a list of object classes, only security principals with object class in this list will be returned. This field is appliciable if 'includeSecurityPrincipals' is set to true. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update an Active Directory.

**Description:** Update an Active Directory.

### HTTP Request 
`***PUT*** /active-directories/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies id of an Active Directory. | Yes | long |
| body | body | Request to update an Active Directory. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete an Active Directory.

**Description:** Delete an Active Directory.

### HTTP Request 
`***DELETE*** /active-directories/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies id of an Active Directory. | Yes | long |
| activeDirectoryAdminUsername | header | Specifies the username of the Active Direcotry Admin. | Yes | string |
| activeDirectoryAdminPassword | header | Specifies the password of the Active Direcotry Admin. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /ALERTSSUMMARY
## ***GET*** 

**Summary:** Get alerts summary.

**Description:** Get alerts summary grouped by category.

### HTTP Request 
`***GET*** /alertsSummary` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| startTimeUsecs | query | Filter by start time. Specify the start time as a Unix epoch Timestamp (in microseconds). By default it is current time minus a day. | No | long |
| endTimeUsecs | query | Filter by end time. Specify the end time as a Unix epoch Timestamp (in microseconds). By default it is current time. | No | long |
| includeTenants | query | IncludeTenants specifies if alerts of all the tenants under the hierarchy of the logged in user's organization should be used to compute summary. | No | boolean |
| tenantIds | query | TenantIds contains ids of the tenants for which alerts are to be used to compute summary. | No | array |
| statesList | query | Specifies list of alert states to filter alerts by. If not specified, only open alerts will be used to get summary. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /AUDIT-LOGS
## ***GET*** 

**Summary:** Get cluster audit logs.

**Description:** Get a cluster audit logs.

### HTTP Request 
`***GET*** /audit-logs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| searchString | query | Search audit logs by 'entityName' or 'details'. | No | string |
| usernames | query | Specifies a list of usernames, only audit logs made by these users will be returned. | No | array |
| domains | query | Specifies a list of domains, only audit logs made by user in these domains will be returned. | No | array |
| entityTypes | query | Specifies a list of entity types, only audit logs containing these entity types will be returned. | No | array |
| actions | query | Specifies a list of actions, only audit logs containing these actions will be returned. | No | array |
| startTimeUsecs | query | Specifies a unix timestamp in microseconds, only audit logs made after this time will be returned. | No | long |
| endTimeUsecs | query | Specifies a unix timestamp in microseconds, only audit logs made before this time will be returned. | No | long |
| tenantIds | query | Specifies a list of tenant ids, only audit logs made by these tenants will be returned. | No | array |
| includeTenants | query | If true, the response will include Protection Groups which were created by all tenants which the current user has permission to see. If false, then only Protection Groups created by the current user will be returned. | No | boolean |
| startIndex | query | Specifies a start index. The oldest logs before this index will skipped, only audit logs from this index will be fetched. | No | long |
| count | query | Specifies the number of indexed obejcts to be fetched from the specified start index. | No | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /AUDIT-LOGS/ACTIONS
## ***GET*** 

**Summary:** Get cluster audit logs actions.

**Description:** Get all actions of cluster audit logs.

### HTTP Request 
`***GET*** /audit-logs/actions` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /AUDIT-LOGS/ENTITY-TYPES
## ***GET*** 

**Summary:** Get cluster audit logs entity types.

**Description:** Get all entity types of cluster audit logs.

### HTTP Request 
`***GET*** /audit-logs/entity-types` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /AUDIT-LOGS/FILER-CONFIGS
## ***GET*** 

**Summary:** Get filer audit log configs.

**Description:** Get filer audit log configs.

### HTTP Request 
`***GET*** /audit-logs/filer-configs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update filer audit log configs.

**Description:** Update filer audit log configs.

### HTTP Request 
`***PUT*** /audit-logs/filer-configs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the filer audit log config to update. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /CHASSIS
## ***GET*** 

**Summary:** Get list of chassis

**Description:** Get list of all chassis info that are part of cluster.

### HTTP Request 
`***GET*** /chassis` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| noRackAssigned | query | Filters chassis that have no rack assigned. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /CHASSIS/{ID}
## ***GET*** 

**Summary:** Get a chassis by chassis id.

**Description:** Get a chassis info by id.

### HTTP Request 
`***GET*** /chassis/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of chassis. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PATCH*** 

**Summary:** Update a chassis by chassis id.

**Description:** Update selected properties of chassis info by id.

### HTTP Request 
`***PATCH*** /chassis/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of chassis. | Yes | long |
| body | body | Specifies the parameters to update chassis. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /CIPHERS
## ***GET*** 

**Summary:** Gets the list of ciphers enabled on the cluster.

**Description:** Gets the list of ciphers enabled on the cluster.

### HTTP Request 
`***GET*** /ciphers` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Enable/Disable a list of ciphers on the cluster. Iris must be restarted for the change to take effect.

**Description:** Enable/Disable a list of ciphers on the cluster.

### HTTP Request 
`***POST*** /ciphers` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Enable/Disable ciphers. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /CLIENTCSR
## ***POST*** 

**Summary:** Create Certificate Signing Requests on the cluster.

**Description:** Create two Certificate Signing Request on the cluster with the given details one each for client and server. Each service can have at most one outstanding pair of CSR.

### HTTP Request 
`***POST*** /clientcsr` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create the Certificate Signing Requests. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /CLIENTCSR/CERTIFICATE
## ***POST*** 

**Summary:** Import the signed certificates on the cluster after the Certificate Signing Requests are created.

**Description:** Import the signed certificates on the cluster after the Certificate Signing Requests are created.

### HTTP Request 
`***POST*** /clientcsr/certificate` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to import the certificate. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /CLUSTERS
## ***GET*** 

**Summary:** Retrieve Cluster Configuration

**Description:** Retrieve some summary information about the Cluster Configuration.

### HTTP Request 
`***GET*** /clusters` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a cluster.

**Description:** Update the Cluster with the given configuration.

### HTTP Request 
`***PUT*** /clusters` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to update cluster. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a cluster.

**Description:** Create a cluster with given network and cluster configuration.

### HTTP Request 
`***POST*** /clusters` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create cluster. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /CLUSTERS/AMQP-TARGET-CONFIG
## ***GET*** 

**Summary:** Get AMQP Target Config

**Description:** Fetch AMQP target config on the cluster.

### HTTP Request 
`***GET*** /clusters/amqp-target-config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update AMQP Target Config

**Description:** Updates AMQP target config on the cluster.

### HTTP Request 
`***PUT*** /clusters/amqp-target-config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to update cluster AMQP target config. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete AMQP Target Config

**Description:** Delete AMQP target config on the cluster.

### HTTP Request 
`***DELETE*** /clusters/amqp-target-config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /CONNECTION-BIFROST
## ***GET*** 

**Summary:** Get connections of Bifrost on the cluster.

**Description:** Get connections of Bifrost on the cluster.

### HTTP Request 
`***GET*** /connection-bifrost` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Specifies the id of the connections. | No | array |
| tenantId | query | Specifies the id of the tenant which the connection belongs to. | No | string |
| names | query | Specifies the name of the connections. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a connection of Bifrost on the cluster.

**Description:** Create a connection of Bifrost on the cluster.

### HTTP Request 
`***POST*** /connection-bifrost` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a connection. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /CONNECTION-BIFROST/{ID}
## ***GET*** 

**Summary:** Get a connection of Bifrost by the id.

**Description:** Get a connection of Bifrost by the id.

### HTTP Request 
`***GET*** /connection-bifrost/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Bifrost connection. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a connection of Bifrost.

**Description:** Update a connection of Bifrost.

### HTTP Request 
`***PUT*** /connection-bifrost/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of a Bifrost connection. | Yes | long |
| body | body | Specifies the parameters to update a connection. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a connection of Bifrost.

**Description:** Delete a connection of Bifrost.

### HTTP Request 
`***DELETE*** /connection-bifrost/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of a Bifrost connection. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /CONNECTION-RIGEL
## ***GET*** 

**Summary:** Get connections of Rigel on the cluster.

**Description:** Get connections of Rigel on the cluster.

### HTTP Request 
`***GET*** /connection-rigel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Specifies the id of the connections. | No | array |
| tenantId | query | Specifies the id of the tenant which the connection belongs to. | No | string |
| names | query | Specifies the name of the connection. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a connection of Rigel on the cluster.

**Description:** Create a connection of Rigel on the cluster.

### HTTP Request 
`***POST*** /connection-rigel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a connection. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /CONNECTION-RIGEL/{ID}
## ***GET*** 

**Summary:** Get a connection of Rigel by the id.

**Description:** Get a connection of Rigel by the id.

### HTTP Request 
`***GET*** /connection-rigel/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Rigel connection. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a connection of Rigel.

**Description:** Update a connection of Rigel.

### HTTP Request 
`***PUT*** /connection-rigel/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Rigel connection. | Yes | long |
| body | body | Specifies the parameters to update the connection. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a connection of Rigel.

**Description:** Delete a connection of Rigel.

### HTTP Request 
`***DELETE*** /connection-rigel/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Rigel connection. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /CONNECTOR-HYBRID-EXTENDER
## ***GET*** 

**Summary:** Get Bifrost connectors on the cluster.

**Description:** Get Bifrost connectors on the cluster.

### HTTP Request 
`***GET*** /connector-hybrid-extender` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Specifies the id of the connectors. | No | array |
| names | query | Specifies the name of the connectors. | No | array |
| tenantId | query | Specifies the id of the tenant which the connector belongs to. | No | string |
| connectionId | query | Specifies the Id of the connection which the connector belongs to. | No | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Bifrost connector on the cluster.

**Description:** Create a Bifrost connector on the cluster.

### HTTP Request 
`***POST*** /connector-hybrid-extender` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a connector. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /CONNECTOR-HYBRID-EXTENDER/{ID}
## ***GET*** 

**Summary:** Get a Bifrost connector by the id.

**Description:** Get a Bifrost connector by the id.

### HTTP Request 
`***GET*** /connector-hybrid-extender/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of connector. | Yes | long |
| tenantId | query | Specifies the id of the tenant which the connector belongs to. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Bifrost connector.

**Description:** Update a Bifrost connector.

### HTTP Request 
`***PUT*** /connector-hybrid-extender/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of connector. | Yes | long |
| body | body | Specifies the parameters to update a connector. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Bifrost connector.

**Description:** Delete a Bifrost connector.

### HTTP Request 
`***DELETE*** /connector-hybrid-extender/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of connector. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /CONNECTOR-RIGEL
## ***GET*** 

**Summary:** Get Rigel connectors on the cluster.

**Description:** Get Rigel connectors on the cluster.

### HTTP Request 
`***GET*** /connector-rigel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Specifies the id of the connector. | No | array |
| names | query | Specifies the name of the connectors. | No | array |
| tenantId | query | Specifies the id of the tenant which the connector belongs to. | No | string |
| connectionId | query | Specifies the Id of the connection which the connector belongs to. | No | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Rigel connector on the cluster.

**Description:** Create a Rigel connector on the cluster.

### HTTP Request 
`***POST*** /connector-rigel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a connector. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /CONNECTOR-RIGEL/{ID}
## ***GET*** 

**Summary:** Get a Rigel connector by the id.

**Description:** Get a Rigel connector by the id.

### HTTP Request 
`***GET*** /connector-rigel/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of connector. | Yes | long |
| tenantId | query | Specifies the id of the tenant which the connector belongs to. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Rigel connector.

**Description:** Update a Rigel connector.

### HTTP Request 
`***PUT*** /connector-rigel/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of connector. | Yes | long |
| body | body | Specifies the parameters to update a connector. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Rigel connector.

**Description:** Delete a Rigel connector.

### HTTP Request 
`***DELETE*** /connector-rigel/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of connector. | Yes | long |
| body | body | Specifies the parameters to delete a connector. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /CSR
## ***GET*** 

**Summary:** List Certificate Signing Requests on the cluster.

**Description:** List Certificate Signing Requests on the cluster with service name filtering.

### HTTP Request 
`***GET*** /csr` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| serviceName | query | Specifies the Cohesity service name for which the CSR is generated. If this is not specified, all the csrs on the cluster will be returned. | No | string |
| ids | query | Specifies the ids of the csrs. If this is not specified, all the csrs on the cluster will be returned. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Certificate Signing Request on the cluster.

**Description:** Create a Certificate Signing Request on the cluster with the given details. Each service has at most one outstanding CSR.

### HTTP Request 
`***POST*** /csr` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a Certificate Signing Request. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /CSR/CERTIFICATE
## ***POST*** 

**Summary:** Update the signed certificate on the cluster after a Certificate Signing Request is created.

**Description:** Update the signed certificate on the cluster after a Certificate Signing Request is created.

### HTTP Request 
`***POST*** /csr/certificate` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to update the certificate. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /CSR/{ID}
## ***GET*** 

**Summary:** List the specified Certificate Signing Request.

**Description:** List the specified Certificate Signing Request.

### HTTP Request 
`***GET*** /csr/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the csr. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Certificate Signing Request on the cluster.

**Description:** Delete a Certificate Signing Request on the cluster.

### HTTP Request 
`***DELETE*** /csr/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the csr to be deleted. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/POLLPLANNEDRUNS
## ***GET*** 

**Summary:** Get the list of failover planned runs.

**Description:** Poll to see whether planned run has been scheduled or not.

### HTTP Request 
`***GET*** /data-protect/failover/pollPlannedRuns` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| failoverIds | query | Get runs for specific failover workflows. | Yes | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Protection Groups which were created by all tenants which the current user has permission to see. If false, then only Protection Groups created by the current user will be returned. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/VIEWS/{ID}
## ***GET*** 

**Summary:** Get View Failover.

**Description:** Get failover tasks of a View.

### HTTP Request 
`***GET*** /data-protect/failover/views/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a view id to create an failover task. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create View Failover Task.

**Description:** Create a view failover task.

### HTTP Request 
`***POST*** /data-protect/failover/views/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a view id to create an failover task. | Yes | long |
| body | body | Specifies the request body to create failover task. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/VIEWS/{ID}/CANCEL
## ***POST*** 

**Summary:** Cancel View Failover Task.

**Description:** Cancel an in progress view failover task.

### HTTP Request 
`***POST*** /data-protect/failover/views/{id}/cancel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a view id to cancel it's failover. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/{ID}
## ***POST*** 

**Summary:** Initiate a failover request.

**Description:** Initiate a failover request.

### HTTP Request 
`***POST*** /data-protect/failover/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the failover workflow. | Yes | string |
| body | body | Specifies the parameters to initiate a failover. This failover request should be intiaited from replication cluster. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/{ID}/BACKUPACTIVATION
## ***POST*** 

**Summary:** Activate failover entity backup on replication clsuter.

**Description:** Specifies the configuration required for activating backup for failover objects on replication cluster. Here orchastrator can call this API multiple times as long as full set of object are non-overlapping. They can also use the existing job if its compatible to backup failover objects.

### HTTP Request 
`***POST*** /data-protect/failover/{id}/backupActivation` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the failover workflow. | Yes | string |
| body | body | Specifies the paramteres to activate the backup of failover entities. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/{ID}/BACKUPDEACTIVATION
## ***POST*** 

**Summary:** Deactivate failover entity backup on source clsuter.

**Description:** Specifies the configuration required for deactivating backup for failover entities on source cluster.

### HTTP Request 
`***POST*** /data-protect/failover/{id}/backupDeactivation` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the failover workflow. | Yes | string |
| body | body | Specifies the paramteres to deactivate the backup of failover entities. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/{ID}/CANCEL
## ***POST*** 

**Summary:** Cancel failover workflow.

**Description:** Specifies the request to cancel failover workflow. The cancellation request should not be made if '/backupActivation' or '/backupDeactivaetion' are already called on replication or source cluster respectively.

### HTTP Request 
`***POST*** /data-protect/failover/{id}/cancel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the failover workflow. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/{ID}/OBJECTLINKAGE
## ***POST*** 

**Summary:** Linking between replicated objects and failover objects

**Description:** Specifies the request to link failover objects on replication cluster to the replicated entity from source cluster. This linking need to be done after perforing recoveries for failed entities on replication cluster. This linkage will be useful when merging snapshots of object across replications and failovers.

### HTTP Request 
`***POST*** /data-protect/failover/{id}/objectLinkage` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the failover workflow. | Yes | string |
| body | body | Specifies the paramteres to create links between replicated objects and failover objects. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/FAILOVER/{ID}/PLANNEDRUN
## ***POST*** 

**Summary:** Create a planned run for backup and replication.

**Description:** Specifies the configuration required for executing a special run as a part of failover workflow. This special run is triggered during palnned failover to sync the source cluster to replication cluster with minimum possible delta.

### HTTP Request 
`***POST*** /data-protect/failover/{id}/plannedRun` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the failover workflow. | Yes | string |
| body | body | Specifies the paramteres to create a planned run while failover workflow. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/FILTER/OBJECTS
## ***POST*** 

**Summary:** List all the filtered objects.

**Description:** List all the filtered objects using given regular expressions and wildcard supported search strings. We are currenly supporting this for only SQL adapter.

### HTTP Request 
`***POST*** /data-protect/filter/objects` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to filter objects. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS
## ***GET*** 

**Summary:** Get Objects.

**Description:** Get Objects Configurations.

### HTTP Request 
`***GET*** /data-protect/objects` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Filter by a list of Object ids. | No | array |
| policyIds | query | Filter by Policy ids that are associated with Protected Objects. | No | array |
| parentId | query | Filter by Parent Id. Parent id is a unique object Id which may contain protected objects underneath in the source tree. | No | long |
| onlyProtectedObjects | query | If true, the response will include only objects which have been protected. | No | boolean |
| storageDomainId | query | Filter by Storage Domain id. Only Objects protected to this Storage Domain will be returned. | No | long |
| environments | query | Filter by environment types such as 'kVMware', 'kView', etc. Only Protected objects protecting the specified environment types are returned. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Objects which were protected by all tenants which the current user has permission to see. If false, then only objects protected by the current user will be returned. | No | boolean |
| includeLastRunInfo | query | If true, the response will include information about the last protection run on this object. | No | boolean |
| onlyAutoProtectedObjects | query | If true, the response will include only the auto protected objects. | No | boolean |
| onlyLeafObjects | query | If true, the response will include only the leaf level objects. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/LAST-RUN
## ***GET*** 

**Summary:** Get last protection run of objects.

**Description:** Get last protection run of objects.

### HTTP Request 
`***GET*** /data-protect/objects/last-run` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Specifies a list of object ids, only last runs for these objects will be returned. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Objects which belongs to all tenants which the current user has permission to see. | No | boolean |
| paginationCookie | query | Specifies the pagination cookie with which subsequent parts of the response can be fetched. | No | string |
| count | query | Specifies the number of objects to be fetched for the specified pagination cookie. | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/RUNS/CANCEL
## ***POST*** 

**Summary:** Cancel object runs.

**Description:** Cancel object runs for object based protection. This does not apply to Group based protection.

### HTTP Request 
`***POST*** /data-protect/objects/runs/cancel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to cancel object runs. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 207 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}
## ***GET*** 

**Summary:** Get an Object.

**Description:** Get Object configrations for given object id.

### HTTP Request 
`***GET*** /data-protect/objects/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Object. | Yes | long |
| onlyProtectedObjects | query | If true, the response will include only objects which have been protected. | No | boolean |
| storageDomainId | query | Filter by Storage Domain id. Only Objects protected to this Storage Domain will be returned. | No | long |
| environments | query | Filter by environment types such as 'kVMware', 'kView', etc. Only Protected objects protecting the specified environment types are returned. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Objects which were protected by all tenants which the current user has permission to see. If false, then only objects protected by the current user will be returned. | No | boolean |
| includeLastRunInfo | query | If true, the response will include information about the last protection run on this object. | No | boolean |
| onlyAutoProtectedObjects | query | If true, the response will include only the auto protected objects. | No | boolean |
| onlyLeafObjects | query | If true, the response will include only the leaf level objects. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}/ACTIONS
## ***POST*** 

**Summary:** Perform an action on an object.

**Description:** Perform an action on an object. Depending on the object environment type, different actions are available.

### HTTP Request 
`***POST*** /data-protect/objects/{id}/actions` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Object. | Yes | long |
| body | body | Specifies the parameters to perform an action on an object. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}/PIT-RANGES
## ***GET*** 

**Summary:** Get PIT ranges for an object

**Description:** Returns the time ranges within which the specified protected object can be restored to any Point in time.

### HTTP Request 
`***GET*** /data-protect/objects/{id}/pit-ranges` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the ID of the protected object. | Yes | long |
| fromTimeUsecs | query | If specified, return the time ranges that lie after this timestamp. This parameter is specified as the timestamp in Unix time epoch in microseconds. | No | long |
| toTimeUsecs | query | If specified, return the time ranges that lie before this timestamp. This parameter is specified as the timestamp in Unix time epoch in microseconds. | No | long |
| protectionGroupIds | query | If specified, return only the points in time corresponding to these protection group IDs. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}/RUNS
## ***GET*** 

**Summary:** Get the list of runs for an object.

**Description:** Get the runs for a particular object.

### HTTP Request 
`***GET*** /data-protect/objects/{id}/runs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the object. | Yes | long |
| runId | query | Specifies a unique id of the run. | No | string |
| startTimeUsecs | query | Filter by a start time when the run starts. Specify the start time as a Unix epoch Timestamp (in microseconds). | No | long |
| endTimeUsecs | query | Filter by a end time when the run starts. Specify the start time as a Unix epoch Timestamp (in microseconds). | No | long |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Protection Group Runs which were created by all tenants which the current user has permission to see. If false, then only Protection Group Runs created by the current user will be returned. | No | boolean |
| runTypes | query | Filter by run type. Only protection run matching the specified types will be returned. | No | array |
| localBackupObjectStatus | query | Specifies a list of status for the object in the backup run. | No | array |
| replicationObjectStatus | query | Specifies a list of status for the object in the replication run. | No | array |
| archivalObjectStatus | query | Specifies a list of status for the object in the archival run. | No | array |
| cloudSpinRunStatus | query | Specifies a list of status for the object in the cloud spin run. | No | array |
| numRuns | query | Specifies the max number of runs. If not specified, at most 100 runs will be returned. | No | long |
| paginationCookie | query | Specifies the pagination cookie with which subsequent parts of the response can be fetched. Users can use this to get next runs | No | string |
| excludeNonRestorableRuns | query | Specifies whether to exclude non restorable runs. Run is treated restorable only if there is atleast one object snapshot (which may be either a local or an archival snapshot) which is not deleted or expired. Default value is false. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}/RUNS/{RUNID}
## ***GET*** 

**Summary:** Get a run for an object.

**Description:** Get a run for an object.

### HTTP Request 
`***GET*** /data-protect/objects/{id}/runs/{runId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the object. | Yes | long |
| runId | path | Specifies the id of the run. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}/SNAPSHOTS
## ***GET*** 

**Summary:** List the snapshots for a given object.

**Description:** List the snapshots for a given object.

### HTTP Request 
`***GET*** /data-protect/objects/{id}/snapshots` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Object. | Yes | long |
| fromTimeUsecs | query | Specifies the timestamp in Unix time epoch in microseconds to filter Object's snapshots which are taken after this value. | No | long |
| toTimeUsecs | query | Specifies the timestamp in Unix time epoch in microseconds to filter Object's snapshots which are taken before this value. | No | long |
| runTypes | query | Filter by run type. Only protection run matching the specified types will be returned. By default, CDP hydration snapshots are not included, unless explicitly queried using this field. | No | array |
| protectionGroupIds | query | If specified, this returns only the snapshots of the specified object ID, which belong to the provided protection group IDs. | No | array |
| runInstanceIds | query | Filter by a list run instance ids. If specified, only snapshots created by these protection runs will be returned. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}/SNAPSHOTS/{SNAPSHOTID}
## ***PUT*** 

**Summary:** Update an object snapshot.

**Description:** Update an object snapshot.

### HTTP Request 
`***PUT*** /data-protect/objects/{id}/snapshots/{snapshotId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Object. | Yes | long |
| snapshotId | path | Specifies the id of the snapshot.<br> Note: 1. If the snapshotid of one of the apps is specified, it applies for all the databases in the Protection Run.<br> 2. In case of volume based jobs, please specify the snapshotid of the source not the database. if source snapshot is specified, applied to source snapshot. if database snapshotid is specified in case of volume based jobs, then it is applicable for host's snapshot. | Yes | string |
| body | body | Specifies the parameters update an object snapshot. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}/STATS
## ***GET*** 

**Summary:** Get stats for a given object.

**Description:** Get stats for a given object.

### HTTP Request 
`***GET*** /data-protect/objects/{id}/stats` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Object. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{ID}/TREE
## ***GET*** 

**Summary:** Get the objects tree hierarchy for for an Object.

**Description:** Get the objects tree hierarchy for for an Object. If the object does not have a hierarchy then a single object will be returned.

### HTTP Request 
`***GET*** /data-protect/objects/{id}/tree` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Object. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{OBJECTID}/INDEXED-OBJECTS/SNAPSHOTS
## ***GET*** 

**Summary:** Get snapshots of indexed object.

**Description:** Get snapshots of indexed object.

### HTTP Request 
`***GET*** /data-protect/objects/{objectId}/indexed-objects/snapshots` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| objectId | path | Specifies the object id. | Yes | long |
| indexedObjectName | query | Specifies the indexed object name. | Yes | string |
| protectionGroupId | query | Specifies the protection group id. | No | string |
| includeIndexedSnapshotsOnly | query | Specifies whether to only return snapshots which are indexed. In an indexed snapshot files are guaranteed to exist, while in a non-indexed snapshot files may not exist. | No | boolean |
| fromTimeUsecs | query | Specifies the timestamp in Unix time epoch in microseconds to filter indexed object's snapshots which are taken after this value. | No | long |
| toTimeUsecs | query | Specifies the timestamp in Unix time epoch in microseconds to filter indexed object's snapshots which are taken before this value. | No | long |
| runTypes | query | Filter by run type. Only protection run matching the specified types will be returned. By default, CDP hydration snapshots are not included, unless explicitly queried using this field. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/OBJECTS/{OBJECTID}/PROTECTION-GROUPS/{PROTECTIONGROUPID}/INDEXED-OBJECTS/SNAPSHOTS
## ***GET*** 

**Summary:** Get snapshots of indexed object.

**Description:** Get snapshots of indexed object.

### HTTP Request 
`***GET*** /data-protect/objects/{objectId}/protection-groups/{protectionGroupId}/indexed-objects/snapshots` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| protectionGroupId | path | Specifies the protection group id. | Yes | string |
| objectId | path | Specifies the object id. | Yes | long |
| indexedObjectName | query | Specifies the indexed object name. | Yes | string |
| includeIndexedSnapshotsOnly | query | Specifies whether to only return snapshots which are indexed. In an indexed snapshots file are guaranteened to exist, while in a non-indexed snapshots file may not exist. | No | boolean |
| fromTimeUsecs | query | Specifies the timestamp in Unix time epoch in microseconds to filter indexed object's snapshots which are taken after this value. | No | long |
| toTimeUsecs | query | Specifies the timestamp in Unix time epoch in microseconds to filter indexed object's snapshots which are taken before this value. | No | long |
| runTypes | query | Filter by run type. Only protection run matching the specified types will be returned. By default, CDP hydration snapshots are not included, unless explicitly queried using this field. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/POLICIES
## ***GET*** 

**Summary:** List Protection Policies based on provided filtering parameters.

**Description:** Lists protection policies based on filtering query parameters.

### HTTP Request 
`***GET*** /data-protect/policies` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Filter policies by a list of policy ids. | No | array |
| policyNames | query | Filter policies by a list of policy names. | No | array |
| tenantIds | query | TenantIds contains ids of the organizations for which objects are to be returned. | No | array |
| includeTenants | query | IncludeTenantPolicies specifies if objects of all the organizations under the hierarchy of the logged in user's organization should be returned. | No | boolean |
| types | query | Types specifies the policy type of policies to be returned | No | array |
| excludeLinkedPolicies | query | If excludeLinkedPolicies is set to true then only local policies created on cluster will be returned. The result will exclude all linked policies created from policy templates. | No | boolean |
| includeReplicatedPolicies | query | If includeReplicatedPolicies is set to true, then response will also contain replicated policies. By default, replication policies are not included in the response. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Protection Policy.

**Description:** Create the Protection Policy and returns the newly created policy object.

### HTTP Request 
`***POST*** /data-protect/policies` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Request to create a Protection Policy. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/POLICIES/{ID}
## ***GET*** 

**Summary:** List details about a single Protection Policy.

**Description:** Returns the Protection Policy details based on provided Policy Id.

### HTTP Request 
`***GET*** /data-protect/policies/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Policy to return. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Protection Policy.

**Description:** Specifies the request to update the existing Protection Policy. On successful update, returns the updated policy object.

### HTTP Request 
`***PUT*** /data-protect/policies/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Policy to update. | Yes | string |
| body | body | Request to update a Protection Policy. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Protection Policy.

**Description:** Deletes a Protection Policy based on given policy id.

### HTTP Request 
`***DELETE*** /data-protect/policies/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Policy to delete. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-PROTECT/POLICY-TEMPLATES
## ***GET*** 

**Summary:** List Policy Templates filtered by query parameters.

**Description:** Returns the policy templates based on the filtering parameters. If no parameters are specified, then all the policy templates are returned.

### HTTP Request 
`***GET*** /data-protect/policy-templates` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Filter policies by a list of policy template ids. | No | array |
| policyNames | query | Filter policies by a list of policy names. | No | array |
| tenantIds | query | TenantIds contains ids of the organizations for which objects are to be returned. | No | array |
| includeTenants | query | IncludeTenantPolicies specifies if objects of all the organizations under the hierarchy of the logged in user's organization should be returned. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/POLICY-TEMPLATES/{ID}
## ***GET*** 

**Summary:** List details about a single Policy Template.

**Description:** Returns the Policy Template corresponding to the specified Policy Id.

### HTTP Request 
`***GET*** /data-protect/policy-templates/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Policy Template to return. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/PROTECTED-OBJECTS
## ***POST*** 

**Summary:** Create Object Backup.

**Description:** Create Protect Objects Backup.

### HTTP Request 
`***POST*** /data-protect/protected-objects` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to protect objects. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 207 |  |
| default |  |

# /DATA-PROTECT/PROTECTED-OBJECTS/ACTIONS
## ***POST*** 

**Summary:** Perform Actions on Protect Objects.

**Description:** Perform actions on Protected Objects.

### HTTP Request 
`***POST*** /data-protect/protected-objects/actions` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to perform an action on an already protected object. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 |  |
| default |  |

# /DATA-PROTECT/PROTECTED-OBJECTS/{ID}
## ***PUT*** 

**Summary:** Update Object Backup.

**Description:** Update Protected object backup configuration given a object id.

### HTTP Request 
`***PUT*** /data-protect/protected-objects/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Protected Object. | Yes | long |
| body | body | Specifies the parameters to perform an update on protected objects. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS
## ***GET*** 

**Summary:** Get the list of Protection Groups.

**Description:** Get the list of Protection Groups.

### HTTP Request 
`***GET*** /data-protect/protection-groups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Filter by a list of Protection Group ids. | No | array |
| names | query | Filter by a list of Protection Group names. | No | array |
| policyIds | query | Filter by Policy ids that are associated with Protection Groups. Only Protection Groups associated with the specified Policy ids, are returned. | No | array |
| storageDomainId | query | Filter by Storage Domain id. Only Protection Groups writing data to this Storage Domain will be returned. | No | long |
| includeGroupsWithDatalockOnly | query | Whether to only return Protection Groups with a datalock. | No | boolean |
| environments | query | Filter by environment types such as 'kVMware', 'kView', etc. Only Protection Groups protecting the specified environment types are returned. | No | array |
| isActive | query | Filter by Inactive or Active Protection Groups. If not set, all Inactive and Active Protection Groups are returned. If true, only Active Protection Groups are returned. If false, only Inactive Protection Groups are returned. When you create a Protection Group on a Primary Cluster with a replication schedule, the Cluster creates an Inactive copy of the Protection Group on the Remote Cluster. In addition, when an Active and running Protection Group is deactivated, the Protection Group becomes Inactive. | No | boolean |
| isDeleted | query | If true, return only Protection Groups that have been deleted but still have Snapshots associated with them. If false, return all Protection Groups except those Protection Groups that have been deleted and still have Snapshots associated with them. A Protection Group that is deleted with all its Snapshots is not returned for either of these cases. | No | boolean |
| isPaused | query | Filter by paused or non paused Protection Groups, If not set, all paused and non paused Protection Groups are returned. If true, only paused Protection Groups are returned. If false, only non paused Protection Groups are returned. | No | boolean |
| lastRunLocalBackupStatus | query | Filter by last local backup run status.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |
| lastRunReplicationStatus | query | Filter by last remote replication run status.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |
| lastRunArchivalStatus | query | Filter by last cloud archival run status.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |
| lastRunCloudSpinStatus | query | Filter by last cloud spin run status.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |
| isLastRunSlaViolated | query | If true, return Protection Groups for which last run SLA was violated. | No | boolean |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Protection Groups which were created by all tenants which the current user has permission to see. If false, then only Protection Groups created by the current user will be returned. | No | boolean |
| includeLastRunInfo | query | If true, the response will include last run info. If it is false or not specified, the last run info won't be returned. | No | boolean |
| pruneExcludedSourceIds | query | If true, the response will not include the list of excluded source IDs in groups that contain this field. This can be set to true in order to improve performance if excluded source IDs are not needed by the user. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Protection Group.

**Description:** Create a Protection Group.

### HTTP Request 
`***POST*** /data-protect/protection-groups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a Protection Group. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS/STATES
## ***POST*** 

**Summary:** Perform an action like pause, resume, active, deactivate on all specified Protection Groups.

**Description:** Perform an action like pause, resume, active, deactivate on all specified Protection Groups. Note that the pause or resume actions will take effect from next Protection Run. Also, user can specify only one type of action on all the Protection Groups. Deactivate and activate actions are independent of pause and resume state. Deactivate and activate actions are useful in case of failover situations. Returns success if the state of all the Protection Groups state is changed successfully.

### HTTP Request 
`***POST*** /data-protect/protection-groups/states` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to perform an action of list of Protection Groups. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS/{ID}
## ***GET*** 

**Summary:** List details about single Protection Group.

**Description:** Returns the Protection Group corresponding to the specified Group id.

### HTTP Request 
`***GET*** /data-protect/protection-groups/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| includeLastRunInfo | query | If true, the response will include last run info. If it is false or not specified, the last run info won't be returned. | No | boolean |
| pruneExcludedSourceIds | query | If true, the response will not include the list of excluded source IDs in groups that contain this field. This can be set to true in order to improve performance if excluded source IDs are not needed by the user. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Protection Group.

**Description:** Update the specified Protection Group.

### HTTP Request 
`***PUT*** /data-protect/protection-groups/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Protection Group. | Yes | string |
| body | body | Specifies the parameters to update a Protection Group. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Protection Group.

**Description:** Returns Success if the Protection Group is deleted.

### HTTP Request 
`***DELETE*** /data-protect/protection-groups/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| deleteSnapshots | query | Specifies if Snapshots generated by the Protection Group should also be deleted when the Protection Group is deleted. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS/{ID}/RUNS
## ***GET*** 

**Summary:** Get the list of runs for a Protection Group.

**Description:** Get the runs for a particular Protection Group.

### HTTP Request 
`***GET*** /data-protect/protection-groups/{id}/runs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| runId | query | Specifies the protection run id. | No | string |
| startTimeUsecs | query | Filter by a start time. Specify the start time as a Unix epoch Timestamp (in microseconds). | No | long |
| endTimeUsecs | query | Filter by a end time. Specify the start time as a Unix epoch Timestamp (in microseconds). | No | long |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Protection Group Runs which were created by all tenants which the current user has permission to see. If false, then only Protection Group Runs created by the current user will be returned. | No | boolean |
| runTypes | query | Filter by run type. Only protection run matching the specified types will be returned. | No | array |
| includeObjectDetails | query | Specifies if the result includes the object details for each protection run. If set to true, details of the protected object will be returned. If set to false or not specified, details will not be returned. | No | boolean |
| localBackupRunStatus | query | Specifies a list of local backup status, runs matching the status will be returned.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |
| replicationRunStatus | query | Specifies a list of replication status, runs matching the status will be returned.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |
| archivalRunStatus | query | Specifies a list of archival status, runs matching the status will be returned.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |
| cloudSpinRunStatus | query | Specifies a list of cloud spin status, runs matching the status will be returned.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |
| numRuns | query | Specifies the max number of runs. If not specified, at most 100 runs will be returned. | No | long |
| excludeNonRestorableRuns | query | Specifies whether to exclude non restorable runs. Run is treated restorable only if there is atleast one object snapshot (which may be either a local or an archival snapshot) which is not deleted or expired. Default value is false. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update runs for a particular Protection Group.

**Description:** Update runs for a particular Protection Group. A user can perform the following actions: 1. Extend or reduce retention of a local, replication and archival snapshots. 2. Can perform resync operation on failed copy snapshots attempts in this Run. 3. Add new replication and archival snapshot targets to the Run. 4. Add or remove legal hold on the snapshots. Only a user with DSO role can perform this operation. 5. Delete the snapshots that were created as a part of this Run. 6. Apply datalock on existing snapshots where a user cannot manually delete snapshots before the expiry time. 

### HTTP Request 
`***PUT*** /data-protect/protection-groups/{id}/runs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| body | body | Specifies the parameters to update a Protection Group Run. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 207 |  |
| default |  |

## ***POST*** 

**Summary:** Create a new protection run.

**Description:** Create a new protection run. This can be used to start a run for a Protection Group on demand, ignoring the schedule and retention specified in the protection policy.

### HTTP Request 
`***POST*** /data-protect/protection-groups/{id}/runs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| body | body | Specifies the parameters to start a protection run. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 |  |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS/{ID}/RUNS/{RUNID}
## ***GET*** 

**Summary:** Get a run for a Protection Group.

**Description:** Get a run for a particular Protection Group.

### HTTP Request 
`***GET*** /data-protect/protection-groups/{id}/runs/{runId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| runId | path | Specifies a unique run id of the Protection Group run. | Yes | string |
| tenantIds | query | TenantIds contains ids of the tenants for which the run is to be returned. | No | array |
| includeTenants | query | If true, the response will include Protection Group Runs which were created by all tenants which the current user has permission to see. If false, then only Protection Groups created by the current user will be returned. If it's not specified, it is true by default. | No | boolean |
| includeObjectDetails | query | Specifies if the result includes the object details for a protection run. If set to true, details of the protected object will be returned. If set to false or not specified, details will not be returned. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS/{ID}/RUNS/{RUNID}/CANCEL
## ***POST*** 

**Summary:** Cancel protection group run.

**Description:** Cancel protection run for a given protection group ID and run ID.

### HTTP Request 
`***POST*** /data-protect/protection-groups/{id}/runs/{runId}/cancel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| runId | path | Specifies a unique run id of the Protection Group run. | Yes | string |
| body | body | Specifies the parameters to cancel a protection run. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS/{ID}/RUNS/{RUNID}/DEBUG-LOGS
## ***GET*** 

**Summary:** Get the debug logs for a run from a Protection Group.

**Description:** Get the debug logs for all objects of a run for a particular Protection Group.

### HTTP Request 
`***GET*** /data-protect/protection-groups/{id}/runs/{runId}/debug-logs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| runId | path | Specifies a unique run id of the Protection Group run. | Yes | string |
| objectId | query | Specifies the id of the object for which debug logs are to be returned.  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS/{ID}/RUNS/{RUNID}/OBJECTS/{OBJECTID}/DEBUG-LOGS
## ***GET*** 

**Summary:** Get the debug logs for a particular object in a run from a Protection Group.

**Description:** Get the debug logs for a particular object of a run for a particular Protection Group.

### HTTP Request 
`***GET*** /data-protect/protection-groups/{id}/runs/{runId}/objects/{objectId}/debug-logs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| runId | path | Specifies a unique run id of the Protection Group run. | Yes | string |
| objectId | path | Specifies the id of the object for which debug logs are to be returned.  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/PROTECTION-GROUPS/{ID}/RUNS/{RUNID}/OBJECTS/{OBJECTID}/DOWNLOADMESSAGES
## ***GET*** 

**Summary:** Get the CSV of errors/warnings for a given run and an object.

**Description:** Get an CSV error report for given objectId and run id. Each row in CSV report contains the File Path, error/warning code and error/warning message.

### HTTP Request 
`***GET*** /data-protect/protection-groups/{id}/runs/{runId}/objects/{objectId}/downloadMessages` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the Protection Group. | Yes | string |
| runId | path | Specifies a unique run id of the Protection Group run. | Yes | string |
| objectId | path | Specifies the id of the object for which errors/warnings are to be returned.  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |
| default |  |

# /DATA-PROTECT/RECOVERIES
## ***GET*** 

**Summary:** Lists the Recoveries.

**Description:** Lists the Recoveries.

### HTTP Request 
`***GET*** /data-protect/recoveries` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Filter Recoveries for given ids. | No | array |
| returnOnlyChildRecoveries | query | Returns only child recoveries if passed as true. This filter should always be used along with 'ids' filter.  | No | boolean |
| tenantIds | query | TenantIds contains ids of the organizations for which recoveries are to be returned. | No | array |
| includeTenants | query | Specifies if objects of all the organizations under the hierarchy of the logged in user's organization should be returned. | No | boolean |
| startTimeUsecs | query | Returns the recoveries which are started after the specific time. This value should be in Unix timestamp epoch in microseconds. | No | long |
| endTimeUsecs | query | Returns the recoveries which are started before the specific time. This value should be in Unix timestamp epoch in microseconds. | No | long |
| storageDomainId | query | Filter by Storage Domain id. Only recoveries writing data to this Storage Domain will be returned. | No | long |
| snapshotTargetType | query | Specifies the snapshot's target type from which recovery has been performed. | No | array |
| archivalTargetType | query | Specifies the snapshot's archival target type from which recovery has been performed. This parameter applies only if 'snapshotTargetType' is 'Archival'. | No | array |
| snapshotEnvironments | query | Specifies the list of snapshot environment types to filter Recoveries. If empty, Recoveries related to all environments will be returned. | No | array |
| status | query | Specifies the list of run status to filter Recoveries. If empty, Recoveries with all run status will be returned. | No | array |
| recoveryActions | query | Specifies the list of recovery actions to filter Recoveries. If empty, Recoveries related to all actions will be returned. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Performs a Recovery.

**Description:** Performs a Recovery.

### HTTP Request 
`***POST*** /data-protect/recoveries` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a Recovery. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/RECOVERIES/DOWNLOADFILESANDFOLDERSRECOVERY
## ***POST*** 

**Summary:** Create a download files and folders recovery.

**Description:** Creates a download files and folders recovery.

### HTTP Request 
`***POST*** /data-protect/recoveries/downloadFilesAndFoldersRecovery` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a download files and folder recovery. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/RECOVERIES/{ID}
## ***GET*** 

**Summary:** Get Recovery for a given id.

**Description:** Get Recovery for a given id.

### HTTP Request 
`***GET*** /data-protect/recoveries/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of a Recovery. | Yes | string |
| includeTenants | query | Specifies if objects of all the organizations under the hierarchy of the logged in user's organization should be returned. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/RECOVERIES/{ID}/CANCEL
## ***POST*** 

**Summary:** Cancel Recovery for a given id.

**Description:** Cancel Recovery for a given id.

### HTTP Request 
`***POST*** /data-protect/recoveries/{id}/cancel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of a Recovery. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-PROTECT/RECOVERIES/{ID}/DEBUG-LOGS
## ***GET*** 

**Summary:** Get the debug logs for a particular recovery operation.

**Description:** Get the debug logs for a particular recovery operation.

### HTTP Request 
`***GET*** /data-protect/recoveries/{id}/debug-logs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of a Recovery job. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/RECOVERIES/{ID}/DOWNLOADFILES
## ***GET*** 

**Summary:** Download files from the given download file recovery.

**Description:** Download files from the given download file recovery.

### HTTP Request 
`***GET*** /data-protect/recoveries/{id}/downloadFiles` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of a Recovery. | Yes | string |
| startOffset | query | Specifies the start offset of file chunk to be downloaded. | No | long |
| length | query | Specifies the length of bytes to download. This can not be greater than 8MB (8388608 byets) | No | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/RECOVERIES/{ID}/TEARDOWN
## ***POST*** 

**Summary:** Tear down Recovery for a given id.

**Description:** Tear down Recovery for a given id.

### HTTP Request 
`***POST*** /data-protect/recoveries/{id}/tearDown` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of a Recovery. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-PROTECT/RUNS/SUMMARY
## ***GET*** 

**Summary:** Get the list of runs.

**Description:** Get a list of protection runs.

### HTTP Request 
`***GET*** /data-protect/runs/summary` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| startTimeUsecs | query | Filter by a start time. Specify the start time as a Unix epoch Timestamp (in microseconds), only runs executing after this time will be returned. By default it is endTimeUsecs minus an hour. | No | long |
| endTimeUsecs | query | Filter by a end time. Specify the start time as a Unix epoch Timestamp (in microseconds), only runs executing before this time will be returned. By default it is current time. | No | long |
| runStatus | query | Specifies a list of status, runs matching the status will be returned.<br> 'Running' indicates that the run is still running.<br> 'Canceled' indicates that the run has been canceled.<br> 'Canceling' indicates that the run is in the process of being canceled.<br> 'Failed' indicates that the run has failed.<br> 'Missed' indicates that the run was unable to take place at the scheduled time because the previous run was still happening.<br> 'Succeeded' indicates that the run has finished successfully.<br> 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/RUNS/{RUNID}/PROGRESS
## ***GET*** 

**Summary:** Get the progress of a run.

**Description:** Get the progress of a run.

### HTTP Request 
`***GET*** /data-protect/runs/{runId}/progress` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| runId | path | Specifies a unique run id of the Protection Run. | Yes | string |
| tenantIds | query | TenantIds contains ids of the tenants for which the run is to be returned. | No | array |
| includeTenants | query | If true, the response will include Protection Group Runs which were created by all tenants which the current user has permission to see. If false, then only Protection Groups created by the current user will be returned. If it's not specified, it is true by default. | No | boolean |
| includeFinishedTasks | query | Specifies whether to return finished tasks. By default only active tasks are returned. | No | boolean |
| startTimeUsecs | query | Specifies the time after which the progress task starts in Unix epoch Timestamp(in microseconds). | No | long |
| endTimeUsecs | query | Specifies the time before which the progress task ends in Unix epoch Timestamp(in microseconds). | No | long |
| maxTasksNum | query | Specifies the maximum number of tasks to return. | No | integer |
| excludeObjectDetails | query | Specifies whether to return objects. By default all the task tree are returned. | No | boolean |
| includeEventLogs | query | Specifies whether to include event logs | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SEARCH/INDEXED-OBJECTS
## ***POST*** 

**Summary:** List indexed objects.

**Description:** List all the indexed objects like files and folders, emails, mailboxes etc., that match the specified search and filter criteria from protected objects.

### HTTP Request 
`***POST*** /data-protect/search/indexed-objects` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to search for indexed objects. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SEARCH/OBJECTS
## ***GET*** 

**Summary:** List Objects.

**Description:** List objects.

### HTTP Request 
`***GET*** /data-protect/search/objects` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| searchString | query | Specifies the search string to filter the objects. This search string will be applicable for objectnames. User can specify a wildcard character '*' as a suffix to a string where all object names are matched with the prefix string. For example, if vm1 and vm2 are the names of objects, user can specify vm* to list the objects. If not specified, then all the objects will be returned which will match other filtering criteria. | No | string |
| environments | query | Specifies the environment type to filter objects. | No | array |
| protectionTypes | query | Specifies the protection type to filter objects. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Objects which belongs to all tenants which the current user has permission to see. | No | boolean |
| protectionGroupIds | query | Specifies a list of Protection Group ids to filter the objects. If specified, the objects protected by specified Protection Group ids will be returned. | No | array |
| objectIds | query | Specifies a list of Object ids to filter. | No | array |
| osTypes | query | Specifies the operating system types to filter objects on. | No | array |
| sourceIds | query | Specifies a list of Protection Source object ids to filter the objects. If specified, the object which are present in those Sources will be returned. | No | array |
| sourceUuids | query | Specifies a list of Protection Source object uuids to filter the objects. If specified, the object which are present in those Sources will be returned. | No | array |
| isProtected | query | Specifies the protection status of objects. If set to true, only protected objects will be returned. If set to false, only unprotected objects will be returned. If not specified, all objects will be returned. | No | boolean |
| lastRunStatusList | query | Specifies a list of status of the object's last protection run. Only objects with last run status of these will be returned. | No | array |
| regionIds | query | Specifies a list of region ids. Only records from clusters having these region ids will be returned. | No | array |
| clusterIdentifiers | query | Specifies the list of cluster identifiers. Format is clusterId:clusterIncarnationId. Only records from clusters having these identifiers will be returned. | No | array |
| paginationCookie | query | Specifies the pagination cookie with which subsequent parts of the response can be fetched. | No | string |
| count | query | Specifies the number of objects to be fetched for the specified pagination cookie. | No | integer |
| mustHaveTagIds | query | Specifies tags which must be all present in the document. | No | array |
| mightHaveTagIds | query | Specifies list of tags, one or more of which might be present in the document. These are OR'ed together and the resulting criteria AND'ed with the rest of the query. | No | array |
| mustHaveSnapshotTagIds | query | Specifies snapshot tags which must be all present in the document. | No | array |
| mightHaveSnapshotTagIds | query | Specifies list of snapshot tags, one or more of which might be present in the document. These are OR'ed together and the resulting criteria AND'ed with the rest of the query. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SEARCH/PROTECTED-OBJECTS
## ***GET*** 

**Summary:** List Protected Objects.

**Description:** List protected objects and corresponding detail information from registered sources filtered by specified query parameters. If no search pattern or filter parameters are specified, all protected objects currently found are returned.

### HTTP Request 
`***GET*** /data-protect/search/protected-objects` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| searchString | query | Specifies the search string to filter the objects. This search string will be applicable for objectnames and Protection Group names. User can specify a wildcard character '*' as a suffix to a string where all object and their Protection Group names are matched with the prefix string. For example, if vm1 and vm2 are the names of objects, user can specify vm* to list the objects. If not specified, then all the objects with Protection Groups will be returned which will match other filtering criteria. | No | string |
| environments | query | Specifies the environment type to filter objects. | No | array |
| snapshotActions | query | Specifies a list of recovery actions. Only snapshots that applies to these actions will be returned. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Objects which belongs to all tenants which the current user has permission to see. | No | boolean |
| protectionGroupIds | query | Specifies a list of Protection Group ids to filter the objects. If specified, the objects protected by specified Protection Group ids will be returned. | No | array |
| objectIds | query | Specifies a list of Object ids to filter. | No | array |
| storageDomainIds | query | Specifies the Storage Domain ids to filter objects for which Protection Groups are writing data to Cohesity Views on the specified Storage Domains. | No | array |
| subResultSize | query | Specifies the size of objects to be fetched for a single subresult. | No | integer |
| filterSnapshotFromUsecs | query | Specifies the timestamp in Unix time epoch in microseconds to filter the objects if the Object has a successful snapshot after this value. | No | long |
| filterSnapshotToUsecs | query | Specifies the timestamp in Unix time epoch in microseconds to filter the objects if the Object has a successful snapshot before this value. | No | long |
| osTypes | query | Specifies the operating system types to filter objects on. | No | array |
| sourceIds | query | Specifies a list of Protection Source object ids to filter the objects. If specified, the object which are present in those Sources will be returned. | No | array |
| runInstanceIds | query | Specifies a list of run instance ids. If specified only objects belonging to the provided run id will be retunrned. | No | array |
| cdpProtectedOnly | query | Specifies whether to only return the CDP protected objects. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SNAPSHOTS/{SNAPSHOTID}
## ***GET*** 

**Summary:** Get details of object snapshot.

**Description:** Get details of object snapshot.

### HTTP Request 
`***GET*** /data-protect/snapshots/{snapshotId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| snapshotId | path | Specifies the snapshot id. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SNAPSHOTS/{SNAPSHOTID}/METAINFO
## ***POST*** 

**Summary:** Construct meta info for any workflow from object snapshot and some other information.

**Description:** Construct meta info from object snapshot and some additional params.

### HTTP Request 
`***POST*** /data-protect/snapshots/{snapshotId}/metaInfo` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| snapshotId | path | Specifies the snapshot id. | Yes | string |
| body | body | Specifies the parameters to construct meta info for desired workflow. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SNAPSHOTS/{SNAPSHOTID}/VOLUME
## ***GET*** 

**Summary:** Get volume info of object snapshot.

**Description:** Get volume info of object snapshot.

### HTTP Request 
`***GET*** /data-protect/snapshots/{snapshotId}/volume` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| snapshotId | path | Specifies the snapshot id. | Yes | string |
| includeSupportedOnly | query | Specifies whether to only return supported volumes. | No | boolean |
| pointInTimeUsecs | query | Specifies the point-in-time timestamp (in usecs from epoch) between snapshots for which the volume info is to be returned. | No | number (int64) |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SNAPSHOTS/{SNAPSHOTSID}/DOWNLOADFILE
## ***GET*** 

**Summary:** Download an indexed file.

**Description:** Download an indexed file from a snapshot.

### HTTP Request 
`***GET*** /data-protect/snapshots/{snapshotsId}/downloadFile` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| snapshotsId | path | Specifies the snapshot id to download from. | Yes | string |
| filePath | query | Specifies the path to the file to download. If no path is specified and snapshot environment is kVMWare, VMX file for VMware will be downloaded. For other snapshot environments, this field must be specified. | No | string |
| retryAttempt | query | Specifies the number of attempts the protection run took to create this file. | No | long |
| startOffset | query | Specifies the start offset of file chunk to be downloaded. | No | long |
| length | query | Specifies the length of bytes to download. This can not be greater than 8MB (8388608 byets) | No | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SOURCES
## ***GET*** 

**Summary:** Get a List of Protection Sources.

**Description:** Get a List of Protection Sources.

### HTTP Request 
`***GET*** /data-protect/sources` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| tenantIds | query | TenantIds contains ids of the tenants for which Sources are to be returned. | No | array |
| includeTenants | query | If true, the response will include Sources which belong belong to all tenants which the current user has permission to see. If false, then only Sources for the current user will be returned. | No | boolean |
| includeSourceCredentials | query | If true, the encrypted crednetial for the registered sources will be included. Credential is first encrypted with internal key and then reencrypted with user supplied encryption key. | No | boolean |
| encryptionKey | query | Specifies the key to be used to encrypt the source credential. If includeSourceCredentials is set to true this key must be specified. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SOURCES/FILTERS
## ***GET*** 

**Summary:** List attribute filters for a source.

**Description:** Get a List of attribute filters for leaf entities within a a source

### HTTP Request 
`***GET*** /data-protect/sources/filters` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| sourceUuid | query | Specifies the source UUID of the parent entity. | Yes | string |
| environment | query | Specifies the environment type of the Protection Source. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SOURCES/REGISTRATIONS
## ***GET*** 

**Summary:** Get the list of Protection Source registrations.

**Description:** Get the list of Protection Source registrations.

### HTTP Request 
`***GET*** /data-protect/sources/registrations` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Ids specifies the list of source registration ids to return. If left empty, every source registration will be returned by default. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Registrations which were created by all tenants which the current user has permission to see. If false, then only Registrations created by the current user will be returned. | No | boolean |
| includeSourceCredentials | query | If true, the encrypted crednetial for the registered sources will be included. Credential is first encrypted with internal key and then reencrypted with user supplied encryption key. | No | boolean |
| encryptionKey | query | Specifies the key to be used to encrypt the source credential. If includeSourceCredentials is set to true this key must be specified. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Register a Protection Source.

**Description:** Register a Protection Source.

### HTTP Request 
`***POST*** /data-protect/sources/registrations` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to register a Protection Source. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-PROTECT/SOURCES/REGISTRATIONS/{ID}
## ***GET*** 

**Summary:** Get a Protection Source registration.

**Description:** Get a Protection Source registration.

### HTTP Request 
`***GET*** /data-protect/sources/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Protection Source registration. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update Protection Source registration.

**Description:** Update Protection Source registration.

### HTTP Request 
`***PUT*** /data-protect/sources/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Protection Source registration. | Yes | long |
| body | body | Specifies the parameters to update the registration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete Protection Source Registration.

**Description:** Delete Protection Source Registration.

### HTTP Request 
`***DELETE*** /data-protect/sources/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the ID of the Protection Source Registration. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-PROTECT/SOURCES/TEST-CONNECTION
## ***POST*** 

**Summary:** Test connection to a source.

**Description:** Test connection to a source.

### HTTP Request 
`***POST*** /data-protect/sources/test-connection` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to test connectivity with a source. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SOURCES/VIRTUAL-DATACENTER/{ID}
## ***GET*** 

**Summary:** Get VDC Details.

**Description:** Get the details such as catelogs, Org networks associated with a VMware virtual datacenter (VDC).

### HTTP Request 
`***GET*** /data-protect/sources/virtual-datacenter/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the ID of the VMware virtual datacenter. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SOURCES/{ID}
## ***GET*** 

**Summary:** Get a Protection Sources.

**Description:** Get a Protection Source.

### HTTP Request 
`***GET*** /data-protect/sources/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the Protection Source. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-PROTECT/SOURCES/{SOURCEID}/OBJECTS
## ***GET*** 

**Summary:** List objects on a source which can be used for data protection.

**Description:** List objects which can be used for data protection.

### HTTP Request 
`***GET*** /data-protect/sources/{sourceId}/objects` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| sourceId | path | Specifies the source ID for which objects should be returned. | Yes | long |
| parentId | query | Specifies the parent ID under which objects should be returned. | No | long |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Objects which belongs to all tenants which the current user has permission to see. | No | boolean |
| vmwareObjectTypes | query | Specifies the VMware object types to filter objects. | No | array |
| netappObjectTypes | query | Specifies the Netapp object types to filter objects. | No | array |
| o365ObjectTypes | query | Specifies the Office 365 object types to filter objects. | No | array |
| cassandraObjectTypes | query | Specifies the Cassandra object types to filter objects. | No | array |
| mongodbObjectTypes | query | Specifies the Mongo DB object types to filter objects. | No | array |
| couchbaseObjectTypes | query | Specifies the Couchbase object types to filter objects. | No | array |
| hdfsObjectTypes | query | Specifies the HDFS object types to filter objects. | No | array |
| hbaseObjectTypes | query | Specifies the Hbase object types to filter objects. | No | array |
| hiveObjectTypes | query | Specifies the Hive object types to filter objects. | No | array |
| hypervObjectTypes | query | Specifies the HyperV object types to filter objects. | No | array |
| azureObjectTypes | query | Specifies the Azure object types to filter objects. | No | array |
| kvmObjectTypes | query | Specifies the KVM object types to filter objects. | No | array |
| awsObjectTypes | query | Specifies the AWS object types to filter objects. | No | array |
| gcpObjectTypes | query | Specifies the GCP object types to filter objects. | No | array |
| acropolisObjectTypes | query | Specifies the Acropolis object types to filter objects. | No | array |
| genericNasObjectTypes | query | Specifies the generic NAS object types to filter objects. | No | array |
| isilonObjectTypes | query | Specifies the Isilon object types to filter objects. | No | array |
| flashbladeObjectTypes | query | Specifies the Flashblade object types to filter objects. | No | array |
| elastifileObjectTypes | query | Specifies the Elastifile object types to filter objects. | No | array |
| gpfsObjectTypes | query | Specifies the GPFS object types to filter objects. | No | array |
| pureObjectTypes | query | Specifies the Pure object types to filter objects. | No | array |
| nimbleObjectTypes | query | Specifies the Nimble object types to filter objects. | No | array |
| physicalObjectTypes | query | Specifies the Physical object types to filter objects. | No | array |
| kubernetesObjectTypes | query | Specifies the Kubernetes object types to filter objects. | No | array |
| exchangeObjectTypes | query | Specifies the Exchange object types to filter objects. | No | array |
| adObjectTypes | query | Specifies the AD object types to filter objects. | No | array |
| mssqlObjectTypes | query | Specifies the MSSQL object types to filter objects. | No | array |
| oracleObjectTypes | query | Specifies the Oracle object types to filter objects. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-TIERING/ANALYSIS-GROUPS
## ***GET*** 

**Summary:** Get the list of data tiering analysis groups.

**Description:** Get list of all data tiering analysis groups.

### HTTP Request 
`***GET*** /data-tiering/analysis-groups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Filter by a list of Analysis Group IDs. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a data tiering analysis group.

**Description:** Create a data tiering analysis group.

### HTTP Request 
`***POST*** /data-tiering/analysis-groups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the data tiering analysis group. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-TIERING/ANALYSIS-GROUPS/STATES
## ***POST*** 

**Summary:** Update data tiering analysis groups state.

**Description:** Perform actions like pause or resume on the data tiering analysis
groups for the specified sources.

### HTTP Request 
`***POST*** /data-tiering/analysis-groups/states` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to perform an action of list of data tiering analysis groups. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-TIERING/ANALYSIS-GROUPS/{ID}
## ***GET*** 

**Summary:** Get data tiering analysis group by id.

**Description:** Get data tiering analysis group by id.

### HTTP Request 
`***GET*** /data-tiering/analysis-groups/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the data tiering analysis group. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete data tiering analysis group.

**Description:** Returns NoContentResponse if the data tiering analysis group is
deleted.

### HTTP Request 
`***DELETE*** /data-tiering/analysis-groups/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the data tiering analysis group. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-TIERING/ANALYSIS-GROUPS/{ID}/CONFIG
## ***PUT*** 

**Summary:** Update data tiering analysis group config.

**Description:** Update data tiering analysis group config.

### HTTP Request 
`***PUT*** /data-tiering/analysis-groups/{id}/config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the data tiering analysis group. | Yes | string |
| body | body | Specifies the data tiering analysis Tags Config. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-TIERING/ANALYSIS-GROUPS/{ID}/RUNS
## ***POST*** 

**Summary:** Create a data tiering analysis group run.

**Description:** Create a data tiering analysis group run.

### HTTP Request 
`***POST*** /data-tiering/analysis-groups/{id}/runs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the data tiering analysis group. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 |  |
| default |  |

# /DATA-TIERING/ANALYSIS-GROUPS/{ID}/RUNS/{RUNID}/CANCEL
## ***POST*** 

**Summary:** Cancel data tiering analysis run.

**Description:** Cancel data tiering analysis run for given analysis group ID
and run ID

### HTTP Request 
`***POST*** /data-tiering/analysis-groups/{id}/runs/{runId}/cancel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of data tiering group. | Yes | string |
| runId | path | Specifies a unique run id of data tiering group run. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 |  |
| default |  |

# /DATA-TIERING/TASKS
## ***GET*** 

**Summary:** Get the list of data tiering tasks.

**Description:** Get the list of data tiering tasks.

### HTTP Request 
`***GET*** /data-tiering/tasks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Filter by a list of data tiering task ids. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a data tiering task.

**Description:** Create a data tiering task.

### HTTP Request 
`***POST*** /data-tiering/tasks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a data tiering task. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DATA-TIERING/TASKS/STATES
## ***POST*** 

**Summary:** Update data tiering source analysis tasks state.

**Description:** Perform actions like pause or resume on the data tiering tasks.

### HTTP Request 
`***POST*** /data-tiering/tasks/states` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to perform an action of list of data tiering tasks. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DATA-TIERING/TASKS/{ID}
## ***GET*** 

**Summary:** Get data tiering task by id.

**Description:** Get data tiering task by id.

### HTTP Request 
`***GET*** /data-tiering/tasks/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the data tiering task. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a data tiering task.

**Description:** Update a data tiering task.

### HTTP Request 
`***PUT*** /data-tiering/tasks/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the data tiering task. | Yes | string |
| body | body | Specifies the parameters to update a data tiering task. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** delete the data tiering task.

**Description:** Returns Success if the data tiering task is deleted.

### HTTP Request 
`***DELETE*** /data-tiering/tasks/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the data tiering task. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DATA-TIERING/TASKS/{ID}/RUNS
## ***POST*** 

**Summary:** Create a data tiering tasks run.

**Description:** Create a data tiering tasks run.

### HTTP Request 
`***POST*** /data-tiering/tasks/{id}/runs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the data tiering tasks. | Yes | string |
| body | body | Specifies the request to run tiering task once. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 |  |
| default |  |

# /DATA-TIERING/TASKS/{ID}/RUNS/{RUNID}/CANCEL
## ***POST*** 

**Summary:** Cancel data tiering task.

**Description:** Cancel data tiering task run for given data tiering task id and run id.

### HTTP Request 
`***POST*** /data-tiering/tasks/{id}/runs/{runId}/cancel` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of data tiering task. | Yes | string |
| runId | path | Specifies a unique run id of data tiering task. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 |  |
| default |  |

# /DISKS/ASSIMILATE
## ***POST*** 

**Summary:** Assimilate disks.

**Description:** Assimilate list of disks from one or more nodes of cluster.

### HTTP Request 
`***POST*** /disks/assimilate` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameter to assimilate disks. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DISKS/DISCOVER
## ***GET*** 

**Summary:** Discover new disks

**Description:** Discover disks that are ready for activation

### HTTP Request 
`***GET*** /disks/discover` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DISKS/IDENTIFY
## ***POST*** 

**Summary:** Identify a disk

**Description:** Turn on/off led light of a disk.

### HTTP Request 
`***POST*** /disks/identify` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameter to identify disk. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DISKS/LOCAL
## ***GET*** 

**Summary:** Get list of disks

**Description:** Get list of local disks.

### HTTP Request 
`***GET*** /disks/local` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| nodeId | query | Specifies node id of the node to get list of disks | No | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DISKS/REMOTE
## ***GET*** 

**Summary:** Get remote disks

**Description:** Get remote disks.

### HTTP Request 
`***GET*** /disks/remote` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| diskIds | query | Specifies a list of disk ids, only disks having these ids will be returned. | No | array |
| nodeIds | query | Specifies a list of node ids, only disks in these nodes will be returned. | No | array |
| tiers | query | Specifies a list of disk tiers, only disks with given tiers will be returned. | No | array |
| mountPath | query | This field is deprecated. Providing this queryparam will not have any impact. Please use fileSystem query param to filter instead. | No | string |
| fileSystem | query | Specified file system name to search. only disks with file system name that partially matches the specified name will be returned. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Add remote disk

**Description:** Add a remote disk.

### HTTP Request 
`***POST*** /disks/remote` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the remote disk configuration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DISKS/REMOTE/{ID}
## ***DELETE*** 

**Summary:** Remove remote disk

**Description:** Remove a remote disk.

### HTTP Request 
`***DELETE*** /disks/remote/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the remote disk to remove. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DISKS/{ID}/REMOVE
## ***POST*** 

**Summary:** Mark Disk for removal

**Description:** Mark disk for removal or cancel removal if a disk is already marked for removal.

### HTTP Request 
`***POST*** /disks/{id}/remove` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies unique id of the disk to mark for removal. | Yes | long |
| body | body | Specifies parameters to mark/cancel disk removal. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /DMAAS-TENANT-CERTIFICATE
## ***GET*** 

**Summary:** Get DMaaS tenant certificates on the cluster.

**Description:** Get DMaaS tenant certificates on the cluster.

### HTTP Request 
`***GET*** /dmaas-tenant-certificate` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| tenantIds | query | TenantIds contains ids of the tenants for which tenants are returned. If no tenant id is specified, all tenant certificates are returned. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Add a DMaaS tenant certificate to the cluster.

**Description:** Add a DMaaS tenant certificate to the cluster.

### HTTP Request 
`***POST*** /dmaas-tenant-certificate` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to add the tenant certificate. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /DMAAS-TENANT-CERTIFICATE/{TENANTID}
## ***DELETE*** 

**Summary:** Delete a tenant certificate.

**Description:** Delete a tenant certificate.

### HTTP Request 
`***DELETE*** /dmaas-tenant-certificate/{tenantId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| tenantId | path | Specifies the id of tenant. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /DOMAIN-CONTROLLERS
## ***GET*** 

**Summary:** Get Domain Controllers of specified domains.

**Description:** Get Domain Controllers of specified domains.

### HTTP Request 
`***GET*** /domain-controllers` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| domainNames | query | Specifies a list of domain names. | Yes | array |
| connectionId | query | Specifies the Id of the connection which the connector belongs to. | No | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /FILE-SERVICES/VIEW-TEMPLATE
## ***GET*** 

**Summary:** List View Templates

**Description:** All view templates on the Cohesity Cluster are returned.
Specifying parameters filters the results that are returned.

### HTTP Request 
`***GET*** /file-services/view-template` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a View Template

**Description:** Creates a View Template.

### HTTP Request 
`***POST*** /file-services/view-template` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Request to create a view template. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /FILE-SERVICES/VIEW-TEMPLATE/{ID}
## ***GET*** 

**Summary:** Read a View Template by Id

**Description:** Reads a view template based on given template id.

### HTTP Request 
`***GET*** /file-services/view-template/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the view template. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a View Template

**Description:** Updates a View Template.

### HTTP Request 
`***PUT*** /file-services/view-template/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the view template. | Yes | long |
| body | body | Request to update a view template. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a View Template

**Description:** Deletes a view template based on given template id.

### HTTP Request 
`***DELETE*** /file-services/view-template/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the view template to delete. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /FILE-SERVICES/VIEWS
## ***GET*** 

**Summary:** List Views

**Description:** If no parameters are specified, all Views on the Cohesity Cluster are returned.
Specifying parameters filters the results that are returned.
NOTE: If maxCount is set and the number of Views returned exceeds the maxCount,
there are more Views to return.
To get the next set of Views, send another request and specify the id of the
last View returned in viewList from the previous response.

### HTTP Request 
`***GET*** /file-services/views` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| viewNames | query | Filter by a list of View names. | No | array |
| viewIds | query | Filter by a list of View ids. | No | array |
| storageDomainIds | query | Filter by a list of Storage Domains (View Boxes) specified by id. | No | array |
| storageDomainNames | query | Filter by a list of View Box names. | No | array |
| protocolAccesses | query | Filter by a list of protocol accesses. Only views with protocol accesses in these specified accesses list will be returned. | No | array |
| matchPartialNames | query | If true, the names in viewNames are matched by any partial rather than exactly matched. | No | boolean |
| maxCount | query | Specifies a limit on the number of Views returned. | No | integer |
| includeInternalViews | query | Specifies if internal Views created by the Cohesity Cluster are also returned. In addition, regular Views are returned. | No | boolean |
| includeProtectionGroups | query | Specifies if Protection Groups information needs to be returned along with view metadata. By default, if not set or set to true, Group information is returned. | No | boolean |
| maxViewId | query | If the number of Views to return exceeds the maxCount specified in the original request, specify the id of the last View from the viewList in the previous response to get the next set of Views. | No | long |
| includeInactive | query | Specifies if inactive Views on this Remote Cluster (which have Snapshots copied by replication) should also be returned. Inactive Views are not counted towards the maxCount. By default, this field is set to false. | No | boolean |
| protectionGroupIds | query | Filter by Protection Group ids. Return Views that are being protected by listed Groups, which are specified by ids. | No | array |
| viewCountOnly | query | Whether to get just the total number of views with the given input filters. If the flag is true, we ignore the parameter 'maxViews' for the count. Also, if flag is true, list of views will not be returned. | No | boolean |
| sortByLogicalUsage | query | If set to true, the list is sorted descending by logical usage. | No | boolean |
| internalAccessSids | query | Sids of restricted principals who can access the view. This is an internal field and therefore does not have json tag. | No | array |
| matchAliasNames | query | If true, view aliases are also matched with the names in viewNames. | No | boolean |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | IncludeTenants specifies if objects of all the tenants under the hierarchy of the logged in user's organization should be returned. | No | boolean |
| includeStats | query | If set to true, stats of views will be returned. By default this parameter is set to false. | No | boolean |
| includeViewsWithAntivirusEnabledOnly | query | If set to true, the list will contain only the views for which antivirus scan is enabled. | No | boolean |
| includeViewsWithDataLockEnabledOnly | query | If set to true, the list will contain only the views for which either file level data lock is enabled or view level data lock is enabled. | No | boolean |
| filerAuditLogEnabled | query | If set to true, only views with filer audit log enabled will be returned. If set to false, only views with filer audit log disabled will be returned. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a View

**Description:** Creates a View.

### HTTP Request 
`***POST*** /file-services/views` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Request to create a View. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /FILE-SERVICES/VIEWS/{ID}
## ***GET*** 

**Summary:** Get a View by Id

**Description:** Get a View based on given Id.

### HTTP Request 
`***GET*** /file-services/views/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the View to delete. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a View

**Description:** Updates a View based on given id.

### HTTP Request 
`***PUT*** /file-services/views/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the View to update. | Yes | long |
| body | body | Request to update a view. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a View

**Description:** Deletes a View based on given id.

### HTTP Request 
`***DELETE*** /file-services/views/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the View to delete. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /FLEET-ENV-INFO
## ***POST*** 

**Summary:** Update Fleet Env Info.

**Description:** Add fleet environment info to cluster.

### HTTP Request 
`***POST*** /fleet-env-info` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to add fleet env info. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /HELIOS-REGISTRATION
## ***POST*** 

**Summary:** Register to Helios.

**Description:** Claim to Helios.

### HTTP Request 
`***POST*** /helios-registration` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to claim to Helios. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /HELIOS-REGISTRATION-CONFIG
## ***GET*** 

**Summary:** Lists the Helios Registration Config.

**Description:** Lists the Helios Registration Config.

### HTTP Request 
`***GET*** /helios-registration-config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /KERBEROS-PROVIDERS
## ***GET*** 

**Summary:** Get the list of Kerberos Providers.

**Description:** Get the list of Kerberos Authentication Providers.

### HTTP Request 
`***GET*** /kerberos-providers` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| realmNames | query | Filter by a list of realm names. | No | array |
| ids | query | Filter by a list of Kerberos Provider Ids. | No | array |
| kdcServers | query | Filter by a list of KDC servers. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /KERBEROS-PROVIDERS/REGISTER
## ***POST*** 

**Summary:** Register a Kerberos Authentication Provider.

**Description:** Register a Kerberos Authentication Provider.

### HTTP Request 
`***POST*** /kerberos-providers/register` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to Register a Kerberos Provider. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /KERBEROS-PROVIDERS/UNREGISTER/{ID}
## ***POST*** 

**Summary:** Unregister a Kerberos Provider.

**Description:** Unregister a Kerberos Provider.

### HTTP Request 
`***POST*** /kerberos-providers/unregister/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id. | Yes | string |
| body | body | Request to unregister a Kerberos Provider. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /KERBEROS-PROVIDERS/{ID}
## ***GET*** 

**Summary:** Get the Registered Kerberos Provider by id.

**Description:** Get the Registered Kerberos Provider by id.

### HTTP Request 
`***GET*** /kerberos-providers/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id which will be of the pattern cluster_id:clusterincarnation_id:resource_id. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update the Kerberos Provider Registration.

**Description:** Update the Kerberos Provider Registration.

### HTTP Request 
`***PUT*** /kerberos-providers/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id which will be of the pattern cluster_id:clusterincarnation_id:resource_id. | Yes | string |
| body | body | Request to update a Kerberos Provider. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /KEYSTONES
## ***GET*** 

**Summary:** Get Keystones.

**Description:** Get Keystones.

### HTTP Request 
`***GET*** /keystones` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| names | query | Specifies a list of Keystone names. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which objects are to be returned. | No | array |
| includeTenants | query | If true, the response will include Keystones which were created by all tenants which the current user has permission to see. If false, then only Keystones created by the current user will be returned. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Keystone configuration.

**Description:** Create a Keystone configuration.

### HTTP Request 
`***POST*** /keystones` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the paremters to create a Keystone configuration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /KEYSTONES/{ID}
## ***GET*** 

**Summary:** Get a Keystone by its id.

**Description:** Get a Keystone by its id.

### HTTP Request 
`***GET*** /keystones/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the Keystone id. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Keystone configuration.

**Description:** Update a Keystone configuration.

### HTTP Request 
`***PUT*** /keystones/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the Keystone id. | Yes | long |
| body | body | Specifies the paremters to update a Keystone configuration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Keystone configuration.

**Description:** Delete a Keystone configuration.

### HTTP Request 
`***DELETE*** /keystones/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the Keystone id. | Yes | long |
| adminPassword | header | Specifies the password of Keystone administrator. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /MCM/ACCOUNTS
## ***GET*** 

**Summary:** Get Accounts

**Description:** Get Helios Accounts

### HTTP Request 
`***GET*** /mcm/accounts` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| searchString | query | Filter by accounts which partially match the string. | No | string |
| supportCaseId | query | Filter by Support Case ID. This must be specified if and only if the currently logged in user is a support user. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/CLAIM
## ***POST*** 

**Summary:** Claim a Cohesity Entity.

**Description:** Claim a Cohesity entity to Helios. An entity could be Rigel or a Cohesity Cluster.

### HTTP Request 
`***POST*** /mcm/claim` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Request paramters to claim a Cohesity entity. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /MCM/DATA-PROTECT/OBJECTS/ACTIVITY
## ***POST*** 

**Summary:** Get Object activity on Helios.

**Description:** Get object activity on Helios. Activity includes Protection Group Runs and Recoveries.

### HTTP Request 
`***POST*** /mcm/data-protect/objects/activity` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Request parameters to filter object activity. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/DATA-PROTECT/POLICIES
## ***GET*** 

**Summary:** List Policies based on provided filtering parameters.

**Description:** Lists policies based on filtering query parameters.

### HTTP Request 
`***GET*** /mcm/data-protect/policies` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| ids | query | Filter policies by a list of policy ids. | No | array |
| policyNames | query | Filter policies by a list of policy names. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Policy.

**Description:** Create a Global policy or a DMaaS on Helios.

### HTTP Request 
`***POST*** /mcm/data-protect/policies` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Request to create a Helios Policy. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /MCM/DATA-PROTECT/POLICIES/{ID}
## ***GET*** 

**Summary:** List details about a single Protection Policy.

**Description:** Returns the Protection Policy details based on provided Policy Id.

### HTTP Request 
`***GET*** /mcm/data-protect/policies/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies a unique id of the Protection Policy to return. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Protection Policy.

**Description:** Specifies the request to update the existing Protection Policy. On successful update, returns the updated policy object.

### HTTP Request 
`***PUT*** /mcm/data-protect/policies/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies a unique id of the Protection Policy to update. | Yes | string |
| body | body | Request to update a Protection Policy. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Policy.

**Description:** Deletes a Policy based on given policy id.

### HTTP Request 
`***DELETE*** /mcm/data-protect/policies/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies a unique id of the Policy to delete. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /MCM/DATA-PROTECT/SOURCES
## ***GET*** 

**Summary:** Get a List of Protection Sources.

**Description:** Get a List of Protection Sources.

### HTTP Request 
`***GET*** /mcm/data-protect/sources` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| environments | query | Specifies the list of environment type of the Protection Source. | No | array |
| ids | query | Specifies the list of ids to filter Protection Sources. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/DATA-PROTECT/SOURCES/REGISTRATIONS
## ***POST*** 

**Summary:** Register a Protection Source.

**Description:** Register a Protection Source.

### HTTP Request 
`***POST*** /mcm/data-protect/sources/registrations` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| accessClusterId | header | Specifies the destination cluster id on which this Source needs to be registered. | No | long |
| regionId | header | Specifies the destination region id on which this Source needs to be registered. | No | string |
| body | body | Specifies the parameters to register a Protection Source. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /MCM/DATA-PROTECT/SOURCES/REGISTRATIONS/{ID}
## ***GET*** 

**Summary:** Get a Protection Source registration.

**Description:** Get a Protection Source registration.

### HTTP Request 
`***GET*** /mcm/data-protect/sources/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies the id of the Protection Source registration. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update Protection Source registration.

**Description:** Update Protection Source registration.

### HTTP Request 
`***PUT*** /mcm/data-protect/sources/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies the id of the Protection Source registration. | Yes | string |
| body | body | Specifies the parameters to update the registration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete Protection Source Registration.

**Description:** Delete Protection Source Registration.

### HTTP Request 
`***DELETE*** /mcm/data-protect/sources/registrations/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies the ID of the Protection Source Registration. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /MCM/DATA-PROTECT/SOURCES/TEST-CONNECTION
## ***POST*** 

**Summary:** Test connection to a source.

**Description:** Specifies the endpoint to test the source connectivity.

### HTTP Request 
`***POST*** /mcm/data-protect/sources/test-connection` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| accessClusterId | header | Specifies the destination cluster id on which this Source needs to be registered. | No | long |
| regionId | header | Specifies the destination region id on which this Source needs to be registered. | No | string |
| body | body | Specifies the parameters to test connectivity of a Protection Source. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/IDP/AUTHENTICATE
## ***POST*** 

**Summary:** Create an Identity Provider Configuration.

**Description:** Authenticate Identity Provider (IDP)

### HTTP Request 
`***POST*** /mcm/idp/authenticate` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| SAMLResponse | query | Specifies the parameters to authenticate an Identity Provider. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 302 |  |
| default |  |

# /MCM/IDPS
## ***GET*** 

**Summary:** Get the list of IDP configurations.

**Description:** Get the list of Identity Providers (IDP) configurations.

### HTTP Request 
`***GET*** /mcm/idps` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| ids | query | Filter by a list of IDP ids. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create an Identity Provider Configuration.

**Description:** Create Identity Provider (IDP) Configuration.

### HTTP Request 
`***POST*** /mcm/idps` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Specifies the parameters to create an Identity Provider. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /MCM/IDPS/PRINCIPALS
## ***GET*** 

**Summary:** List IDP Principals

**Description:** List the IDP Principals which have been created.

### HTTP Request 
`***GET*** /mcm/idps/principals` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create an Identity Provider Configuration.

**Description:** Create and IDP User or Group.

### HTTP Request 
`***POST*** /mcm/idps/principals` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Specifies the parameters to create an IDP Principal. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /MCM/IDPS/PRINCIPALS/{SID}
## ***GET*** 

**Summary:** Get IDP Principal by SID

**Description:** List the IDP Principals which have been created.

### HTTP Request 
`***GET*** /mcm/idps/principals/{sid}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sid | path | Specifies the ID of the IDP. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update IDP Principal.

**Description:** Update the specified IDP Principal

### HTTP Request 
`***PUT*** /mcm/idps/principals/{sid}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sid | path | Specifies the SID of the IDP Principal. | Yes | string |
| body | body | Specifies the parameters to update IDP Principal. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete an IDP Principal.

**Description:** Returns Success if the Identity Provider Principal is deleted.

### HTTP Request 
`***DELETE*** /mcm/idps/principals/{sid}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sid | path | Specifies a unique SID of the Principal. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /MCM/IDPS/{ID}
## ***GET*** 

**Summary:** List details about single Identity Provider configuration.

**Description:** Returns a specific Identity Provider configuration.

### HTTP Request 
`***GET*** /mcm/idps/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies a unique id of the IDP. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update IDP Configuration.

**Description:** Update the specified Identity Provider Configuration.

### HTTP Request 
`***PUT*** /mcm/idps/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies the id of the IDP configuration. | Yes | long |
| body | body | Specifies the parameters to update IDP configuration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a IDP configuration.

**Description:** Returns Success if the Identity Provider configuration is deleted.

### HTTP Request 
`***DELETE*** /mcm/idps/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies a unique id of the IDP. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /MCM/SIGNUP
## ***GET*** 

**Summary:** List MCM signup requests.

**Description:** List MCM signup requests.

### HTTP Request 
`***GET*** /mcm/signup` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| emails | query | Specifies a list of email ids to filter the signup requests. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a signup request for MCM.

**Description:** Create a signup request for MCM.

### HTTP Request 
`***POST*** /mcm/signup` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Specifies the parameters to create a signup request for MCM. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /MCM/SIGNUP/{ID}
## ***PUT*** 

**Summary:** Update MCM signup request.

**Description:** Update MCM signup request.

### HTTP Request 
`***PUT*** /mcm/signup/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Specifies the id of the MCM signup request. | Yes | integer |
| body | body | Specifies the parameters to update a signup request for MCM. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/SSLCERTIFICATE
## ***GET*** 

**Summary:** Get the Helios SSL Certificate.

**Description:** Get the Helios SSL certificate.

### HTTP Request 
`***GET*** /mcm/sslCertificate` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/STATS/ALERTS-SUMMARY
## ***GET*** 

**Summary:** Get alerts summary on Helios.

**Description:** Get alerts summary grouped by category.

### HTTP Request 
`***GET*** /mcm/stats/alerts-summary` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| clusterIdentifiers | query | Specifies the list of cluster identifiers. Format is clusterId:clusterIncarnationId. | No | array |
| startTimeUsecs | query | Filter by start time. Specify the start time as a Unix epoch Timestamp (in microseconds). By default it is current time minus a day. | No | long |
| endTimeUsecs | query | Filter by end time. Specify the end time as a Unix epoch Timestamp (in microseconds). By default it is current time. | No | long |
| statesList | query | Specifies list of alert states to filter alerts by. If not specified, only open alerts will be used to get summary. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/STATS/POLICIES/LASTRUN
## ***GET*** 

**Summary:** Compute stats of last Protection Run of Protection Policies.

**Description:** Compute stats of last Protection Run of Protection Policies.

### HTTP Request 
`***GET*** /mcm/stats/policies/lastRun` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/STATS/PROTECTION-RUNS/LAST-RUN
## ***GET*** 

**Summary:** Compute stats of last Protection Run across all objects.

**Description:** Compute stats of last Protection Run across all objects.

### HTTP Request 
`***GET*** /mcm/stats/protection-runs/last-run` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /MCM/USERS
## ***GET*** 

**Summary:** Get Users.

**Description:** Get helios users

### HTTP Request 
`***GET*** /mcm/users` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /NETWORK-INTERFACES
## ***GET*** 

**Summary:** Get list of interfaces

**Description:** Get a list of interfaces present on the node or cluster.

### HTTP Request 
`***GET*** /network-interfaces` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /NETWORKRESET
## ***POST*** 

**Summary:** Set or cancel cluster reset state. This is destructive operation.

**Description:** This is destructive operation. Reset nodes' networking in cluster to factory state or cancel the reset operation.

### HTTP Request 
`***POST*** /networkReset` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Request to reset or restore cluster networking. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 |  |
| default |  |

# /NETWORKRESET/STATUS
## ***GET*** 

**Summary:** List of nodes reset states.

**Description:** Get networking reset state status.

### HTTP Request 
`***GET*** /networkReset/status` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 |  |
| default |  |

# /NIS-NETGROUPS
## ***GET*** 

**Summary:** Get a list of NIS netgroups.

**Description:** Get a list of NIS netgroups.

### HTTP Request 
`***GET*** /nis-netgroups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| netgroupNames | query | Filter by a list of NIS netgroup names. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create an NIS netgroup.

**Description:** Create an NIS netgroup.

### HTTP Request 
`***POST*** /nis-netgroups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create an NIS netgroup. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /NIS-NETGROUPS/{NAME}
## ***GET*** 

**Summary:** Get an NIS netgroup by name.

**Description:** Get an NIS netgroup by name.

### HTTP Request 
`***GET*** /nis-netgroups/{name}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| name | path | Specifies name of the NIS netgroup. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update an NIS netgroup by name.

**Description:** Update an NIS netgroup by name.

### HTTP Request 
`***PUT*** /nis-netgroups/{name}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| name | path | Specifies name of the NIS netgroup. | Yes | string |
| body | body | Request to update the NIS netgroup. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete an NIS netgroup by name.

**Description:** Delete an NIS netgroup by name.

### HTTP Request 
`***DELETE*** /nis-netgroups/{name}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| name | path | Specifies name of the NIS netgroup. | Yes | string |
| body | body | Request to delete the NIS netgroup. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /NIS-PROVIDERS
## ***GET*** 

**Summary:** Get a list of NIS Providers.

**Description:** Get a list of NIS Providers.

### HTTP Request 
`***GET*** /nis-providers` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| domainNames | query | Filter by a list of NIS domain names. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create an NIS Provider.

**Description:** Create an NIS Provider.

### HTTP Request 
`***POST*** /nis-providers` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create an NIS provider entry. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /NIS-PROVIDERS/{DOMAIN}
## ***GET*** 

**Summary:** Get an NIS Provider by domain name.

**Description:** Get an NIS Provider by domain name.

### HTTP Request 
`***GET*** /nis-providers/{domain}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| domain | path | Specifies domain of an NIS Provider. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update an NIS Provider by domain name.

**Description:** Update an NIS Provider by domain name.

### HTTP Request 
`***PUT*** /nis-providers/{domain}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| domain | path | Specifies domain name of an NIS Provider. | Yes | string |
| body | body | Request to update an NIS Provider. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete an NIS Provider by domain name.

**Description:** Delete an NIS Provider by domain name.

### HTTP Request 
`***DELETE*** /nis-providers/{domain}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| domain | path | Specifies domain name of an NIS Provider. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /NODEGROUPS
## ***GET*** 

**Summary:** List Node Groups based on provided filtering parameters.

**Description:** List node groups.

### HTTP Request 
`***GET*** /nodeGroups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| groupNames | query | Filter node groups by a list of node group names. | No | array |
| groupType | query | Filter node groups by a node group type. | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Node Group.

**Description:** Create the Node Group and returns the newly created node group object.

### HTTP Request 
`***POST*** /nodeGroups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Request to create a Node Group. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /NODEGROUPS/{GROUPNAME}
## ***GET*** 

**Summary:** List Node Groups for a given Group Name.

**Description:** Returns Node Group for given Group Name.

### HTTP Request 
`***GET*** /nodeGroups/{groupName}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| groupName | path | Specifies a unique id of Node Group to return. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Node Group.

**Description:** Specifies the request to update the existing Node Group. On successful update, returns the updated node group object.

### HTTP Request 
`***PUT*** /nodeGroups/{groupName}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| groupName | path | Specifies a unique name of the Node Group to update. | Yes | string |
| body | body | Request to update a Node Group. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Node Group.

**Description:** Deletes a Node Group based on given node group name.

### HTTP Request 
`***DELETE*** /nodeGroups/{groupName}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| groupName | path | Specifies a unique name of the Node Group to delete. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /NODEPOWER
## ***POST*** 

**Summary:** Reboot or shutdown nodes in cluster.

**Description:** Reboot or shutdown nodes in cluster.

### HTTP Request 
`***POST*** /nodePower` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the reboot or shutdown operation. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /NODES/{ID}/IDENTIFY
## ***POST*** 

**Summary:** Identify node

**Description:** Turn on/off LED light of a node to identify.

### HTTP Request 
`***POST*** /nodes/{id}/identify` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies id of node to identify. | Yes | long |
| body | body | Specifies the parameter to identify node. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /NODES/{ID}/REMOVE
## ***POST*** 

**Summary:** Mark Node for removal

**Description:** Mark node for removal or Cancel if a node is already marked for removal.

### HTTP Request 
`***POST*** /nodes/{id}/remove` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies id of node to cancel removal. | Yes | long |
| body | body | Specifies parameters to initiate/cancel node removal . | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /PATCH-MANAGEMENT/APPLIED-PATCHES
## ***GET*** 

**Summary:** Get applied patches

**Description:** Returns a list of currently applied patches that are running on the cluster.

### HTTP Request 
`***GET*** /patch-management/applied-patches` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| service | query | Specifies optional service name whose current patch is returned. If it is not specified, all the applied patches are returned. | No | string |
| includeDetails | query | Specifies whether to return the details of all the fixes in the patch. By default, returns only the most recent fix made for the service in the patch. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Revert patches

**Description:** Revert an applied service patch and its dependencies.

### HTTP Request 
`***POST*** /patch-management/applied-patches` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Request to revert patches. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /PATCH-MANAGEMENT/AVAILABLE-PATCHES
## ***GET*** 

**Summary:** Get available patches

**Description:** Returns a list of patches that are available and ready to apply on the cluster.

### HTTP Request 
`***GET*** /patch-management/available-patches` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| service | query | Specifies optional service name whose available patch is returned. If it is not specified, available patches for all the serivces are returned. | No | string |
| includeDetails | query | Specifies whether to return the description of all the fixes in the patch. By default, returns only the most recent fix made for the service in the patch. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Import patches

**Description:** Import a patch or a hotfix to the cluster.

### HTTP Request 
`***PUT*** /patch-management/available-patches` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| fileName | formData |  | Yes | string |
| checksum | formData |  | Yes | string |
| patch | formData |  | Yes | file |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

## ***POST*** 

**Summary:** Apply patches

**Description:** Apply a service patch and its dependencies.

### HTTP Request 
`***POST*** /patch-management/available-patches` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Request to apply patches. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /PATCH-MANAGEMENT/PATCHES-HISTORY
## ***GET*** 

**Summary:** Get patches history

**Description:** Get the history of all the patch management operations.

### HTTP Request 
`***GET*** /patch-management/patches-history` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| service | query | Specifies optional service name whose patch operation history is returned. If it is not specified, patch operations of all the serivces are returned. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /RACKS
## ***GET*** 

**Summary:** Get list of racks

**Description:** Get list of all racks that are part of cluster.

### HTTP Request 
`***GET*** /racks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create racks

**Description:** Create list of racks and optionally also assign list of chassis to each rack

### HTTP Request 
`***POST*** /racks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create racks. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete all the racks.

**Description:** Delete all the racks.

### HTTP Request 
`***DELETE*** /racks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

## ***PATCH*** 

**Summary:** Update racks

**Description:** Updates list of racks with name, chassis list or/and location

### HTTP Request 
`***PATCH*** /racks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to update racks. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /RACKS/{ID}
## ***GET*** 

**Summary:** Get a rack by rack id.

**Description:** Get a rack info by id.

### HTTP Request 
`***GET*** /racks/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of rack. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a rack by id.

**Description:** Delete a given rack by id.

### HTTP Request 
`***DELETE*** /racks/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the rack. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

## ***PATCH*** 

**Description:** Update selected properties of a rack given by id.

### HTTP Request 
`***PATCH*** /racks/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of rack. | Yes | long |
| body | body | Specifies the parameters to update rack. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /REFRESH-BULLETIN-BOARD
## ***POST*** 

**Summary:** Refresh bulletin board from Helios.

**Description:** Refresh bulletin board from Helios.

### HTTP Request 
`***POST*** /refresh-bulletin-board` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /REMOTE-STORAGE
## ***GET*** 

**Summary:** Get Registered Remote Storage Servers List

**Description:** Get summary about list of registered remote storage servers.

### HTTP Request 
`***GET*** /remote-storage` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Register Remote Storage

**Description:** Register a remote storage to be used for disaggregated storage.

### HTTP Request 
`***POST*** /remote-storage` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to register a remote storage management server. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /REMOTE-STORAGE/{ID}
## ***GET*** 

**Summary:** Get remote storage details

**Description:** Get details of remote storage given by id.

### HTTP Request 
`***GET*** /remote-storage/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the registered remote storage. | Yes | long |
| includeAvailableSpace | query | Specifies whether to include available capacity on remote storage. | No | boolean |
| includeAvailableDataVips | query | Specifies whether to include available data vips on remote storage. | No | boolean |
| includeArrayInfo | query | Includes flashblade specific info like name, software os and version of pure flashblade. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete Remote Storage Registration

**Description:** Delete remote storage registration.

### HTTP Request 
`***DELETE*** /remote-storage/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the registration id of the registered remote storage. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

## ***PATCH*** 

**Summary:** Update Remote Storage Config

**Description:** Update Registered Remote Storage Config.

### HTTP Request 
`***PATCH*** /remote-storage/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the registration id of the registered remote storage. | Yes | long |
| body | body | Specifies the parameters to update the registration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /RIGEL-CLAIM-LOGS
## ***GET*** 

**Summary:** Lists the claim logs for rigel.

**Description:** Lists the logs during rigel cluster creation and claim.

### HTTP Request 
`***GET*** /rigel-claim-logs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /SECURITY-CONFIG
## ***GET*** 

**Summary:** Get cluster security settings.

**Description:** Get cluster security settings.

### HTTP Request 
`***GET*** /security-config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update cluster security settings.

**Description:** Update cluster security settings.

### HTTP Request 
`***PUT*** /security-config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to update security config. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /SECURITY-PRINCIPALS
## ***GET*** 

**Summary:** Get Security Principals.

**Description:** Get Security Principals

### HTTP Request 
`***GET*** /security-principals` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| sids | query | Specifies a list of SIDs. | Yes | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /STATS/PROTECTION-RUNS
## ***GET*** 

**Summary:** Get statistics of protection runs.

**Description:** Get statistics of protection runs.

### HTTP Request 
`***GET*** /stats/protection-runs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| startTimeUsecs | query | Specify the start time as a Unix epoch Timestamp (in microseconds), only runs executing after this time will be counted. By default it is current time minus a day. | No | long |
| endTimeUsecs | query | Specify the end time as a Unix epoch Timestamp (in microseconds), only runs executing before this time will be counted. By default it is current time. | No | long |
| runStatus | query | Specifies a list of status, runs matching the status will be returned. 'Running' indicates that the run is still running. 'Canceled' indicates that the run has been canceled. 'Failed' indicates that the run has failed. 'Succeeded' indicates that the run has finished successfully. 'SucceededWithWarning' indicates that the run finished successfully, but there were some warning messages. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /STORAGE-DOMAINS/{ID}
## ***DELETE*** 

**Summary:** Delete a Storage Domain.

**Description:** Delete a Storage Domain.

### HTTP Request 
`***DELETE*** /storage-domains/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specified the Storage Domain id to delete. | Yes | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /SUPPORT-CHANNEL-CONFIG
## ***GET*** 

**Summary:** Get support channel configuration.

**Description:** Get support channel configuration.

### HTTP Request 
`***GET*** /support-channel-config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update support channel configuration.

**Description:** Update support channel configuration.

### HTTP Request 
`***PUT*** /support-channel-config` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the support channel configuration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /SYSLOGAUDITTAGS
## ***GET*** 

**Summary:** Get cluster audit tags.

**Description:** Get cluster audit tags.

### HTTP Request 
`***GET*** /syslogAuditTags` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Update cluster audit tags.

**Description:** Update cluster audit tags.

### HTTP Request 
`***POST*** /syslogAuditTags` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies syslog audit tag to update. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /SYSLOGPROGRAMNAMES
## ***GET*** 

**Summary:** Get supported program names.

**Description:** Get supported program names to configure for a syslog server.

### HTTP Request 
`***GET*** /syslogProgramNames` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /SYSLOGS
## ***GET*** 

**Summary:** Get list of syslog servers.

**Description:** Get list of syslog servers.

### HTTP Request 
`***GET*** /syslogs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Add Syslog Server

**Description:** Add a new syslog server

### HTTP Request 
`***POST*** /syslogs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies parameters to add syslog server. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

## ***DELETE*** 

**Summary:** Remove syslog servers

**Description:** Delete all syslog servers.

### HTTP Request 
`***DELETE*** /syslogs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /SYSLOGS/{ID}
## ***GET*** 

**Summary:** Get a syslog server by id.

**Description:** Get a syslog server by id.

### HTTP Request 
`***GET*** /syslogs/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of syslog server. | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a syslog server by id.

**Description:** Update syslog server by id.

### HTTP Request 
`***PUT*** /syslogs/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of syslog server. | Yes | integer |
| body | body | Specifies the body of syslog server body to update. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Remove syslog server by id

**Description:** Delete syslog server by id.

### HTTP Request 
`***DELETE*** /syslogs/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies a unique id of the syslog server. | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

## ***PATCH*** 

**Summary:** Patch a syslog server by id.

**Description:** Patch syslog server by id.

### HTTP Request 
`***PATCH*** /syslogs/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of syslog server. | Yes | integer |
| body | body | Specifies the body of syslog server fields to patch. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /SYSLOGS/{ID}/STATUS
## ***GET*** 

**Summary:** Get a syslog server reachability status.

**Description:** Check syslog server reachability by given Id.

### HTTP Request 
`***GET*** /syslogs/{id}/status` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of syslog server. | Yes | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /TAGS
## ***GET*** 

**Summary:** Get tags based on filters.

**Description:** If no parameters are specified, all tags are returned.
Specifying parameters filters the results that are returned.

### HTTP Request 
`***GET*** /tags` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Filter by a list of Tag Ids. If Ids are mentioned all other fields will be ignored. | No | array |
| names | query | Filter by a list of Tag names. | No | array |
| namespaces | query | Filter by a list of Namespaces. | No | array |
| tenantIds | query | TenantIds contains ids of the tenants for which tags are to be returned. | No | array |
| includeTenants | query | IncludeTenants specifies if tags of all the tenants under the hierarchy of the logged in user's organization should be returned. False, by default. | No | boolean |
| includeMarkedForDeletion | query | Specifies if tags marked for deletion should be shown. These are tags which are undergoing deletion. False, by default. | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a Tag

**Description:** Creates a Tag.

### HTTP Request 
`***POST*** /tags` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Request to create a Tag. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /TAGS/{ID}
## ***GET*** 

**Summary:** Get Tag by id.

**Description:** Get Tag by id.

### HTTP Request 
`***GET*** /tags/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the Id of the tag. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Tag

**Description:** Updates a Tag by id.

### HTTP Request 
`***PUT*** /tags/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the Id of the tag. | Yes | string |
| body | body | Request to update a tag. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a Tag

**Description:** Deletes a Tag by id.

### HTTP Request 
`***DELETE*** /tags/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the Id of the tag. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /TASKS
## ***GET*** 

**Summary:** Get tasks details.

**Description:** Get details about tasks by providing task ids.

### HTTP Request 
`***GET*** /tasks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Specifies a unique task id to get the deatils of a task. To fetch the status of multiple tasks, pass comma seperated list of taskIds. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /TDM/OBJECTS
## ***GET*** 

**Summary:** Get all TDM objects

**Description:** Get all TDM objects matching specified optional filter criteria.

### HTTP Request 
`***GET*** /tdm/objects` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Get the objects matching specifies IDs. | No | array |
| environments | query | Get the objects matching specified environments. | No | array |
| name | query | Get the objects matching specified name. | No | string |
| taskIds | query | Get the objects belonging to the specified TDM task IDs. | No | array |
| statuses | query | Get the objects matching specified statuses. | No | array |
| paginationCookie | query | Get the next set of objects by specifying the cookie string, as received from the server in the last call. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /TDM/OBJECTS/{ID}
## ***GET*** 

**Summary:** Get TDM object by ID

**Description:** Get a TDM object by specifying its ID.

### HTTP Request 
`***GET*** /tdm/objects/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the ID of the TDM object. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /TDM/OBJECTS/{ID}/TIMELINE-EVENTS
## ***GET*** 

**Summary:** Get timeline events of object

**Description:** Get the collection of timeline events of a TDM object by specifying its ID.

### HTTP Request 
`***GET*** /tdm/objects/{id}/timeline-events` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the ID of the TDM object. | Yes | string |
| createdAfter | query | Get the events created after the specified time (in usecs from epoch). | No | long |
| createdBefore | query | Get the events created before the specified time (in usecs from epoch). | No | long |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /TDM/SNAPSHOTS/{ID}
## ***PUT*** 

**Summary:** Update a snapshot by ID

**Description:** Update the details of a snapshot by specifying its ID.

### HTTP Request 
`***PUT*** /tdm/snapshots/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the ID of the snapshot. | Yes | string |
| body | body | Specifies the parameters to update the snapshot. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete a snapshot by ID

**Description:** Delete a snapshot by specifying its ID.

### HTTP Request 
`***DELETE*** /tdm/snapshots/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the ID of the snapshot. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /TDM/TASKS
## ***GET*** 

**Summary:** Get all TDM tasks

**Description:** Get all the TDM tasks matching specified optional filter criteria.

### HTTP Request 
`***GET*** /tdm/tasks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Get the tasks matching specified IDs. | No | array |
| actions | query | Get the tasks matching specified actions. | No | array |
| environments | query | Get the tasks matching specified environments. | No | array |
| createdAfterUsecs | query | Get the tasks created after the specified time (in usecs from epoch). | No | long |
| createdBeforeUsecs | query | Get the tasks created before the specified time (in usecs from epoch). | No | long |
| statuses | query | Get the tasks matching specified statuses. | No | array |
| objectIds | query | Get the tasks for the specified TDM object IDs. | No | array |
| paginationCookie | query | Get the next set of tasks by specifying the cookie string, as received from the server in the last call. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Create a TDM task

**Description:** Create a task for the Test Data Management (TDM) workflow.

### HTTP Request 
`***POST*** /tdm/tasks` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a TDM task. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /TDM/TASKS/{ID}
## ***GET*** 

**Summary:** Get a TDM task by ID

**Description:** Get a TDM task by ID.

### HTTP Request 
`***GET*** /tdm/tasks/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the ID of the TDM task. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /TENANTS/SWIFT
## ***GET*** 

**Summary:** Get a Swift configuration.

**Description:** Get a Swift configuration.

### HTTP Request 
`***GET*** /tenants/swift` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| tenantId | query | Specifies the tenant Id. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***PUT*** 

**Summary:** Update a Swift configuration.

**Description:** Update a Swift configuration.

### HTTP Request 
`***PUT*** /tenants/swift` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to update a Swift configuration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

# /TENANTS/SWIFT/REGISTER
## ***POST*** 

**Summary:** Register Swift service on a Keystone server.

**Description:** Register Swift service on Keystone server.

### HTTP Request 
`***POST*** /tenants/swift/register` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to register a Swift service on Keystone server. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /TENANTS/SWIFT/UNREGISTER
## ***POST*** 

**Summary:** Unregister Swift service from a Keystone server.

**Description:** Unregister Swift service from Keystone server.

### HTTP Request 
`***POST*** /tenants/swift/unregister` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to unregister a Swift service from Keystone server. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /TRUSTED-CAS
## ***GET*** 

**Summary:** List all Certificates with cluster trust store.

**Description:** List all trusted certificates in cluster trust store.

### HTTP Request 
`***GET*** /trusted-cas` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| ids | query | Specifies the ids of the certificates to be returned. | No | array |
| names | query | Specifies the names of the certificates to be returned. | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***POST*** 

**Summary:** Register CA Certificate to the cluster trust store.

**Description:** Register CA Certificate to the cluster trust store.

### HTTP Request 
`***POST*** /trusted-cas` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to register a Certificate. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /TRUSTED-CAS/{ID}
## ***GET*** 

**Summary:** List the specified Certificate.

**Description:** List the specified Certificate.

### HTTP Request 
`***GET*** /trusted-cas/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the certificate. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| default |  |

## ***DELETE*** 

**Summary:** Unregister CA Certificate from the cluster trust store.

**Description:** Unregister CA Certificate from the cluster trust store.

### HTTP Request 
`***DELETE*** /trusted-cas/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the certificate to be unregistered. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

# /TRUSTED-CAS/{ID}/VALIDATE
## ***POST*** 

**Summary:** Validate CA Certificate.

**Description:** Certificate will be checked for Expiration and Revocation.

### HTTP Request 
`***POST*** /trusted-cas/{id}/validate` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| id | path | Specifies the id of the certificate to be validated. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

# /USERS/SESSIONS
## ***POST*** 

**Summary:** Create a user session

**Description:** Create a user session

### HTTP Request 
`***POST*** /users/sessions` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| body | body | Specifies the parameters to create a user session | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| default |  |

## ***DELETE*** 

**Summary:** Delete user sessions

**Description:** Deletes all sessions for given user sid or system wide sessions

### HTTP Request 
`***DELETE*** /users/sessions` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
|  |  |  | No |  |
| sid | query | Specifies a user sid. If sid is not given system wide sessions are deleted. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 |  |
| default |  |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
