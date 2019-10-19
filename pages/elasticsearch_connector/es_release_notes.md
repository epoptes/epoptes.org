---
title: Elasticsearch Connector Release Notes
keywords: sample
sidebar: elasticsearch_connector_sidebar
permalink: es_release_notes.html
folder: elasticsearch_connector
---
The Anypoint Connector for Elasticsearch lets you connect to the
Elasticsearch from mule flows. The connector exposes convenient methods
for exploiting the capabilities of Elasticsearch.

The connector executes API calls targeting Elasticsearch’s REST API
depending on you configuration. The API calls use an JSON
request/response over HTTP and HTTPS connection.

Read through this user guide to understand how to set up and configure a
basic flow using the connector. Track feature additions, compatibility,
limitations, and API version updates using the Docker Connector Release
Notes. Review the connector operations and see how they work by
reviewing the Technical Reference alongside the Demo Applications.

[Elasticsearch Connector User
Guide](elasticsearch-connector-user-manual.adoc)

Elasticsearch connector v1.0.0 - August 22, 2018
================================================

Version V1.0 Compatibility
--------------------------

<table>
<col width="50%" />
<col width="50%" />
<thead>
<tr class="header">
<th align="left">Software</th>
<th align="left">Version</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Mule Runtime</p></td>
<td align="left"><p>4.1.1</p></td>
</tr>
<tr class="even">
<td align="left"><p>Elasticsearch</p></td>
<td align="left"><p>6.2.4</p></td>
</tr>
</tbody>
</table>

Features
--------

1.  TLS support

2.  Supports multiple APIs of Elasticsearch like indices, documents and
    search.

    -   Create Index API

    -   Delete Index API

    -   Open Index API

    -   Close Index API

    -   Index API

    -   Get API

    -   Delete API

    -   Update API

    -   Bulk API

    -   Search API

    -   Search Scroll API

    -   Clear Scroll API

    -   Info API

Support Resources
-----------------

-   Learn how to [Install Anypoint
    Connectors](https://docs.mulesoft.com/anypoint-studio/v/7.1/add-modules-in-studio-to).

-   Access MuleSoft’ [Forum](http://forum.mulesoft.org/mulesoft) to pose
    questions and get help from Mule’s broad community of users.

-   To access MuleSoft’s expert support team,
    [subscribe](http://www.mulesoft.com/mule-esb-subscription) to Mule
    ESB Enterprise and log in to MuleSoft’s [Customer
    Portal](http://www.mulesoft.com/support-login).

{% include links.html %}