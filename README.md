# parquet-cli

Visit the [releases page](https://github.com/CBIIT/parquet-cli/releases) to download builds for [parquet-java/parquet-cli](https://github.com/apache/parquet-java/tree/master/parquet-cli). All releases are built using the `local` profile, producing standalone Uber JAR files that can be executed with `java -jar` without requiring a Hadoop environment (on non-Windows systems).

## Getting Started

### Convert a csv file to a parquet file

Download `parquet-cli`
```sh
curl -L -O https://github.com/CBIIT/parquet-cli/releases/download/1.15.0/parquet-cli-1.15.0.jar
```

Convert `input.csv` to `output.parquet`
```sh
java -jar parquet-cli-1.15.0.jar convert-csv input.csv -o output.parquet
```


### Troubleshooting

#### Security Manager
You may encounter errors and warnings regarding Security Manager being disabled. Note that Security Manager will be completely removed in Java 24.

1. Create a policy file called `parquet.policy`
```
grant {
    permission java.util.PropertyPermission "*", "read,write";
    permission java.security.AllPermission;
};
```

2. Run the jar with the Security Manager activated, using the specified policy
```sh
java -Djava.security.manager -Djava.security.policy=parquet.policy -jar parquet-cli-1.15.0.jar convert-csv input.csv -o output.parquet
```



#### Hadoop on Windows
To run this on Windows, you will need hadoop/winutils

1. Clone https://github.com/cdarlint/winutils
```sh 
git clone https://github.com/cdarlint/winutils C:\Programs\winutils
```
2. Set the HADOOP_HOME environment variable to the location of the winutils/hadoop-3.3.6 folder
```sh
$env:HADOOP_HOME = "C:\Programs\winutils\hadoop-3.3.6"
# or permanently: [Environment]::SetEnvironmentVariable("HADOOP_HOME", "C:\Programs\winutils\hadoop-3.3.6", "User")
```
5. Run the jar
```sh
java -jar parquet-cli-1.15.0.jar convert-csv input.csv -o output.parquet
```
