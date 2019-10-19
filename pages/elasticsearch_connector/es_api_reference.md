---
title: Elasticsearch Connector API Reference 
keywords: sample
sidebar: elasticsearch_connector_sidebar
permalink: es_api_reference.html
folder: elasticsearch_connector
---
Configurations
==============

---

Config
------

Default configuration

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>String</p></td>
<td><p>The name for this configuration. Connectors reference the configuration with this name.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Connection</p></td>
<td><ul>
<li><p><a href="#config_http-connection">HTTP Connection</a>  </p></li>
<li><p><a href="#config_https-connection">HTTPS Connection</a>  </p></li>
</ul></td>
<td><p>The connection types that can be provided to this configuration.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Expiration Policy</p></td>
<td>ExpirationPolicy</td>
<td><p>Configures the minimum amount of time that a dynamic configuration instance can remain idle before the runtime considers it eligible for expiration. This does not mean that the platform will expire the instance at the exact moment that it becomes eligible. The runtime will actually purge the instances when it sees it fit.</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Connection Types

#### HTTP Connection



<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Host</p></td>
<td>String</td>
<td><p>ElasticSearch instance host IP or DNS name</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Port</p></td>
<td>Number</td>
<td><p>ElasticSearch instance port</p></td>
<td><p>9200</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>User Name</p></td>
<td>String</td>
<td><p>Elasticsearch instance username. Keep this blank for anonymous user.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Password</p></td>
<td>String</td>
<td><p>Elasticsearch instance password. Keep this blank for anonymous user.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Reconnection</p></td>
<td>Reconnection</td>
<td><p>When the application is deployed, a connectivity test is performed on all connectors. If set to true, deployment will fail if the test doesn't pass after exhausting the associated reconnection strategy</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

#### HTTPS Connection


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Host</p></td>
<td>String</td>
<td><p>ElasticSearch instance host IP or DNS name</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Port</p></td>
<td>Number</td>
<td><p>ElasticSearch instance port</p></td>
<td><p>9200</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>User Name</p></td>
<td>String</td>
<td><p>Elasticsearch instance username. Keep this blank for anonymous user.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Password</p></td>
<td>String</td>
<td><p>Elasticsearch instance password. Keep this blank for anonymous user.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Type</p></td>
<td>String</td>
<td><p>Type of the TrustStore</p></td>
<td><p>jks</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Path</p></td>
<td>String</td>
<td><p>TrustStore file path</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Password</p></td>
<td>String</td>
<td><p>Trust store password</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection</p></td>
<td>Reconnection</td>
<td><p>When the application is deployed, a connectivity test is performed on all connectors. If set to true, deployment will fail if the test doesn't pass after exhausting the associated reconnection strategy</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Associated Operations

