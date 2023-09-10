# Importing test data

## Navigating to bulk file directory

```
cd /path/to/data/file/directory
```

### Examples
```
# macOS and Linux
cd ~/Desktop

# Windows
cd C:\Users\Public\Desktop
cd %userprofile%\Desktop
```

## Importing data into local cluster

```
# Without CA certificate validation. This is fine for development clusters, but don't do this in production!
curl -k -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/_bulk --data-binary "@orders.bulk.ndjson"
curl -k -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-01.bulk.ndjson"
curl -k -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-02.bulk.ndjson"
curl -k -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-03.bulk.ndjson"

# With CA certificate validation. The certificate is located at $ES_HOME/config/certs/http_ca.crt
curl --cacert /path/to/http_ca.crt -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/_bulk --data-binary "@orders.bulk.ndjson"
curl --cacert /path/to/http_ca.crt -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-01.bulk.ndjson"
curl --cacert /path/to/http_ca.crt -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-02.bulk.ndjson"
curl --cacert /path/to/http_ca.crt -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-03.bulk.ndjson"
```

## Importing data into Elastic Cloud 
```
curl -H "Content-Type:application/x-ndjson" -XPOST -u elastic:your_password https://elastic-cloud-endpoint.com:9243/_bulk --data-binary "@orders.bulk.ndjson"
curl -H "Content-Type:application/x-ndjson" -XPOST -u elastic:your_password https://elastic-cloud-endpoint.com:9243/_bulk --data-binary "@nginx-access-logs-2020-01.bulk.ndjson"
curl -H "Content-Type:application/x-ndjson" -XPOST -u elastic:your_password https://elastic-cloud-endpoint.com:9243/_bulk --data-binary "@nginx-access-logs-2020-02.bulk.ndjson"
curl -H "Content-Type:application/x-ndjson" -XPOST -u elastic:your_password https://elastic-cloud-endpoint.com:9243/_bulk --data-binary "@nginx-access-logs-2020-03.bulk.ndjson"
