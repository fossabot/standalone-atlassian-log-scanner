Sick of the time it takes to scan your Atlassian log files using the Log Analyser?
 Enter SALSA!
# Standalone Atlassian Log Scanner/Analyser
This is a standalone version of the Log Scanner (Hercules) that is built into Jira, Confluence, Bitbucket, Bamboo, Crowd and Fisheye/Crucible. 
The aim is to increase the speed of scanning dramatically compared to executing through the interface and allow automated scanning of log files in a support system.

## Performance
A 3MB Log File took the following duration:
* Support Tools Log Analyser: 6 minutes 14 seconds
* Standalone Log Scanner (sequential): 1 minute 48 seconds
* Standalone Log Scanner (parrallel): 37 seconds

*That's an over 70% improvement when sequentially run and a 90% improvement when run in parrallel*

## How it Works
The following steps are followed:
1. (if it doesn't already exist) Download the definition file from the Atlassian website
2. Parses the XML into JAXB Objects
3. Generates Regular Expression List
4. Reads the Log File
5. Runs Regular Expressions on each Log Line (either sequentially or in parrallel)
6. Prints out the URL of all errors that have been found in the system (distinct)

## Compiling
Run the following command to build the project into a JAR file:
`mvn package`

## Usage
Execute the following on your command line (CMD or Bash) and leave the "stream" parameter out if you would like it to run sequentially (which is much less demanding)
`java -jar logscanner.jar "jira-core" "atlassian-jira.log" "stream"`

## Download
You can download a pre-compiled binary from the [releases page](https://github.com/jackgraves/standalone-atlassian-log-scanner/releases)

## Example
### Built-in Tool

![Support Tools Output](example/example_output_supporttools.png)

### Standalone Tool

![SALSA Output](example/example_output_standalone.png)

## Next Steps
- [ ] Write Jira plugin to automatically scan incoming support log files
