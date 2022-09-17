# Prometheus and Graphana for Substrate node 3DPass
To install the tools for this tutorial:
### Prometheus
Download the appropriate precompiled binary for Prometheus from prometheus <a href="https://prometheus.io/download/">download.<a/>

```
Make attention which version you download then modify line below.
gunzip prometheus-2.35.0.darwin-amd64.tar.gz && tar -xvf prometheus-2.35.0.darwin-amd64.tar 
```
change prometheus.yml with prometheus.yml in this repo.
after starting prometheus with command like this 
```./prometheus```
you can then try comand below to check is everything ok.
```curl localhost:9615/metrics```
you will see similar output like 

```
# HELP substrate_block_height Block height info of the chain
# TYPE substrate_block_height gauge
substrate_block_height{status="best"} 7
substrate_block_height{status="finalized"} 4
# HELP substrate_build_info A metric with a constant '1' value labeled by name, version
# TYPE substrate_build_info gauge
substrate_build_info{name="available-vacation-6791",version="2.0.0-4d97032-x86_64-linux-gnu"} 1
# HELP substrate_database_cache_bytes RocksDB cache size in bytes
# TYPE substrate_database_cache_bytes gauge
substrate_database_cache_bytes 0
# HELP substrate_finality_grandpa_precommits_total Total number of GRANDPA precommits cast locally.
# TYPE substrate_finality_grandpa_precommits_total counter
substrate_finality_grandpa_precommits_total 31
# HELP substrate_finality_grandpa_prevotes_total Total number of GRANDPA prevotes cast locally.
# TYPE substrate_finality_grandpa_prevotes_total counter
substrate_finality_grandpa_prevotes_total 31
#
# --snip--
#
```
### Graphana

Navigate to Grafana OSS <a href="https://grafana.com/grafana/download?edition=oss">download</a>.

After you start Grafana, you can navigate to it in a browser.

Open a browser and navigate to the port Grafana uses. By default, the URL is https://localhost:3000/.
Log in using the default user admin and password admin and navigate to the data sources page at localhost:3000/datasources.
You then need to select a Prometheus data source type and specify where Grafana needs to look for it.

The Prometheus port Grafana needs is NOT the one you set in the prometheus.yml file (http://localhost:9615) for where your node is publishing its data.

With both the Substrate node and Prometheus running, configure Grafana to look for Prometheus on its default port http://localhost:9090 or the port you configured if you customized it.

Click Save & Test to ensure that you have the data source set correctly. Now you can configure a new dashboard.

If you would like a dashboard to start here in repo is template that you can Import in Grafana to get basic information about your node:

![image](https://user-images.githubusercontent.com/52631720/190867065-5a019325-ce5b-4298-aa06-dcab2f55e1df.png)
