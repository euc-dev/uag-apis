---
layout: page
title: Sample API Usage Reference
hide:
  #- navigation
  - toc
---

**Example of Using the Generated Access Token for REST API Calls**

To utilize the monitoring API, users must include the access_token as a Bearer token in the Authorization Header. Below is a cURL snippet illustrating the procedure for calling the monitor API:

*Request:*

```shell
curl -s -i -k -X 'GET' \
  'https://localhost:9443/rest/v1/monitor/stats' \
  -H 'accept: application/xml' \
  -H 'Authorization: Bearer <access-token>'
```

*Response:*

```xml
HTTP/1.1 200 OK
… (other response headers)

<?xml version="1.0" encoding="UTF-8"?>
<accessPointStatusAndStats>
   <sessionCount>19</sessionCount>
   <authenticatedSessionCount>0</authenticatedSessionCount>
   <authenticatedViewSessionCount>0</authenticatedViewSessionCount>
   <openIncomingConnectionCount>0</openIncomingConnectionCount>
   <highWaterMark>19</highWaterMark>
   <timeStamp>1744123552933</timeStamp>
   <date>Tue Apr 08 14:45:52 UTC 2025</date>
   <overAllStatus>
      <status>RUNNING</status>
   </overAllStatus>
   <authentication name="eas">
      <status>
         <reason>Reachable</reason>
         <status>RUNNING</status>
      </status>
      <successLogins>3</successLogins>
      <failedLogins>2</failedLogins>
   </authentication>
   <authentication name="cas">
      <status>
         <reason>Reachable</reason>
         <status>RUNNING</status>
      </status>
      <successLogins>0</successLogins>
      <failedLogins>0</failedLogins>
   </authentication>
   <viewEdgeServiceStats>
      <backendStatus>
         <reason>Reachable</reason>
         <status>RUNNING</status>
      </backendStatus>
      <edgeServiceSessionStats>
         <identifier>VIEW</identifier>
         <totalSessions>6</totalSessions>
         <highWaterMarkOfSessions>6</highWaterMarkOfSessions>
         <authenticatedSessions>0</authenticatedSessions>
         <unauthenticatedSessions>6</unauthenticatedSessions>
         <failedLoginAttempts>1</failedLoginAttempts>
         <userCount>0</userCount>
      </edgeServiceSessionStats>
      <edgeServiceStatus>
         <status>RUNNING</status>
      </edgeServiceStatus>
      <xmlapiUnrecognizedRequestsCount>0</xmlapiUnrecognizedRequestsCount>
      <protocol name="pcoip">
         <status>
            <status>DISABLED</status>
         </status>
         <sessions>0</sessions>
         <maxSessions>0</maxSessions>
         <unrecognizedRequestsCount>0</unrecognizedRequestsCount>
      </protocol>
      <protocol name="Tunnel,RDP">
         <status>
            <reason>Reachable</reason>
            <status>RUNNING</status>
         </status>
         <sessions>0</sessions>
         <maxSessions>0</maxSessions>
         <unrecognizedRequestsCount>0</unrecognizedRequestsCount>
      </protocol>
      <protocol name="blast">
         <status>
            <reason>Reachable</reason>
            <status>RUNNING</status>
         </status>
         <sessions>0</sessions>
         <maxSessions>0</maxSessions>
         <unrecognizedRequestsCount>0</unrecognizedRequestsCount>
      </protocol>
      <protocol name="utserver">
         <status>
            <reason>Reachable</reason>
            <status>RUNNING</status>
         </status>
         <sessions>0</sessions>
         <maxSessions>0</maxSessions>
         <unrecognizedRequestsCount>0</unrecognizedRequestsCount>
      </protocol>
   </viewEdgeServiceStats>
   <edgeServiceSessionStats>
      <identifier>Total</identifier>
      <totalSessions>6</totalSessions>
      <highWaterMarkOfSessions>0</highWaterMarkOfSessions>
      <authenticatedSessions>0</authenticatedSessions>
      <unauthenticatedSessions>6</unauthenticatedSessions>
      <failedLoginAttempts>1</failedLoginAttempts>
      <userCount>0</userCount>
   </edgeServiceSessionStats>
   <applianceStats>
      <cpuCores>2</cpuCores>
      <totalCpuLoadPercent>0</totalCpuLoadPercent>
      <cpuRunQueue>0</cpuRunQueue>
      <memoryPageInRate>0.0</memoryPageInRate>
      <memoryPageOutRate>25.78</memoryPageOutRate>
      <totalMemoryMb>3650</totalMemoryMb>
      <freeMemoryMb>985</freeMemoryMb>
      <usedDiskSpacePercentage>39.0</usedDiskSpacePercentage>
      <diskLatency>0.64</diskLatency>
      <diskQueueLength>0.0</diskQueueLength>
      <usedHeapMemoryPercentage>1.0</usedHeapMemoryPercentage>
      <cpuDetailedStats>
         <idle>92.59</idle>
         <ioWait>0.0</ioWait>
         <irq>0.1</irq>
         <nice>0.0</nice>
         <softIrq>0.2</softIrq>
         <steal>0.0</steal>
         <system>3.2</system>
         <user>3.9</user>
      </cpuDetailedStats>
   </applianceStats>
   <uagVersion>25.03</uagVersion>
   <uptimeInMins>1110</uptimeInMins>
   <toolsInfo>
      <vmToolsStatus>Available</vmToolsStatus>
      <vmToolsVersion>12.1.5.39265 (build-20735119)</vmToolsVersion>
      <timeOfRecord>1744084193167</timeOfRecord>
   </toolsInfo>
</accessPointStatusAndStats>
```
