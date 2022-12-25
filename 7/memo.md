学習用ElasticSearch + kibana
===
# linux-bindmount + es で権限不足
`es-data` ディレクトリを chmod 777
# サンプルデータ入れる
...

# クエリを打つ環境
curlだと面倒なので、kibanaのdev-tool を使う、見やすいしわかりやすいから
表記もこれに合わせる

# どんなクエリが飛んだかを読む
slowlog という形で読める  
https://www.elastic.co/guide/en/elasticsearch/reference/7.17/index-modules-slowlog.html

```
curl -XPUT "http://localhost:9200/_all/_settings" -H "content-type: application/json" -d'
{
    "index.search.slowlog.threshold.query.debug": "0s"
}'
```
デフォルトは -1 で一切表示されない。kibana使いで allでやってしまうと、他のindexもログにわんさか出てくるので、目的のindexごとに指定するのが良い。`_all` で指定せずに

