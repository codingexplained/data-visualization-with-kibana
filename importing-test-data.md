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
curl -H "Content-Type: application/x-ndjson" -XPOST http://localhost:9200/_bulk --data-binary "@orders.bulk.ndjson"
curl -H "Content-Type: application/x-ndjson" -XPOST http://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-01.bulk.ndjson"
curl -H "Content-Type: application/x-ndjson" -XPOST http://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-02.bulk.ndjson"
curl -H "Content-Type: application/x-ndjson" -XPOST http://localhost:9200/_bulk --data-binary "@nginx-access-logs-2020-03.bulk.ndjson"
```

## Importing data into Elastic Cloud 
```
curl -H "Content-Type: application/x-ndjson" -XPOST -u elastic:your_password https://elastic-cloud-endpoint.com:9243/_bulk --data-binary "@orders.bulk.ndjson"
curl -H "Content-Type: application/x-ndjson" -XPOST -u elastic:your_password https://elastic-cloud-endpoint.com:9243/_bulk --data-binary "@nginx-access-logs-2020-01.bulk.ndjson"
curl -H "Content-Type: application/x-ndjson" -XPOST -u elastic:your_password https://elastic-cloud-endpoint.com:9243/_bulk --data-binary "@nginx-access-logs-2020-02.bulk.ndjson"
curl -H "Content-Type: application/x-ndjson" -XPOST -u elastic:your_password https://elastic-cloud-endpoint.com:9243/_bulk --data-binary "@nginx-access-logs-2020-03.bulk.ndjson"