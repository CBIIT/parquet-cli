# parquet-cli

Visit the [releases page](https://github.com/CBIIT/parquet-cli/releases) to download builds for [parquet-java/parquet-cli](https://github.com/apache/parquet-java/tree/master/parquet-cli). All releases are built using the `local` profile, producing standalone Uber JAR files that can be executed with `java -jar` without requiring a Hadoop environment.

## Getting Started

### Convert a csv file to a parquet file

Download `parquet -cli`
```sh
curl -L -O https://github.com/CBIIT/parquet-cli/releases/download/1.14.4/parquet-cli-1.14.4.jar
```

Convert `input.csv` to `output.parquet`
```sh
java -jar parquet-cli-1.14.4.jar convert-csv input.csv -o output.parquet
```
