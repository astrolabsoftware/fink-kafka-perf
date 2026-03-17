# Kafka performances

If you observe bad performances when using the [fink-client]() to get data from the Livestream or the Data Transfer service, it might be a slow connection with the Fink Kafka servers. This repository offers tools to measure and report the consuming performances:

```bash
# For LSST
./fink_kafka_perf -survey lsst

# For ZTF
./fink_kafka_perf -survey ztf
```

To check existing options:

```bash
finkenv ❯ ./fink_kafka_perf -h

fink_kafka_perf is a wrapper around Kafka performance measurement tools specialised for Fink. It is meant to inspect slow connections to the Fink Kafka servers.

  Find more information on Fink at https://fink-broker.org

Usage: fink_kafka_perf [OPTIONS]

Options:
  -h          Show this help
  -survey     Survey name (ztf, lsst)
  -topic      Kafka topic name. Optional. Default topics for performance are:
                - ZTF:  fink_sso_ztf_candidates_ztf
	        - LSST: fink_sn_near_galaxy_candidate_lsst
              Note that any Livestream topics or Data Transfer topic works.
  -nmessages  Number of messages to poll. Optional. Default is 1500.
  -timeout    Timeout in milliseconds. Optional. Default is 20000.
  -kVersion   Kafka version to use. Optional. Default is 2.8.1.

Examples:
  ./fink_kafka_perf -survey lsst
  ./fink_kafka_perf -survey ztf

```
