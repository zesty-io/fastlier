# phastly
functional fastly api with promises. A simple, minimal node.js fastly api wrapper. Sends the requests out and gives you back promises which resolve to the parsed object.

For information on request parameters and response formats, please read: <https://docs.fastly.com/api/>

Tested with node4+

Unlike current node fastly wrappers, this library seeks to add administrative endpoints such as adding and removing backends, in addition to purging.

In development and does not immediately seek to cover all endpoints but open to it. Pull requests and feature requests welcome.

## Usage

### Promises

```js
import * as fastly from 'phastly'

function setup(name) {
  fastly.createService(name)
  .then((newService) => {
    // use newService here
  })
}
```

### Async/Await
```js
import * as fastly from 'phastly'

async function setup(name) {
  let newService = await fastly.createService(name)
  // use newService here
}
```

## API Reference
phastly module.


* [phastly](#module_phastly)
    * [.sendP(request)](#module_phastly.sendP) ⇒ <code>Promise</code>
    * [.purgeUrlP(url, [soft])](#module_phastly.purgeUrlP) ⇒ <code>Promise</code>
    * [.purgeP(serviceId, key, [soft])](#module_phastly.purgeP) ⇒ <code>Promise</code>
    * [.purgeAllP(serviceId)](#module_phastly.purgeAllP) ⇒ <code>Promise</code>
    * [.createBackendP(serviceId, version, data)](#module_phastly.createBackendP) ⇒ <code>Promise</code>
    * [.deleteBackendP(serviceId, version, name)](#module_phastly.deleteBackendP) ⇒ <code>Promise</code>
    * [.createServiceP(name)](#module_phastly.createServiceP) ⇒ <code>Promise</code>
    * [.createServiceVersionP(serviceId)](#module_phastly.createServiceVersionP) ⇒ <code>Promise</code>
    * [.updateServiceVersionP(serviceId, version, data)](#module_phastly.updateServiceVersionP) ⇒ <code>Promise</code>
    * [.validateServiceVersionP(serviceId, version)](#module_phastly.validateServiceVersionP) ⇒ <code>Promise</code>
    * [.activateServiceVersionP(serviceId, version)](#module_phastly.activateServiceVersionP) ⇒ <code>Promise</code>
    * [.deactivateServiceVersionP(serviceId, version)](#module_phastly.deactivateServiceVersionP) ⇒ <code>Promise</code>
    * [.cloneServiceVersion(serviceId, version)](#module_phastly.cloneServiceVersion) ⇒ <code>Promise</code>
    * [.lockServiceVersion(serviceId, version)](#module_phastly.lockServiceVersion) ⇒ <code>Promise</code>
    * [.deleteServiceP(serviceId)](#module_phastly.deleteServiceP) ⇒ <code>Promise</code>
    * [.renameServiceP(serviceId, newName)](#module_phastly.renameServiceP) ⇒ <code>Promise</code>
    * [.ListServicesP()](#module_phastly.ListServicesP) ⇒ <code>Promise</code>
    * [.getServiceP(serviceId)](#module_phastly.getServiceP) ⇒ <code>Promise</code>
    * [.getServiceDetailsP(serviceId)](#module_phastly.getServiceDetailsP) ⇒ <code>Promise</code>
    * [.getServiceDomainsP(service)](#module_phastly.getServiceDomainsP) ⇒ <code>Promise</code>
    * [.createDomainP(serviceId, version, data)](#module_phastly.createDomainP) ⇒ <code>Promise</code>
    * [.createRequestSettingP(serviceId, version, settings)](#module_phastly.createRequestSettingP) ⇒ <code>Promise</code>
    * [.updateSettingsP(serviceId, version, settings)](#module_phastly.updateSettingsP) ⇒ <code>Promise</code>

<a name="module_phastly.sendP"></a>

### phastly.sendP(request) ⇒ <code>Promise</code>
send the fastly request

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolving to response  

| Param | Type | Description |
| --- | --- | --- |
| request | <code>Object</code> | options |

<a name="module_phastly.purgeUrlP"></a>

### phastly.purgeUrlP(url, [soft]) ⇒ <code>Promise</code>
Instant Purge an individual URL. Soft Purging sets an object's TTL to 0s, forcing revalidation. For best results, Soft Purging should be used in conjuction with stale_while_revalidate and stale_if_error.

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type | Default |
| --- | --- | --- |
| url | <code>string</code> |  | 
| [soft] | <code>Boolean</code> | <code>false</code> | 

<a name="module_phastly.purgeP"></a>

### phastly.purgeP(serviceId, key, [soft]) ⇒ <code>Promise</code>
Instant Purge a particular service of items tagged with a Surrogate Key. Soft Purging sets an object's TTL to 0s, forcing revalidation. For best results, Soft Purging should be used in conjuction with stale_while_revalidate and stale_if_error.

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| serviceId | <code>string</code> |  |  |
| key | <code>string</code> |  |  |
| [soft] | <code>Boolean</code> | <code>false</code> | sets an object's TTL to 0s |

<a name="module_phastly.purgeAllP"></a>

### phastly.purgeAllP(serviceId) ⇒ <code>Promise</code>
Instant Purge everything from a service

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 

<a name="module_phastly.createBackendP"></a>

### phastly.createBackendP(serviceId, version, data) ⇒ <code>Promise</code>
Create a backend for a particular service and version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type | Description |
| --- | --- | --- |
| serviceId | <code>string</code> |  |
| version | <code>number</code> |  |
| data | <code>Object</code> | keys are backend object keys |

<a name="module_phastly.deleteBackendP"></a>

### phastly.deleteBackendP(serviceId, version, name) ⇒ <code>Promise</code>
Delete the backend for a particular service and version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type | Description |
| --- | --- | --- |
| serviceId | <code>string</code> |  |
| version | <code>number</code> |  |
| name | <code>string</code> | name of backend |

<a name="module_phastly.createServiceP"></a>

### phastly.createServiceP(name) ⇒ <code>Promise</code>
Create a service

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| name | <code>string</code> | 

<a name="module_phastly.createServiceVersionP"></a>

### phastly.createServiceVersionP(serviceId) ⇒ <code>Promise</code>
Create a version for a particular service

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 

<a name="module_phastly.updateServiceVersionP"></a>

### phastly.updateServiceVersionP(serviceId, version, data) ⇒ <code>Promise</code>
Update a particular version for a particular service.

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type | Description |
| --- | --- | --- |
| serviceId | <code>string</code> |  |
| version | <code>number</code> |  |
| data | <code>Object</code> | keys are service object keys |

<a name="module_phastly.validateServiceVersionP"></a>

### phastly.validateServiceVersionP(serviceId, version) ⇒ <code>Promise</code>
Validate the version for a particular service and version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 
| version | <code>number</code> | 

<a name="module_phastly.activateServiceVersionP"></a>

### phastly.activateServiceVersionP(serviceId, version) ⇒ <code>Promise</code>
Activate the current version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 
| version | <code>number</code> | 

<a name="module_phastly.deactivateServiceVersionP"></a>

### phastly.deactivateServiceVersionP(serviceId, version) ⇒ <code>Promise</code>
Deactivate the current version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 
| version | <code>number</code> | 

<a name="module_phastly.cloneServiceVersion"></a>

### phastly.cloneServiceVersion(serviceId, version) ⇒ <code>Promise</code>
Clone the current configuration into a new version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 
| version | <code>number</code> | 

<a name="module_phastly.lockServiceVersion"></a>

### phastly.lockServiceVersion(serviceId, version) ⇒ <code>Promise</code>
Locks the specified version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 
| version | <code>number</code> | 

<a name="module_phastly.deleteServiceP"></a>

### phastly.deleteServiceP(serviceId) ⇒ <code>Promise</code>
Delete a service

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 

<a name="module_phastly.renameServiceP"></a>

### phastly.renameServiceP(serviceId, newName) ⇒ <code>Promise</code>
Rename a service

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 
| newName | <code>string</code> | 

<a name="module_phastly.ListServicesP"></a>

### phastly.ListServicesP() ⇒ <code>Promise</code>
List services

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  
<a name="module_phastly.getServiceP"></a>

### phastly.getServiceP(serviceId) ⇒ <code>Promise</code>
Get a service by id

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 

<a name="module_phastly.getServiceDetailsP"></a>

### phastly.getServiceDetailsP(serviceId) ⇒ <code>Promise</code>
List detailed information on a specified service

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type |
| --- | --- |
| serviceId | <code>string</code> | 

<a name="module_phastly.getServiceDomainsP"></a>

### phastly.getServiceDomainsP(service) ⇒ <code>Promise</code>
List the domains within a service

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to deserialized response  

| Param | Type | Description |
| --- | --- | --- |
| service | <code>string</code> | id |

<a name="module_phastly.createDomainP"></a>

### phastly.createDomainP(serviceId, version, data) ⇒ <code>Promise</code>
Create a domain for a particular service and version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type | Description |
| --- | --- | --- |
| serviceId | <code>string</code> |  |
| version | <code>number</code> |  |
| data | <code>Object</code> | fastly domain object |

<a name="module_phastly.createRequestSettingP"></a>

### phastly.createRequestSettingP(serviceId, version, settings) ⇒ <code>Promise</code>
Create a new Request Settings object

**Kind**: static method of <code>[phastly](#module_phastly)</code>  

| Param | Type | Description |
| --- | --- | --- |
| serviceId | <code>string</code> |  |
| version | <code>number</code> |  |
| settings | <code>Object</code> | fastly request settings object: {hash_keys, action, ...} |

<a name="module_phastly.updateSettingsP"></a>

### phastly.updateSettingsP(serviceId, version, settings) ⇒ <code>Promise</code>
Update the settings for a particular service and version

**Kind**: static method of <code>[phastly](#module_phastly)</code>  
**Returns**: <code>Promise</code> - resolves to parsed api result object  

| Param | Type | Description |
| --- | --- | --- |
| serviceId | <code>string</code> |  |
| version | <code>number</code> |  |
| settings | <code>Object</code> | fastly settings object e.g. {general.default_host, general.default_ttl, ...} |

