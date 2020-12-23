!!! note
    **This page is still a work in progress!**
    
# Viewing Query Statistics

This displays statistics related to [sinks](https://siddhi.io/en/v5.1/docs/query-guide/#sink) in the Siddhi applications currently deployed in your WSO2 Streaming Integrator server.

The information displayed in this dashboard is as follows.

![Sink statistics dashboard](../images/streaming-integrator-grafana-dashboard/sink_statistics_dashboard.png)

## Sink Mapper Statistics Summary Table
```IMAGE HERE```
This lists all the sink mappers, from all the Siddhi applications in your WSO2 Streaming Integrator server, along with the following for each sink mapper:

   - Siddhi application in which, the sink mapper is present
   - Stream to which, the sink mapper is attached to
   - Type of the sink to which, the mapper is attached to
   - Type of the mapper
   - Latency of events in the mapper
   - Throughput of events to the sink to which, the mapper is attached to
   
## Sink Throughput

```IMAGE```

This shows the throughput of each sink mapper in your WSO2 Streaming Integrator server.

## Sink Mapper Latency

```IMAGE```

This shows the latency of each sink mapper in your WSO2 Streaming Integrator server.