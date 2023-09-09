# Adding index templates

We will need to add the following two index templates before ingesting some test data into Elasticsearch. 
Run the following two queries within Kibana's Console tool.

## Index template for the access logs dataset 
```
PUT /_index_template/access-logs
{
  "index_patterns": ["access-logs*"],
  "template": {
    "settings": {
      "index.mapping.coerce": false
    },
    "mappings": {
      "dynamic": false,
      "properties": {
        "@timestamp": { "type": "date" },
        "message": { "type": "text" },
        "event.dataset": { "type": "keyword" },
        "hour_of_day": { "type": "short" },
        "http.request.method": { "type": "keyword" },
        "http.request.referrer": { "type": "keyword" },
        "http.response.body.bytes": { "type": "long" },
        "http.response.status_code": { "type": "long" },
        "http.version": { "type": "keyword" },
        "url.fragment": { "type": "keyword" },
        "url.path": { "type": "keyword" },
        "url.query": { "type": "keyword" },
        "url.scheme": { "type": "keyword" },
        "url.username": { "type": "keyword" },
        "url.original": {
          "type": "keyword",
          "fields": {
            "text": {
              "type": "text",
              "norms": false
            }
          }
        },
        "client.address": { "type": "keyword" },
        "client.ip": { "type": "ip" },
        "client.geo.city_name": { "type": "keyword" },
        "client.geo.continent_name": { "type": "keyword" },
        "client.geo.country_iso_code": { "type": "keyword" },
        "client.geo.country_name": { "type": "keyword" },
        "client.geo.location": { "type": "geo_point" },
        "client.geo.region_iso_code": { "type": "keyword" },
        "client.geo.region_name": { "type": "keyword" },
        "user_agent.device.name": { "type": "keyword" },
        "user_agent.name": { "type": "keyword" },
        "user_agent.version": { "type": "keyword" },
        "user_agent.original": {
          "type": "keyword",
          "fields": {
            "text": {
              "type": "text",
              "norms": false
            }
          }
        },
        "user_agent.os.version": { "type": "keyword" },
        "user_agent.os.name": {
          "type": "keyword",
          "fields": {
            "text": {
              "type": "text",
              "norms": false
            }
          }
        },
        "user_agent.os.full": {
          "type": "keyword",
          "fields": {
            "text": {
              "type": "text",
              "norms": false
            }
          }
        }
      }
    }
  }
}
```

## Index template for the orders dataset
```
PUT /_index_template/orders
{
  "index_patterns": ["orders*"],
  "template": {
    "settings": {
      "index.mapping.coerce": false
    },
    "mappings": {
      "dynamic": false,
      "properties": {
        "@timestamp": { "type": "date" },
        "id": { "type": "keyword" },
        "product": {
          "properties": {
            "id": { "type": "keyword" },
            "name": { "type": "keyword" },
            "price": { "type": "float" },
            "brand": { "type": "keyword" },
            "category": { "type": "keyword" }
          }
        },
        "customer.id": { "type": "keyword" },
        "customer.age": { "type": "short" },
        "customer.gender": { "type": "keyword" },
        "customer.name": { "type": "keyword" },
        "customer.email": { "type": "keyword" },
        "channel": { "type": "keyword" },
        "store": { "type": "keyword" },
        "salesman.id": { "type": "keyword" },
        "salesman.name": { "type": "keyword" },
        "discount": { "type": "float" },
        "total": { "type": "float" }
      }
    }
  }
}
```
