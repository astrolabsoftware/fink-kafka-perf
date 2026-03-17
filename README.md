# Kafka performances

This repository offers tools to measure and report performances when polling Fink Kafka servers (used in the Data Transfer, Livestream, and Xmatch services). Simply use:


```bash
# For LSST with default topic
./fink_kafka_perf -survey lsst

# For LSST with any Data Transfer topic
./fink_kafka_perf -survey lsst -topic ftransfer_lsst_2026-03-17_244593

# For ZTF with default topic
./fink_kafka_perf -survey ztf
```

The first time you run it, it will download Kafka. Logs will be appended in a file `fink_kafka_output_<SURVEY>.log`. To check all existing options:

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
  -nmessages  Number of messages to poll. Optional. Default is 5000.
  -timeout    Timeout in milliseconds. Optional. Default is 20000.
  -kVersion   Kafka version to use. Optional. Default is 2.8.1.

Examples:
  ./fink_kafka_perf -survey lsst   # using default topic
  ./fink_kafka_perf -survey ztf    # using default topic

  # Using Data Transfer topic
  ./fink_kafka_perf -survey lsst -topic ftransfer_lsst_2026-03-17_244593
```

## Fink  
