## Kafka-Helpers
Follow the Wiki instructions to [Setup Kafka CLI Helper Scripts](../../../wiki/Setup-Kafka-CLI-Helper-Scripts).

Sets common properties, like a print/parse key, tab key-separator, string key, etc. Sets the environment properties based on localhost, a *.my-company.com host, or values found in `~/.ccloud/{{ env-prefix }}.config`.

### [__k-functions](__k-functions)
Base helper functions used by `k-*` Kafka Helpers. Not called directly.

### [k-avro-console-consumer](k-avro-console-consumer)
Calls `${CONFLUENT_HOME}/kafka-avro-console-consumer` and sets properties as described above.

###### Usage:
* `k-avro-console-consumer {{ env-prefix | host }} --topic {{ topic-name }} {{ additional-flags }}`
  * `k-avro-console-consumer qa3 --topic event-cool-stuff`
  * `k-avro-console-consumer localhost --topic other-cool-stuff`
  * `k-avro-console-consumer dev-host.my-company.com --topic more-cool-stuff`
 
### [k-avro-console-producer](k-avro-console-producer)
Calls `${CONFLUENT_HOME}/kafka-avro-console-producer` and sets properties as described above. Sets the `--property value.schema.id=` to the latest version, if one is found in the configured schema.registry.

###### Usage:
* `k-avro-console-producer {{ env-prefix | host }} --topic {{ topic-name }} {{ additional-flags }}`
  * `k-avro-console-producer qa --topic event-call-data-adapter --property value.schema='{"name":"AdapterRecordContainer","namespace":"io.company.ada","type":"record","fields":[{"name":"payload","default": null,"type":["null",{"name":"AdapterRecord","type":"record","fields":[{"name":"caller_info_email","default": null,"type":["null","string"]}]}]}]}'`
 
### [k-console-consumer](k-console-consumer)
Calls `${CONFLUENT_HOME}/kafka-console-consumer` and sets properties as described above.

###### Usage:
* `k-console-consumer {{ env-prefix | host }} --topic {{ topic-name }} {{ additional-flags }}`
  * `k-console-consumer dev-host.my-company.com --topic event-other-stuff`
  * `k-console-consumer qa3 --topic event-other-stuff`
 
### [k-console-producer](k-console-producer)
Calls `${CONFLUENT_HOME}/kafka-console-producer` and sets properties as described above.

###### Usage:
* `k-avro-console-producer {{ env-prefix | host }} --topic {{ topic-name }} {{ additional-flags }}`
  * `k-console-producer localhost --topic test-topic-stuff`
  * `k-console-producer dev-host.my-company.com --topic more-topic-stuff`
 
### [k-consumer-groups](k-consumer-groups)
Calls `${CONFLUENT_HOME}/kafka-consumer-groups` and sets properties as described above.

###### Usage:
* `k-consumer-groups {{ env-prefix | host }} {{ additional-flags }}`
  * `k-consumer-groups prod --list`
  * `k-consumer-groups dev-host.my-company.com --list`
 
### [k-copy-schema](k-copy-schema)
Copies schemas from Source Schema Registry to Destination Schema Registry. Defaults to reading from QA and posting to localhost. Run with `--help` for options.

###### Usage:
* `k-copy-schema --topic {{ topic-name }} {{ optional-flags }}`
  * `k-copy-schema --topic event-my-avro-topic`
  * `k-copy-schema --topic event-my-avro-topic --source some.schema.registry:8081 --destination dev-host.my-company.com --type value`

### [k-topics](k-topics)
Calls `${CONFLUENT_HOME}/kafka-topics` and sets properties as described above.

###### Usage:
* `k-topics {{ env-prefix | host }} {{ additional-flags }}`
  * `k-topics qa2 --list`
  * `k-topics dev-host.my-company.com --list`
