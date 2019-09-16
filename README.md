# UdG-CAES-sample-static-code-analysis
A dockerized way to easily perform a static code analysis using https://www.sonarqube.org

## Usage

Make sure you have the required dependencies installed on your system:

* [Docker](https://docs.docker.com/)
* [Docker Compose](https://docs.docker.com/compose/)

Clone this repository

```
git clone git@github.com:victormartingarcia/UdG-CAES-sample-static-code-analysis.git
```

Go to base repo folder and run the docker containers

```
cd Udg-CAES-sample-static-code-analysis
docker-compose up
```

That should have started SonarQube UI under URL address [http://127.0.0.1:9000](http://127.0.0.1:9000). You can access with default credentials `admin/admin`

Create a "token" on SonarQube UI and write it down.

In order to perform a static code analysis for a maven java project:

```
mvn clean install

mvn sonar:sonar \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=<SONARQUBE_GENERATED_token> \
  -Dsonar.sources=src/main \
  -Dsonar.sourceEncoding=UTF-8 \
  -Dsonar.language=java \
  -Dsonar.tests=src/test \
  -Dsonar.junit.reportsPath=target/surefire-reports \
  -Dsonar.surefire.reportsPath=target/surefire-reports \
  -Dsonar.jacoco.reportPath=target/jacoco.exec \
  -Dsonar.binaries=target/classes \
  -Dsonar.java.coveragePlugin=jacoco \
  -Dsonar.verbose=true

```
