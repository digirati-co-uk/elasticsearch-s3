# Elasticsearch-s3

Dockerfile for ElasticSearch 5.5.0 with [`s3-repository`](https://www.elastic.co/guide/en/elasticsearch/plugins/5.5/repository-s3.html) plugin.

## Docker Image

Docker image is available: `digirati/elasticsearch-s3:5.5.0`

## Repository-S3 Usage

```bash
# Create repository "my_repo"
curl -XPUT --data '{ "type": "s3", "settings": { "bucket": "my-bucket", "base_path": "backups/elastic" } }'  http://127.0.0.1:9200/_snapshot/my_repo

# Create snapshot "first" in "my_repo". Optionally append ?wait_for_completion=true
curl -XPUT http://127.0.0.1:9200/_snapshot/my_repo/first

# View all repos
curl http://127.0.0.1:9200/_snapshot/_all

# View "my_repo"
curl http://127.0.0.1:9200/_snapshot/my_repo
```

More available options, including required S3 permissions in updated docs: https://www.elastic.co/guide/en/elasticsearch/reference/8.3/repository-s3.html