# Prometheus Time Range script

## Understanding the script flow
This script based on the input parameters runs the set of Prometheus queries, capturing the time taken, status and output of the PromQL queries executed over a specified time range i.e.
15 days

### Collection of queries
1. Individual queries: Set of queries, capturing the container resource data (cpu and memory) by pod with `imageOwners` and `imageWorkloads` queries over 15days
2. Grouped queries: Set of queries which group the container data by pod owner and workload on the fly over 15 days
3. Grouped queries over 5 day windows: This collection uses the same set of grouped queries, instead divides the 15 days time range in three windows each corresponding to 5 days time range

### Prerequisites:
OpenShift cluster

### Execute the script on OpenShift as:
./local_monitoring_demo.sh

```
Usage: ./local_monitoring_demo.sh [-n namespace] [-c container] [-q query_set] [-s start timestamp] [-e end timestamp]
n = namespace (default=openshift-cloud-controller-manager-operator)
c = container (default=config-sync-controllers)
q = query set to be used (individual[default], grouped, grouped_5days) 
s = start timestamp
e = end timestamp
```