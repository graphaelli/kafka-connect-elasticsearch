Configuration Options
---------------------

``connection.url``
  The URL to connect to Elasticsearch.

  * Type: string
  * Default: ""
  * Importance: high

``type.name``
  The type to use for each index.

  * Type: string
  * Default: ""
  * Importance: high

``key.ignore``
  Whether to ignore the key during indexing. When this is set to true, only the value from the message will be written to Elasticsearch.Note that this is a global config that applies to all topics. If this is set to true, Use ``topic.key.ignore`` to config for different topics. This value will be overridden by the per topic configuration.

  * Type: boolean
  * Default: false
  * Importance: high

``batch.size``
  The number of requests to process as a batch when writing to Elasticsearch.

  * Type: int
  * Default: 2000
  * Importance: medium

``max.in.flight.requests``
  The maximum number of incomplete batches each task will send before blocking. Note that if this is set to be greater than 1 and there are failed sends, there is a risk of message re-ordering due to retries

  * Type: int
  * Default: 5
  * Importance: medium

``flush.timeout.ms``
  The timeout when flushing data to Elasticsearch.

  * Type: long
  * Default: 10000
  * Importance: low

``linger.ms``
  The task groups together any records that arrive in between request transmissions into a single batched request. Normally this occurs only under load when records arrive faster than they can be sent out. However in some circumstances the tasks may want to reduce the number of requests even under moderate load. This setting accomplishes this by adding a small amount of artificial delay. Rather than immediately sending out a record the task will wait for up to the given delay to allow other records to be sent so that the sends can be batched together.

  * Type: long
  * Default: 1
  * Importance: low

``max.buffered.records``
  Approximately the max number of records each task will buffer. This config controls the memory usage for each task. When the number of buffered records is larger than this value, the partitions assigned to this task will be paused.

  * Type: long
  * Default: 20000
  * Importance: low

``max.retries``
  The max allowed number of retries. Allowing retries will potentially change the ordering of records.

  * Type: int
  * Default: 5
  * Importance: low

``retry.backoff.ms``
  The amount of time to wait before attempting to retry a failed batch. This avoids repeatedly sending requests in a tight loop under some failure scenarios.

  * Type: long
  * Default: 100
  * Importance: low

``schema.ignore``
  Whether to ignore schemas during indexing. When this is set to true, the schema in ``SinkRecord`` will be ignored and Elasticsearch will infer the mapping from data. Note that this is a global config that applies to all topics.Use ``topic.schema.ignore`` to config for different topics. This value will be overridden by the per topic configuration.

  * Type: boolean
  * Default: false
  * Importance: low

``topic.index.map``
  The map between Kafka topics and Elasticsearch indices.

  * Type: list
  * Default: []
  * Importance: low

``topic.key.ignore``
  A list of topics to ignore key when indexing. In case that the key for a topic can be null, you should include the topic in this config in order to generate a valid document id.

  * Type: list
  * Default: []
  * Importance: low

``topic.schema.ignore``
  A list of topics to ignore schema.

  * Type: list
  * Default: []
  * Importance: low