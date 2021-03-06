<a name="top" />

[**HOME**](Home) » [**SNOWPLOW SETUP GUIDE**](Setting-up-Snowplow) » [Step 3: Setting up Enrich](Setting-up-enrich) » Step 3.1: Setting up EmrEtlRunner

![Enrichment](https://d3i6fms1cm1j0i.cloudfront.net/github-wiki/images/snowplow-architecture-3-enrichment.png) 

Snowplow [EmrEtlRunner][emr-etl-runner] is an application that parses the log files generated by your Snowplow collector and

1. **Cleans up the data** into a format that is easier to parse / analyse
2. **Enriches the data** (e.g. infers the location of the visitor from his / her IP address and infers the search engine keywords from the query string)
3. **Stores that cleaned, enriched data in S3**

This guide covers how to setup EmrEtlRunner (including scheduling it) so that your event data is automatically fetched from the collector logs, processed and updated in your cleaned data store on S3. It is divided into six sections:

1. [Installation](1-Installing-EmrEtlRunner). You need to install EmrEtlRunner on your own server. It will interact with Amazon Elastic MapReduce and S3 via the Amazon API
2. [Usage](2-Using-EmrEtlRunner). How to use EmrEtlRunner at the command line, to instruct it to process data from your collector
3. [Scheduling](3-Scheduling-EmrEtlRunner). How to schedule the tool so that you always have an up to date set of cleaned, enriched data available for analysis
4. [Self-hosting Spark Enrich](4-Self-hosting-Spark-Enrich). (Optional step)
5. [Configuring enrichments](5-Configuring-enrichments). How to configure enrichments such as referer parsing and IP lookups
6. [Configuring shredding](6-Configuring-shredding). How to configure Snowplow to shred custom self-describing events (also called unstructured events) and contexts ready for loading into dedicated tables in Redshift

» Read more about 

- [The enrichment process](The-enrichment-process)
- [Events and contexts](Events-and-contexts)
- [Batch pipeline steps](Batch-pipeline-steps) (block dataflow diagram)

To start with, [install][installation] EmrEtlRunner.

**Note**: We recommend running all Snowplow AWS operations through an IAM user with the bare minimum permissions required to run Snowplow. Please see our [IAM user setup page](IAM-setup) for more information on doing this.


[installation]: 1-Installing-EmrEtlRunner
[usage]: 2-Using-EmrEtlRunner
[schedule]: 3-Scheduling-EmrEtlRunner
[emr-etl-runner]: https://github.com/snowplow/snowplow/tree/master/3-enrich/emr-etl-runner
