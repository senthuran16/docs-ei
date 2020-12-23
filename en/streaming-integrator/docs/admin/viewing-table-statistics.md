!!! note
    **This page is still a work in progress!**
    
# Viewing Table Statistics

This displays statistics related to [tables](https://siddhi.io/en/v5.1/docs/query-guide/#table) in the Siddhi applications currently deployed in your WSO2 Streaming Integrator server.

The information displayed in this dashboard is as follows.

![Table statistics dashboard](../images/streaming-integrator-grafana-dashboard/table_statistics_dashboard.png)

## Table Statistics Summary Table
```IMAGE HERE```
This lists all the table operations, defined in all the Siddhi applications in your WSO2 Streaming Integrator server, along with the following for each operation:

!!! note
    When multiple operations are performed on the same table, each operation appears as a separate entry.
   
   - Siddhi application in which, the table is present
   - Name in which, the table has been defined
   - Operation, which was performed on the table
   - Latency of events in the table
   - Throughput of events to/from the table
   
## Latency

```IMAGE```

This shows the latency of each table operation in your WSO2 Streaming Integrator server.

## Throughput

```IMAGE```

This shows the throughput of each table operation in your WSO2 Streaming Integrator server.