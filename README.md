
# Mac install

```
brew install logstash
brew install kibana
brew install elasticsearch
```

Download the bulk data here: 
https://tock.18f.gov/api/timecards_bulk.csv

Modify the logstash.config file to have the absolute path to the csv file in your local environment.

Start elasticsearch
```
elasticsearch --config=/usr/local/opt/elasticsearch/config/elasticsearch.yml
```

Create the elasticsearch index
```
logstash -f `pwd`/logstash.config
```

You should see all the csv data in the console.

Start kibana
```
kibana
```

Configure an index pattern in kibana: navigate to http://localhost.com:5601, enter "labor" in the "index name or pattern" box, select "start_time" in the drop down menu.

![Kibana Screenshot](/assets/ConfigureIndexPattern.png)

## Error Recovery

If you have already done an import with errors in the config you may need to
delete the logstash db

```
rm ~/.sincedb_*
```

And delete the elasticsearch index

```
curl -XDELETE 'http://localhost:9200/labor'
```
