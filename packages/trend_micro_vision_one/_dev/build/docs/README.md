# Trend Micro Vision One

## Overview

The [Trend Micro Vision One](https://www.trendmicro.com/en_in/business/products/detection-response.html) integration allows you to monitor Alert, Audit, and Detection activity. Trend Micro Vision One refers to the ability to do detection and response across email, endpoints, servers, cloud workloads, and networks via a single Trend Micro Vision One platform or the managed Trend Micro Vision One service.

Use the Trend Micro Vision One integration to collects and parses data from the REST APIs. Then visualize that data in Kibana.

## Data streams

The Trend Micro Vision One integration collects logs for three types of events: Alert, Audit, and Detection.

**Alert** Displays information about workbench alerts. See more details in the doc [here](https://automation.trendmicro.com/xdr/api-v3#tag/Workbench/paths/~1v3.0~1workbench~1alerts/get).

**Audit** Displays log entries that match the specified search criteria. See more details in the doc [here](https://automation.trendmicro.com/xdr/api-v3#tag/Audit-Logs).

**Detection** Displays search results from the Detection Data source. See more details in the doc [here](https://automation.trendmicro.com/xdr/api-v3#tag/Search/paths/~1v3.0~1search~1detections/get).

## Requirements

You need Elasticsearch for storing and searching your data and Kibana for visualizing and managing it. You can use our hosted Elasticsearch Service on Elastic Cloud, which is recommended, or self-manage the Elastic Stack on your hardware.

This module has been tested against `Trend Micro Vision One API version 3.0`.

**Note:** The authentication token generated by a user expires one year after being generated.

## Setup

### To collect data from Trend Micro Vision One APIs, the user must have API Token. To create an API token follow the below steps:

1. Log on to the Trend Micro Vision One console.
2. Go to **Administration -> User Accounts**.
![Trend Micro Vision One console](../img/trend-micro-vision-one-console.png)
3. Click on the account name having appropriate API access permission to generate an API token.
![Trend Micro Vision One generate API token ](../img/trend-micro-vision-one-api-token-generate.png)
4. Copy the Authentication token.

## Logs Reference

### alert

This is the `alert` dataset.

#### Example

{{event "alert"}}

{{fields "alert"}}

### audit

This is the `audit` dataset.

#### Example

{{event "audit"}}

{{fields "audit"}}

### detection

This is the `detection` dataset.

#### Example

{{event "detection"}}

{{fields "detection"}}
