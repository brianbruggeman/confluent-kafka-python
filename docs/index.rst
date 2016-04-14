Welcome to Confluent's Apache Kafka Python client documentation
===============================================================

Indices and tables
==================

* :ref:`genindex`

:mod:`confluent_kafka` --- Confluent's Apache Kafka Python client
*****************************************************************

.. automodule:: confluent_kafka
   :synopsis: Confluent's Apache Kafka Python client.
   :members:


Configuration
=============
Configuration of producer and consumer instances is performed by
providing a dict of configuration properties to the instance constructor, e.g.::

  conf = {'bootstrap.servers': 'mybroker.com',
          'group.id': 'mygroup', 'session.timeout.ms': 6000,
          'default.topic.config': {'auto.offset.reset': 'smallest'}}
  consumer = confluent_kafka.Consumer(**conf)

The supported configuration values are dictated by the underlying
librdkafka C library. For the full range of configuration properties
please consult librdkafka's documentation:
https://github.com/edenhill/librdkafka/blob/master/CONFIGURATION.md

The Python bindings also provide some additional configuration properties:

* ``default.topic.config``: value is a dict of topic-level configuration
  properties that are applied to all used topics for the instance.

* ``delivery_callback`` (**Producer**): value is a Python function reference
  that is called once for each produced message to indicate the final
  delivery result (success or failure).
  This property may also be set per-message by passing ``callback=somefunc``
  to the confluent_kafka.Producer.produce() function.


  