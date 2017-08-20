# Configuration of ELK Stack

The Documentation explains configuring ELK stack with FileBeat For Clustered Environment.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

>- Elasticsearch
>- Logstash
>- Kibana
>- FileBeat

### Log data flow diagram
![ELK](https://github.com/kprasad99/myfirstrepo/blob/master/images/elk.png)

### Installation and Configuration

#### Elasticsearch

 1.  Download Elasticsearch zip.
````
https://www.elastic.co/downloads/elasticsearch
 ````
 2. Extract zip.
 3. cd to bin directory.
````
cd elasticsearch-{version}\bin
````
 4. Start Elasticsearch application.
 5. Verify Elasticsearch application starts successfully.
 Browse for url `http://localhost:9200/` you should get output something similar to below json data.
```json
 {
   "name" : "DQKs7b9",
   "cluster_name" : "elasticsearch",
   "cluster_uuid" : "Nn6ZBMzvQgyDy-YoO8a17w",
   "version" : {
      "number" : "5.5.1",
      "build_hash" : "19c13d0",
      "build_date" : "2017-07-18T20:44:24.823Z",
      "build_snapshot" : false,
      "lucene_version" : "6.6.0"
   },
  "tagline" : "You Know, for Search"
 }
 ```
#### Logstash
 1. Download logstash zip.
 > https://www.elastic.co/downloads/logstash
 
 2.  Extract the zip file.
 3. Go to bin directory.
 4. create logstash.conf file with below configuration.
 ```config
input {
  beats {
    # The port to listen on for filebeat connections.
    port => 5044
    # The IP address to listen for filebeat connections.
    host => "0.0.0.0"
  }
}
output {
  elasticsearch {
    hosts => localhost
  }
}
 ```
 5. Start the logstash application with previous configuration file created.
 ```sh
 logstash.bat -f logstash.conf
 ```
 6. Verify application is started successfully.
 Browse for `http://localhost:9600` you should get ouput something similar to below json data.
 ```json
 {
   "host":"kp-pc",
   "version":"5.5.1",
   "http_address":"127.0.0.1:9600",
   "id":"f10e43c8-d310-4b83-bf10-d653b9840375",
   "name":"kp-pc",
   "build_date":"2017-07-18T21:15:04Z",
   "build_sha":"4267263f454d5cfeb85d98cec4925c6aa28d230b",
   "build_snapshot":false
}
 ```
 > **Note:** Since we have configured filebeat as input make sure in log 5044 is started. 

#### Filebeat

 1. Download filebeat zip.
 > https://www.elastic.co/downloads/beats/filebeat

 2. Extract zip file.
 3. Create `filebeat.yml` file.
 ```yml
 filebeat.prospectors:
 4. input_type: log
      paths:
         - D:\log\*.log
 output.logstash:
     hosts: ["localhost:5044"]
 ``` 
> **Note:** If you are reusing `filebeat.full.yml` make sure you comment out `output.elasticsearch:` section.

 5. Start filebeat application.
 ```sh
 filebeat.exe -e -c filebeat.yml -d "Publish"
 ```

 6. On Successful start you shall see data being written in log.
> libbeat.logstash.publish.write_bytes=61768 libbeat.logstash.published_and_acked_events=1434 

## Authors

* **Karthik Prasad** - *Initial work* - [kprasad99](https://github.com/kprasad99)


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
