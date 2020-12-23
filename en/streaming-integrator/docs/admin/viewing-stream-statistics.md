!!! note
    **This page is still a work in progress!**
    
# Viewing Stream Statistics

This displays statistics related to [streams](https://siddhi.io/en/v5.1/docs/query-guide/#stream) in the Siddhi applications currently deployed in your WSO2 Streaming Integrator server.

The information displayed in this dashboard is as follows.

![Stream statistics dashboard](../images/streaming-integrator-grafana-dashboard/stream_statistics_dashboard.png)

This dashboard displays the following information for your current WSO2 Streaming Integrator deployment:

- The throughput of each stream
- The total stream count
- A graphical representation of the throughput of each stream over time.

## Filtering stream statistics - Move this to a common place

- If you want to view stream statistics only for a specific time interval, you can select a pre-defined time interval or define a custom time interval in the following field. This field is is located in the top right of the dashboard.

    ![Monitoring SI Performance](../images/monitoring-si-performance/select-time-interval.png)

- If you want to view statistics relating to streams in a one or more selected Streaming Integrator servers in your Streaming Integrator deployment, expand the **Instance** field and select the required instance(s).

    The stream statistics of all the servers 

- If you want to view statistics relating to streams in one or more selected Siddhi appli