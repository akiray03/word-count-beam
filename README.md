word-count-beam
===============

https://beam.apache.org/get-started/quickstart-java/

Run Direct
----------

```bash
$ mvn compile exec:java -Dexec.mainClass=org.apache.beam.examples.WordCount \
     -Dexec.args="--inputFile=pom.xml --output=counts" -Pdirect-runner
```

Run Dataflow
------------

```bash
$ export GCLOUD_PROJECT="<your-project-name>"
$ export GCLOUD_STORAGE="<your-google-storage>"

$ gcloud auth application-default login

$ mvn compile exec:java -Dexec.mainClass=org.apache.beam.examples.WordCount \
    -Dexec.args="--runner=DataflowRunner \
                 --project=$GCLOUD_PROJECT \
                 --gcpTempLocation=gs://$GCLOUD_STORAGE/tmp \
                 --inputFile=gs://apache-beam-samples/shakespeare/* \
                 --output=gs://$GCLOUD_STORAGE/counts" \
     -Pdataflow-runner
```
