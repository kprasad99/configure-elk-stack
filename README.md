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
````
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
 ````
#### Logstash
#### [step1] Download logstash zip.

## Authors

* **Karthik Prasad** - *Initial work* - [kprasad99](https://github.com/kprasad99)


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
