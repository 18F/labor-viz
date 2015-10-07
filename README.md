
# Mac install

```
brew install logstash
brew install kibana
brew install elasticsearch
```

https://tock.18f.gov/api/timecards_bulk.csv

Create the elasticsearch index
```
logstash -f `pwd`/logstash.config
```

You should see all the csv data in the console.

If you have already done an import with errors in the config you may need to
delete the logstash db

```
rm ~/.sincedb_*
```


to delete the elasticsearch index

```
curl -XDELETE 'http://localhost:9200/labor'
```
