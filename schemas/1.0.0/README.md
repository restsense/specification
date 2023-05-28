# RESTSense DataModel v1.0.0
The RESTSense model has three main entities: resources, metrics and traces.They are described below.

## Resources
Resources are the entities that report traces and metrics. In the context of Cloud architectures, a resource can be understood as one of the cloud services that are part of the architecture. A resource must be identifiable within the network that communicates the services, so certain attributes must be known, as shown in the [Resource schema](Resource.json).

## Traces
A trace is an abstract entity that groups a set of transactions (spans) based on a complex propagation mechanism, which carries values between logically associated execution units. Thus, a trace is composed of a set of spans that share the same context. 

On the other hand, a span is nothing more than a specific operation carried out between a source and a destination within a time window and with attributes that allow it to be uniquely identified. Every span must contain temporal information, context information that identifies the transaction and metadata that provides additional information, as shown in the [Trace schema](Trace.json)

## Metrics
Metrics contains general information such as the name of the metric, a description, the unit of measurement and the type of metric (cumulative sum, histogram, counter, etc.), as well as metadata such as those collected in the traces. Depending on the type of metric, the data collected vary, however they maintain a common structure to some extent, differing only in the attributes.

All collected data are interpreted as points in a time series, so they must contain both the temporal information and the point value that allows them to be represented. In addition, each point contains attributes that vary according to the specific metric to be collected, and therefore depend on the implementation to be carried out when implementing the service.

Additionally, metrics, if any, must correlate with the traces on a time basis. To this end, each of the points keeps a reference to the transactions performed in the corresponding time space. The metrics model is formalized through the [Metric schema](Metric.json)
