---
title: "How to Instantiate AWS ES Connection using python elasticsearch_dsl"
description: "import boto3, os from requests_aws4auth import AWS4Auth from elasticsearch import RequestsHttpConnection from elasticsearch_dsl import connections def…"
original_date: 2020-02-05T04:49:12-08:00
---

![](/assets/img/posts/how-to-instantiate-aws-es-connection-using-python-elasticsearch_dsl/1-B_LkCNig-0qvI0q-QihDKw.jpeg)
```
import boto3, os
from requests_aws4auth import AWS4Auth
from elasticsearch import RequestsHttpConnection
from elasticsearch_dsl import connections
def init_connection():
service = "es"
region = "us-west-2"
credentials = boto3.Session().get_credentials()
awsauth = AWS4Auth(
credentials.access_key,
credentials.secret_key,
region,
service,
session_token=credentials.token,
)
connections.configure(
default={
"hosts": [{"host": os.environ["ES_ENDPOINT"], "port": 443,}],
"http_auth": awsauth,
"use_ssl": True,
"verify_certs": True,
"connection_class": RequestsHttpConnection,
}
)
connections.get_connection()  # Checks if conn already exists if not creates a new one
```

Checkout the gist here: <https://gist.github.com/asthinasthi/9ceb20159edc70df0997ca2a79361548>

### Saving a document

1. Tweet Document/Entity

```
from elasticsearch_dsl import Document, Date, Text, Integer, Nested
class Tweet(Document):
  class Index:
     name = "index-tweet"

  created_at = Date(default_timezone="UTC")
  body = Text()
  favorites = Integer()
  retweets = Integer()
```

2. Save a tweet/Persist Tweet

```
init_connection() # See above
tweet = Tweet(body="My first tweet", favorites=5, retweets=10)
tweet.save()
```

Check your ES for all docs in **index-tweet** You should see this document