-   [Bulk Operation](#bulk-operation)

-   [Clear Scroll](#clear-scroll)  

-   [Close Index](#close-index)  

-   [Create Index](#create-index)  

-   [Delete Document](#delete-document)  

-   [Delete Index](#delete-index)  

-   [Get Document](#get-document)  

-   [Index Document](#index-document)  

-   [Info](#info)  

-   [Open Index](#open-index)  

-   [Search](#search)  

-   [Search Scroll](#search-scroll)  

-   [Search Using Json Data](#search-using-json-data)  

-   [Update Document](#update-document)  

Operations
==========

[Bulk Operation](#bulk-operation)
--------------

`<elasticsearch:bulk-operation>`

Bulk operation makes it possible to perform many index, delete and update operations in a single API call.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>Index name on which bulk operation Performed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Type</p></td>
<td>String</td>
<td><p>Type name on which bulk operation Performed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>File</p></td>
<td>String</td>
<td><p>Provide the JSON file path</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Text</p></td>
<td>String</td>
<td><p>Provide the JSON string</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>Response</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Clear Scroll](#clear-scroll)
------------

`<elasticsearch:clear-scroll>`

The search contexts used by the Search Scroll operation are automatically deleted when the scroll times out. Clear scroll operation release search contexts as soon as they are not necessary anymore using the Clear Scroll.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Scroll ID</p></td>
<td>String</td>
<td><p>Scroll identifier to clear scroll</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>ClearScrollResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Close Index](#closeIndex)
-----------

`<elasticsearch:close-index>`

A closed index has almost no overhead. It is used to close an Index. If you want to keep your data but save resources (memory/CPU), a good alternative to deleting an index is to close them.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>The index to close</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Timeout</p></td>
<td>String</td>
<td><p>Time to wait for the all the nodes to acknowledge if the index is closed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Mater Node Timeout</p></td>
<td>String</td>
<td><p>Timeout to connect to the master node</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Indices Opt</p></td>
<td>IndexOptions</td>
<td><p>IndicesOptions controls how unavailable indices are resolved and how wildcard expressions are expanded</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>CloseIndexResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Create Index](#create-index)
------------

`<elasticsearch:create-index>`

The createIndex Operation allows to instantiate an index.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>The index to create</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Index Settings</p></td>
<td>Object</td>
<td><p>Settings for this index</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Index Settings JSON</p></td>
<td>String</td>
<td><p>Index Settings JSON</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Type for Mapping</p></td>
<td>String</td>
<td><p>The index type to define index</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Index Mapping</p></td>
<td>Object</td>
<td><p>The mapping for index type, provided as a JSON string</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>JSON Input file path for mapping</p></td>
<td>String</td>
<td><p>Path of the JSON file. The whole source including all of its sections (mappings, settings and aliases) can be provided in this json file.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Index Alias</p></td>
<td>String</td>
<td><p>The alias of the index</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Timeout</p></td>
<td>String</td>
<td><p>Timeout to wait for the all the nodes to acknowledge the index creation</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Master Node Timeout</p></td>
<td>String</td>
<td><p>Timeout to connect to the master node</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Wait for Active Shards</p></td>
<td>Number</td>
<td><p>The number of active shard copies to wait for before the create index</p></td>
<td><p>0</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>CreateIndexResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Delete Document](#delete-document)
---------------

`<elasticsearch:delete-document>`

Delete Document operation allows to delete a typed JSON document from a specific index based on its id

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>Name of the index</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Type</p></td>
<td>String</td>
<td><p>Type of the index</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Document Id</p></td>
<td>String</td>
<td><p>ID of the document</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Routing value</p></td>
<td>String</td>
<td><p>Routing is used to determine in which shard the document will reside in</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Parent value</p></td>
<td>String</td>
<td><p>Parent value of the index request</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Timeout</p></td>
<td>String</td>
<td><p>Time to wait for primary shard to become available</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Refresh policy</p></td>
<td>Enumeration, one of:
<ul>
<li><p>NONE</p></li>
<li><p>IMMEDIATE</p></li>
<li><p>WAIT_UNTIL</p></li>
</ul></td>
<td><p>Refresh policy is used to control when changes made by the requests are made visible to search. Option for refresh policy A) true : Refresh the relevant primary and replica shards (not the whole index) immediately after the operation occurs, so that the updated document appears in search results immediately. B) wait_for : Wait for the changes made by the request to be made visible by a refresh before replying. This doesn?t force an immediate refresh, rather, it waits for a refresh to happen. C) false (default) : Take no refresh related actions. The changes made by this request will be made visible at some point after the request returns.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Version</p></td>
<td>Number</td>
<td><p>Version number of the indexed document</p></td>
<td><p>0</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Version Type</p></td>
<td>Enumeration, one of:
<ul>
<li><p>INTERNAL</p></li>
<li><p>EXTERNAL</p></li>
<li><p>EXTERNAL_GTE</p></li>
<li><p>FORCE</p></li>
</ul></td>
<td><p>Version type: internal, external, external_gte</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>DeleteResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Delete Index](#delete-index)
------------

`<elasticsearch:delete-index>`

The Delete index operation allows to delete an existing index.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>The index to delete</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Timeout</p></td>
<td>String</td>
<td><p>Timeout to wait for the all the nodes to acknowledge the index deletion</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Mater Node Timeout</p></td>
<td>String</td>
<td><p>Timeout to connect to the master node</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Indices Opts</p></td>
<td>IndexOptions</td>
<td><p>IndicesOptions controls how unavailable indices are resolved and how wildcard expressions are expanded</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>DeleteIndexResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Get Document](#get-document)
------------

`<elasticsearch:get-document>`

Get Document operation allows to get a typed JSON document from the index based on its id.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>Name of the index</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Type</p></td>
<td>String</td>
<td><p>Type of the index</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Document Id</p></td>
<td>String</td>
<td><p>ID of the document</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Source retrieval</p></td>
<td>DocumentFetchSourceOptions</td>
<td><p>Enable or disable source retrieval</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Routing</p></td>
<td>String</td>
<td><p>Routing is used to determine in which shard the document will reside in</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Parent</p></td>
<td>String</td>
<td><p>Parent value of the index request</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Preference value</p></td>
<td>String</td>
<td><p>Preference value</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Set realtime flag</p></td>
<td>Boolean</td>
<td><p>Set realtime flag</p></td>
<td><p>true</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Refresh</p></td>
<td>Boolean</td>
<td><p>Perform a refresh before retrieving the document</p></td>
<td><p>false</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Version</p></td>
<td>Number</td>
<td><p>Version number of the indexed document</p></td>
<td><p>0</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Version Type</p></td>
<td>Enumeration, one of:
<ul>
<li><p>INTERNAL</p></li>
<li><p>EXTERNAL</p></li>
<li><p>EXTERNAL_GTE</p></li>
<li><p>FORCE</p></li>
</ul></td>
<td><p>Version type: internal, external, external_gte,</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Output Mime Type</p></td>
<td>String</td>
<td><p>The mime type of the payload that this operation outputs.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>String</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Index Document](#index-document)
--------------

`<elasticsearch:index-document>`

Index Document operation adds or updates a typed JSON document in a specific index, making it searchable.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>Name of the index</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Type</p></td>
<td>String</td>
<td><p>Type of the index</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Document Id</p></td>
<td>String</td>
<td><p>ID of the document</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Routing</p></td>
<td>String</td>
<td><p>Routing is used to determine in which shard the document will reside in</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Parent</p></td>
<td>String</td>
<td><p>A parent-child relationship can be established between documents in the same index by making one mapping type the parent of another</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Timeout</p></td>
<td>String</td>
<td><p>Timeout to wait for primary shard to become available</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Refresh policy</p></td>
<td>Enumeration, one of:
<ul>
<li><p>NONE</p></li>
<li><p>IMMEDIATE</p></li>
<li><p>WAIT_UNTIL</p></li>
</ul></td>
<td><p>Refresh policy is used to control when changes made by the requests are made visible to search. Option for refresh policy A) true : Refresh the relevant primary and replica shards (not the whole index) immediately after the operation occurs, so that the updated document appears in search results immediately. B) wait_for : Wait for the changes made by the request to be made visible by a refresh before replying. This doesn?t force an immediate refresh, rather, it waits for a refresh to happen. C) false (default) : Take no refresh related actions. The changes made by this request will be made visible at some point after the request returns.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Version</p></td>
<td>Number</td>
<td><p>Version number of the indexed document. It will control the version of the document the operation is intended to be executed against.</p></td>
<td><p>0</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Version Type</p></td>
<td>Enumeration, one of:
<ul>
<li><p>INTERNAL</p></li>
<li><p>EXTERNAL</p></li>
<li><p>EXTERNAL_GTE</p></li>
<li><p>FORCE</p></li>
</ul></td>
<td><p>Version type: internal, external, external_gte</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Operation type</p></td>
<td>Enumeration, one of:
<ul>
<li><p>INDEX</p></li>
<li><p>CREATE</p></li>
<li><p>UPDATE</p></li>
<li><p>DELETE</p></li>
</ul></td>
<td><p>Type of the operation. When create type is used, the index operation will fail if a document by that id already exists in the index.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Pipeline</p></td>
<td>String</td>
<td><p>Name of the ingest pipeline to be executed before indexing the document</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>JSON Input file path</p></td>
<td>String</td>
<td><p>Provide the JSON file path</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Document Source</p></td>
<td>Object</td>
<td><p>Provide the Document source</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>IndexResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Info](#info)
----

`<elasticsearch:info>`

To retrieve the cluster information.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>MainResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Open Index](#open-index)
----------

`<elasticsearch:open-index>`

Open Index operation allow to open an index.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>The index to open</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Timeout</p></td>
<td>String</td>
<td><p>Timeout to wait for the all the nodes to acknowledge the index is opened. It is the time to wait for an open index to become available to elasticsearch.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Mater Node Timeout</p></td>
<td>String</td>
<td><p>Timeout to connect to the master node</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Wait for Active Shards</p></td>
<td>Number</td>
<td><p>The number of active shard copies to wait for</p></td>
<td><p>0</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Indices Opts</p></td>
<td>IndexOptions</td>
<td><p>IndicesOptions controls how unavailable indices are resolved and how wildcard expressions are expanded</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>OpenIndexResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Search](#search)
------

`<elasticsearch:search>`

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Query Type</p></td>
<td>One of:
<ul>
<li><p><a href="#MatchQuery">section_title</a></p></li>
<li><p><a href="#MultiMatchQuery">section_title</a></p></li>
<li><p><a href="#MatchAllQuery">section_title</a></p></li>
<li><p><a href="#MatchPhraseQuery">section_title</a></p></li>
<li><p><a href="#MatchPhrasePrefixQuery">section_title</a></p></li>
<li><p><a href="#CommonTermsQuery">section_title</a></p></li>
<li><p><a href="#QueryStringQuery">section_title</a></p></li>
<li><p><a href="#SimpleQueryString">section_title</a></p></li>
</ul></td>
<td><p>Different types of Elasticsearch query query configuration</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Search Source</p></td>
<td>SearchSourceConfiguration</td>
<td><p>Search source configuration to control the search behavior.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>Restricts the search request to an index</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Search Type</p></td>
<td>Enumeration, one of:
<ul>
<li><p>DFS_QUERY_THEN_FETCH</p></li>
<li><p>QUERY_THEN_FETCH</p></li>
<li><p>QUERY_AND_FETCH</p></li>
</ul></td>
<td><p>The type of the search operation to perform</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Type</p></td>
<td>String</td>
<td><p>Limits the search request to a type</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Routing</p></td>
<td>String</td>
<td><p>Search the document using routing</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Scroll Interval Time</p></td>
<td>Number</td>
<td><p>Scroll interval time keep the search context alive(minutes). If value is non-zero, scroll search is initiated.</p></td>
<td><p>0</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>SearchResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Search Scroll](#search-scroll)
-------------

`<elasticsearch:search-scroll>`

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Scroll Id</p></td>
<td>String</td>
<td><p>Scroll identifier returned in last scroll request</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Keep alive time</p></td>
<td>Number</td>
<td><p>Set the scroll interval time keep the search context alive(minutes)</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>SearchResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Search Using Json Data](#search-using-json-data)
----------------------

`<elasticsearch:search-using-json-data>`

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>Restricts the search request to an index</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Output Mime Type</p></td>
<td>String</td>
<td><p>The mime type of the payload that this operation outputs.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>File</p></td>
<td>String</td>
<td><p>Provide the JSON file path</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Text</p></td>
<td>String</td>
<td><p>Provide the JSON string</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>String</td>
</tr>
<tr class="even">
<td><p><strong>Attributes Type</strong></p></td>
<td>StatusLine</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

[Update Document](#update-document)
---------------

`<elasticsearch:update-document>`

Update Document operation allows to update a document based on a script provided.

### Parameters

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 35%" />
<col style="width: 20%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>String</p></td>
<td><p>The name of the configuration to use.</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td><p>Name of the index</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Type</p></td>
<td>String</td>
<td><p>Type of the index</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="even">
<td><p>Document Id</p></td>
<td>String</td>
<td><p>ID of the document</p></td>
<td></td>
<td><p><strong>x</strong> </p></td>
</tr>
<tr class="odd">
<td><p>Routing</p></td>
<td>String</td>
<td><p>Routing is used to determine in which shard the document will reside in</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Parent</p></td>
<td>String</td>
<td><p>Parent value of the index request</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Timeout</p></td>
<td>String</td>
<td><p>Time to wait for primary shard to become available</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Refresh policy</p></td>
<td>Enumeration, one of:
<ul>
<li><p>NONE</p></li>
<li><p>IMMEDIATE</p></li>
<li><p>WAIT_UNTIL</p></li>
</ul></td>
<td><p>Refresh policy is used to control when changes made by the requests are made visible to search. Option for refresh policy A) true : Refresh the relevant primary and replica shards (not the whole index) immediately after the operation occurs, so that the updated document appears in search results immediately. B) wait_for : Wait for the changes made by the request to be made visible by a refresh before replying. This doesn?t force an immediate refresh, rather, it waits for a refresh to happen. C) false (default) : Take no refresh related actions. The changes made by this request will be made visible at some point after the request returns.</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Retry on Conflict</p></td>
<td>Number</td>
<td><p>How many times to retry the update operation if the document to update has been changed by another operation between the get and indexing phases of the update operation</p></td>
<td><p>0</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Fetch Source</p></td>
<td>Boolean</td>
<td><p>Enable or disable source retrieval</p></td>
<td><p>false</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Version</p></td>
<td>Number</td>
<td><p>Version number of the indexed document</p></td>
<td><p>0</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Noop Detection</p></td>
<td>Boolean</td>
<td><p>Enable or disable the noop detection</p></td>
<td><p>true</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Scripted Upsert</p></td>
<td>Boolean</td>
<td><p>Indicate that the script must run regardless of whether the document exists or not</p></td>
<td><p>false</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Doc Upsert</p></td>
<td>Boolean</td>
<td><p>Indicate that the partial document must be used as the upsert document if it does not exist yet.</p></td>
<td><p>false</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>JSON Input file path</p></td>
<td>String</td>
<td><p>Provide the JSON file path</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Document Source</p></td>
<td>Object</td>
<td><p>Provide the Document source</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Target Variable</p></td>
<td>String</td>
<td><p>The name of a variable on which the operation's output will be placed</p></td>
<td></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Target Value</p></td>
<td>String</td>
<td><p>An expression that will be evaluated against the operation's output and the outcome of that expression will be stored in the target variable</p></td>
<td><p>#[payload]</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>A retry strategy in case of connectivity errors</p></td>
<td></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

### Output

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td>UpdateResponse</td>
</tr>
</tbody>
</table>

### For Configurations.

-   [Config](#config)  

### Throws

-   ELASTICSEARCH:INVALID\_CONNECTION  

-   ELASTICSEARCH:CONNECTIVITY  

-   ELASTICSEARCH:RETRY\_EXHAUSTED  

-   ELASTICSEARCH:OPERATION\_FAILED  

-   ELASTICSEARCH:INVALID\_AUTH  

Types
=====

Reconnection
------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Fails Deployment</p></td>
<td>Boolean</td>
<td><p>When the application is deployed, a connectivity test is performed on all connectors. If set to true, deployment will fail if the test doesn’t pass after exhausting the associated reconnection strategy</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Reconnection Strategy</p></td>
<td><ul>
<li><p><a href="#reconnect">Reconnect</a></p></li>
<li><p><a href="#reconnect-forever">Reconnect Forever</a></p></li>
</ul></td>
<td><p>The reconnection strategy to use</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Reconnect
---------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Frequency</p></td>
<td>Number</td>
<td><p>How often (in ms) to reconnect</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Count</p></td>
<td>Number</td>
<td><p>How many reconnection attempts to make</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Reconnect Forever
-----------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Frequency</p></td>
<td>Number</td>
<td><p>How often (in ms) to reconnect</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Expiration Policy
-----------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Max Idle Time</p></td>
<td>Number</td>
<td><p>A scalar time value for the maximum amount of time a dynamic configuration instance should be allowed to be idle before it’s considered eligible for expiration</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Time Unit</p></td>
<td>Enumeration, one of:
<ul>
<li><p>NANOSECONDS</p></li>
<li><p>MICROSECONDS</p></li>
<li><p>MILLISECONDS</p></li>
<li><p>SECONDS</p></li>
<li><p>MINUTES</p></li>
<li><p>HOURS</p></li>
<li><p>DAYS</p></li>
</ul></td>
<td><p>A time unit that qualifies the maxIdleTime attribute</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Response
--------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Entity</p></td>
<td>HttpEntity</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Headers</p></td>
<td>Array of Header</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Host</p></td>
<td>HttpHost</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Request Line</p></td>
<td>RequestLine</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Status Line</p></td>
<td>StatusLine</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Http Host
---------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Address</p></td>
<td>Any</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Host Name</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Port</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Scheme Name</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Clear Scroll Response
---------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Num Freed</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Succeeded</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Close Index Response
--------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Acknowledged</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Index Options
-------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ignore Unavailable</p></td>
<td>Boolean</td>
<td></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Allow No Indices</p></td>
<td>Boolean</td>
<td></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Expand To Open Indices</p></td>
<td>Boolean</td>
<td></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Expand To Closed Indices</p></td>
<td>Boolean</td>
<td></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Allow Aliases To Multiple Indices</p></td>
<td>Boolean</td>
<td></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Forbid Closed Indices</p></td>
<td>Boolean</td>
<td></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Ignore Aliases</p></td>
<td>Boolean</td>
<td></td>
<td><p>false</p></td>
<td></td>
</tr>
</tbody>
</table>

Create Index Response
---------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Acknowledged</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Shards Acked</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Shards Acknowledged</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Delete Response
---------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Forced Refresh</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Id</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Index</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Primary Term</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Result</p></td>
<td>Enumeration, one of:
<ul>
<li><p>CREATED</p></li>
<li><p>UPDATED</p></li>
<li><p>DELETED</p></li>
<li><p>NOT_FOUND</p></li>
<li><p>NOOP</p></li>
</ul></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Seq No</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Shard Id</p></td>
<td>ShardId</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Shard Info</p></td>
<td>ShardInfo</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Type</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Shard Id
--------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Id</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>Index</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Index Name</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Shard Info
----------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Failed</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Failures</p></td>
<td>Array of Failure</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Successful</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Total</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Failure
-------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cause</p></td>
<td>Any</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Delete Index Response
---------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Acknowledged</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Document Fetch Source Options
-----------------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Fetch Source</p></td>
<td>Boolean</td>
<td><p>Fetch the source of the search document</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Include Fields</p></td>
<td>Array of String</td>
<td><p>List of the field that are included into the document source</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Exclude Fields</p></td>
<td>Array of String</td>
<td><p>List of the field that are excluded from the document source</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Index Response
--------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Forced Refresh</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Id</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Index</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Primary Term</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Result</p></td>
<td>Enumeration, one of:
<ul>
<li><p>CREATED</p></li>
<li><p>UPDATED</p></li>
<li><p>DELETED</p></li>
<li><p>NOT_FOUND</p></li>
<li><p>NOOP</p></li>
</ul></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Seq No</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Shard Id</p></td>
<td>ShardId</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Shard Info</p></td>
<td>ShardInfo</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Type</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Main Response
-------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Available</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Build</p></td>
<td>Build</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Cluster Name</p></td>
<td>ClusterName</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Cluster Uuid</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Node Name</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td>Version</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Build
-----

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Snapshot</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Version
-------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RC</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Alpha</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Beta</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Release</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Open Index Response
-------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Acknowledged</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Shards Acknowledged</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Search Response
---------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aggregations</p></td>
<td>Array of Aggregation</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Clusters</p></td>
<td>Clusters</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Failed Shards</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Hits</p></td>
<td>Array of Array of Array of Any</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Num Reduce Phases</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Profile Results</p></td>
<td>Object</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Scroll Id</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Shard Failures</p></td>
<td>Array of ShardSearchFailure</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Skipped Shards</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Successful Shards</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Suggest</p></td>
<td>Array of Array of Array of Option</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Timed Out</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Took</p></td>
<td>TimeValue</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Total Shards</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Clusters
--------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Skipped</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Successful</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Total</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Shard Search Failure
--------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cause</p></td>
<td>Any</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Option
------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Highlighted</p></td>
<td>Text</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Score</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Text</p></td>
<td>Text</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Time Value
----------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Days</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Days Frac</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Hours</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Hours Frac</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Micros</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Micros Frac</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Millis</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Millis Frac</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Minutes</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Minutes Frac</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Nanos</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Seconds</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Seconds Frac</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>String Rep</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Search Source Configuration
---------------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>From</p></td>
<td>Number</td>
<td><p>Retrieve search result from a certain offset</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Size</p></td>
<td>Number</td>
<td><p>The number of search hits to return</p></td>
<td><p>10</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Timeout</p></td>
<td>Number</td>
<td><p>Time allowed to finish the search operation</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Sort Order</p></td>
<td>Enumeration, one of:
<ul>
<li><p>ASC</p></li>
<li><p>DESC</p></li>
</ul></td>
<td><p>The sort order of search result using default field (_score).</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Sort By Field Name</p></td>
<td>String</td>
<td><p>Field name to sort the search result</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Fetch Source</p></td>
<td>Boolean</td>
<td><p>Fetch the source of the search document</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Include Fields</p></td>
<td>Array of String</td>
<td><p>List of the field that are included into the document source</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Exclude Fields</p></td>
<td>Array of String</td>
<td><p>List of the field that are excluded from the document source</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Profile</p></td>
<td>Boolean</td>
<td><p>Enable the profiling to the execution of search queries</p></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Explain</p></td>
<td>Boolean</td>
<td><p>Explain the execution of search queries</p></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Terminate After</p></td>
<td>Number</td>
<td><p>The maximum number of documents to collect for each shard</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Track Scores</p></td>
<td>Boolean</td>
<td><p>Enable the search source tracking</p></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Track Total Hits</p></td>
<td>Boolean</td>
<td><p>Enable the total hits tracking</p></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td>Boolean</td>
<td><p>Returns a version for each search hit.</p></td>
<td><p>false</p></td>
<td></td>
</tr>
</tbody>
</table>

Update Response
---------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Forced Refresh</p></td>
<td>Boolean</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Get Result</p></td>
<td>Array of Array of Any</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Id</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Primary Term</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Result</p></td>
<td>Enumeration, one of:
<ul>
<li><p>CREATED</p></li>
<li><p>UPDATED</p></li>
<li><p>DELETED</p></li>
<li><p>NOT_FOUND</p></li>
<li><p>NOOP</p></li>
</ul></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Seq No</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Shard Id</p></td>
<td>ShardId</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Shard Info</p></td>
<td>ShardInfo</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Type</p></td>
<td>String</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Version</p></td>
<td>Number</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Match Query
-----------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td>String</td>
<td><p>Restrict the search request to field</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="even">
<td><p>Search String</p></td>
<td>String</td>
<td><p>Search text string</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="odd">
<td><p>Fuzziness</p></td>
<td>Fuzziness</td>
<td><p>Enable fuzzy matching on the match query</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Fuzzy Transpositions</p></td>
<td>Boolean</td>
<td><p>Allow the fuzzy transpositions match</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Prefix Length</p></td>
<td>Number</td>
<td><p>Prefix length option on the match query</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Max Expansions</p></td>
<td>Number</td>
<td><p>Max expansion to control the fuzzy process of the query</p></td>
<td><p>50</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Operator</p></td>
<td>Enumeration, one of:
<ul>
<li><p>OR</p></li>
<li><p>AND</p></li>
</ul></td>
<td><p>Set the match query operator</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Lenient</p></td>
<td>Boolean</td>
<td><p>Ignore exceptions caused by data-type mismatches</p></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Zero Terms Query</p></td>
<td>Enumeration, one of:
<ul>
<li><p>ALL</p></li>
<li><p>NONE</p></li>
</ul></td>
<td><p>Set the zero terms query option</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Cutoff Frequency</p></td>
<td>Number</td>
<td><p>Specify an absolute or relative document frequency</p></td>
<td><p>0.0</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Auto Generate Synonyms Phrase Query</p></td>
<td>Boolean</td>
<td><p>Enable the auto generate synonyms phrase</p></td>
<td><p>false</p></td>
<td></td>
</tr>
</tbody>
</table>

Multi Match Query
-----------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Fields</p></td>
<td>Array of String</td>
<td><p>Restrict the search request to list of field</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="even">
<td><p>Type</p></td>
<td>Enumeration, one of:
<ul>
<li><p>BEST_FIELDS</p></li>
<li><p>CROSS_FIELDS</p></li>
<li><p>MOST_FIELDS</p></li>
<li><p>PHRASE</p></li>
<li><p>PHRASE_PREFIX</p></li>
</ul></td>
<td><p>Type of the multi match query is executed internally</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Tie Breaker</p></td>
<td>Number</td>
<td><p>The tie breaker parameter used to select field in a group of field based on score</p>
<p>0.0 - Take the single best score out of multiple field</p>
<p>1.0 - Add together the scores of the multiple field</p>
<p>0.0 &lt; n &lt; 1.0 - Take the single best score plus tie_breaker multiplied by each of the scores from other matching fields.</p></td>
<td><p>0.0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Minimum Should Match</p></td>
<td>String</td>
<td><p>Set minimum should match with possible value using integer and percentage.</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Search String</p></td>
<td>String</td>
<td><p>Search text string</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="even">
<td><p>Fuzziness</p></td>
<td>Fuzziness</td>
<td><p>Enable fuzzy matching on the match query</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Fuzzy Transpositions</p></td>
<td>Boolean</td>
<td><p>Allow the fuzzy transpositions match</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Prefix Length</p></td>
<td>Number</td>
<td><p>Prefix length option on the match query</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Max Expansions</p></td>
<td>Number</td>
<td><p>Max expansion to control the fuzzy process of the query</p></td>
<td><p>50</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Operator</p></td>
<td>Enumeration, one of:
<ul>
<li><p>OR</p></li>
<li><p>AND</p></li>
</ul></td>
<td><p>Set the match query operator</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Lenient</p></td>
<td>Boolean</td>
<td><p>Ignore exceptions caused by data-type mismatches</p></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Zero Terms Query</p></td>
<td>Enumeration, one of:
<ul>
<li><p>ALL</p></li>
<li><p>NONE</p></li>
</ul></td>
<td><p>Set the zero terms query option</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Cutoff Frequency</p></td>
<td>Number</td>
<td><p>Specify an absolute or relative document frequency</p></td>
<td><p>0.0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Auto Generate Synonyms Phrase Query</p></td>
<td>Boolean</td>
<td><p>Enable the auto generate synonyms phrase</p></td>
<td><p>false</p></td>
<td></td>
</tr>
</tbody>
</table>

Match All Query
---------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Boost</p></td>
<td>Number</td>
<td><p>Sets the boost value of the query</p></td>
<td><p>1.0</p></td>
<td></td>
</tr>
</tbody>
</table>

Match Phrase Query
------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td>String</td>
<td><p>Restrict the search request to field</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="even">
<td><p>Query String</p></td>
<td>String</td>
<td><p>Search text string</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="odd">
<td><p>Boost</p></td>
<td>Number</td>
<td><p>Sets the boost value of the query</p></td>
<td><p>1.0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Analyzer</p></td>
<td>String</td>
<td><p>The analyzer name used to analyze the query string</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Match Phrase Prefix Query
-------------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Max Expansions</p></td>
<td>Number</td>
<td><p>Number of suffixes the last term will be expanded</p></td>
<td><p>50</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Field</p></td>
<td>String</td>
<td><p>Restrict the search request to field</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="odd">
<td><p>Query String</p></td>
<td>String</td>
<td><p>Search text string</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="even">
<td><p>Boost</p></td>
<td>Number</td>
<td><p>Sets the boost value of the query</p></td>
<td><p>1.0</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Analyzer</p></td>
<td>String</td>
<td><p>The analyzer name used to analyze the query string</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Common Terms Query
------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Field Name</p></td>
<td>String</td>
<td><p>Restrict the search request to field</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="even">
<td><p>Query String</p></td>
<td>String</td>
<td><p>Search text string</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="odd">
<td><p>Analyzer</p></td>
<td>String</td>
<td><p>The analyzer name used to analyze the query string</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Boost</p></td>
<td>Number</td>
<td><p>Sets the boost value of the query</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Cutoff Frequency</p></td>
<td>Number</td>
<td><p>Specify an absolute or relative document frequency</p></td>
<td><p>0.0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>High Freq Minimum Should Match</p></td>
<td>String</td>
<td><p>Set minimum should match with possible value using integer and percentage.</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>High Freq Operator</p></td>
<td>Enumeration, one of:
<ul>
<li><p>OR</p></li>
<li><p>AND</p></li>
</ul></td>
<td><p>High frequency query operator</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Low Freq Minimum Should Match</p></td>
<td>String</td>
<td><p>Set minimum should match with possible value using integer and percentage.</p>
<p>@see &lt;a href=&quot;http://google.com&quot;&gt;Minimum Should Matchedit&lt;/a&gt;</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Low Freq Operator</p></td>
<td>Enumeration, one of:
<ul>
<li><p>OR</p></li>
<li><p>AND</p></li>
</ul></td>
<td><p>Low frequency query operator</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Query String Query
------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Allow Leading Wildcard</p></td>
<td>Boolean</td>
<td><p>Allow first wildcard (* or ?) in query string</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Default Field</p></td>
<td>String</td>
<td><p>The default field for query terms if no prefix field is specified.</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Enable Position Increments</p></td>
<td>Boolean</td>
<td><p>Set to true to enable position increments in result queries.</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Escape</p></td>
<td>Boolean</td>
<td><p>Allow escape in query string</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Phrase Slop</p></td>
<td>Number</td>
<td><p>Sets the default slop for phrases. If zero, then exact phrase matches are required.</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Tie Breaker</p></td>
<td>Number</td>
<td><p>The disjunction max tie breaker for multi fields</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Query String</p></td>
<td>String</td>
<td><p>The actual query to be parsed</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="even">
<td><p>Field And Boost</p></td>
<td>Object</td>
<td><p>List of the field name and associated field boost</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Analyzer</p></td>
<td>String</td>
<td><p>The analyzer name used to analyze the query string</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Analyze Wildcard</p></td>
<td>Boolean</td>
<td><p>Analyze the wildcards terms from the query string</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Auto Generate Synonyms Phrase Query</p></td>
<td>Boolean</td>
<td><p>Enable auto generated synonyms phrase queries</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Boost</p></td>
<td>Number</td>
<td><p>Sets the boost value of the query</p></td>
<td><p>1.0</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Default Operator</p></td>
<td>Enumeration, one of:
<ul>
<li><p>OR</p></li>
<li><p>AND</p></li>
</ul></td>
<td><p>The default operator used if no explicit query operator is specified</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Fuzzy Max Expansions</p></td>
<td>Number</td>
<td><p>Controls the number of terms fuzzy queries will expand to.</p></td>
<td><p>50</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Fuzzy Prefix Length</p></td>
<td>Number</td>
<td><p>Set the prefix length for fuzzy queries</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Fuzzy Transpositions</p></td>
<td>Boolean</td>
<td><p>Set to false to disable fuzzy transpositions</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Lenient</p></td>
<td>Boolean</td>
<td><p>If set to true will cause format based failures (like providing text to a numeric field) to be ignored.</p></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Minimum Should Match</p></td>
<td>String</td>
<td><p>Set minimum should match with possible value using integer and percentage.</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Quote Field Suffix</p></td>
<td>String</td>
<td><p>A suffix to append to fields for quoted parts of the query string.</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Simple Query String
-------------------

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 25%" />
<col style="width: 30%" />
<col style="width: 15%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Type</th>
<th>Description</th>
<th>Default Value</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Simple Query String Flag</p></td>
<td>Enumeration, one of:
<ul>
<li><p>ALL</p></li>
<li><p>AND</p></li>
<li><p>ESCAPE</p></li>
<li><p>FUZZY</p></li>
<li><p>NEAR</p></li>
<li><p>NONE</p></li>
<li><p>NOT</p></li>
<li><p>OR</p></li>
<li><p>PHRASE</p></li>
<li><p>PRECEDENCE</p></li>
<li><p>PREFIX</p></li>
<li><p>SLOP</p></li>
<li><p>WHITESPACE</p></li>
</ul></td>
<td><p>Specify which parsing flag should be enabled</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Query String</p></td>
<td>String</td>
<td><p>The actual query to be parsed</p></td>
<td></td>
<td><p>x</p></td>
</tr>
<tr class="odd">
<td><p>Field And Boost</p></td>
<td>Object</td>
<td><p>List of the field name and associated field boost</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Analyzer</p></td>
<td>String</td>
<td><p>The analyzer name used to analyze the query string</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Analyze Wildcard</p></td>
<td>Boolean</td>
<td><p>Analyze the wildcards terms from the query string</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Auto Generate Synonyms Phrase Query</p></td>
<td>Boolean</td>
<td><p>Enable auto generated synonyms phrase queries</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Boost</p></td>
<td>Number</td>
<td><p>Sets the boost value of the query</p></td>
<td><p>1.0</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Default Operator</p></td>
<td>Enumeration, one of:
<ul>
<li><p>OR</p></li>
<li><p>AND</p></li>
</ul></td>
<td><p>The default operator used if no explicit query operator is specified</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Fuzzy Max Expansions</p></td>
<td>Number</td>
<td><p>Controls the number of terms fuzzy queries will expand to.</p></td>
<td><p>50</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Fuzzy Prefix Length</p></td>
<td>Number</td>
<td><p>Set the prefix length for fuzzy queries</p></td>
<td><p>0</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Fuzzy Transpositions</p></td>
<td>Boolean</td>
<td><p>Set to false to disable fuzzy transpositions</p></td>
<td><p>true</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Lenient</p></td>
<td>Boolean</td>
<td><p>If set to true will cause format based failures (like providing text to a numeric field) to be ignored.</p></td>
<td><p>false</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Minimum Should Match</p></td>
<td>String</td>
<td><p>Set minimum should match with possible value using integer and percentage.</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Quote Field Suffix</p></td>
<td>String</td>
<td><p>A suffix to append to fields for quoted parts of the query string.</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

{% include links.html %}
