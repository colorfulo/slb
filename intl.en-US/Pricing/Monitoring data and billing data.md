# Monitoring data and billing data {#concept_dzd_4hs_wdb .concept}

Server Load Balancer provides a function that monitors the inbound and outbound traffic, number of connections, and more. You can view real-time monitoring data on the console. You are charged for the network traffic consumed by the Server Load Balancer instance. However, monitoring data is different from billing data, which is caused by factors as described in the following table.

|Factors|Monitoring Data|Billing data|
|:------|:--------------|:-----------|
|Calculation methods| Monitoring data is collected every one minute by the Server Load Balancer system, and reported to the cloud monitoring system. Then, the cloud monitoring system calculates the average value of all collected data in each 15 minutes.

 The displayed network traffic data is the calculated average value.

 | Billing data is collected at the same granularity and the Server Load Balancer system reports the accumulated value in each hour to the billing system.

 The monitoring data is the calculated average value, but the billing data is the accumulation value. These two data sets are incomparable because they are calculated and generated differently.

 |
|Latency|Server Load Balancer provides real-time monitoring data. However, a short delay may inevitably occur in the data collection, calculation, and display process. Although this delay is almost insignificant, it can create a certain degree of discrepancy between the monitoring and billing data.|Billing data tolerates a maximum delay of three hours. For example, billing data generated between 01:00-02:00 is normally reported to the billing system at 03:00, but is allowed to be reported to the billing system at 05:00. As a result, there are differences between billing data and monitoring data.|
|Purpose|The purpose of monitoring is to help users observe if the instance is in abnormal conditions. If so, users can resolve the problem as soon as possible. Observe whether there is abnormal situation in the instance, so as to take specific measures to solve the problem.|The purpose of billing is to generate bills. Monitoring data cannot be used as the billing data.|

