# Vulnado - Intentionally Vulnerable Java Application

This application and exercises will take you through some of the OWASP top 10 Vulnerabilities and how to prevent them.

## Up and running

1. Install Docker for [MacOS](https://hub.docker.com/editions/community/docker-ce-desktop-mac) or [Windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows). You'll need to create a Docker account if you don't already have one.
2. `git clone https://github.com/kapilalgo/jenkins-sonar-sample.git`
3. `cd vulnado`
4. `docker-compose up`
5. Open a browser and navigate to the client to make sure it's working: [http://localhost:1337](http://localhost:1337)
6. Then back in your terminal verify you have connection to your API server: `nc -vz localhost 8080`

## Sonar Scan
1. Run scan using command `/opt/apache-maven-3.9.6/bin/mvn clean verify sonar:sonar \ 
  -Dsonar.organization=your_organization_name \
  -Dsonar.projectKey=your_project_key \
  -Dsonar.host.url=https://sonarcloud.io \
  -Dsonar.login=your_secret_token`
2. Instead of maven absolution path if source is done only mvn can be used
3. In sonarcloud dashboard --> Main Branch --> Summary --> choose Overall Code to view coverage

### Sonar test coverage requirements
1. Unit Test cases should be present in test folder
2. Junit Plugin should be present in pom.xml
3. Jacoco Plugin should be present in pom.xml
4. Jacoco report execution goal should be present in build tag in pom.xml
5. Maven "verify" goal should be run while running sonar analysis

## Architecture

The docker network created by `docker-compose` maps pretty well to a multi-tier architecture where a web server is publicly available and there are other network resources like a database and internal site that are not publicly available.

![](exercises/assets/arch.png)

## Exercises

* [SQL Injection](exercises/01-sql-injection.md)
* [XSS - Cross Site Scripting](exercises/02-xss.md)
* [SSRF - Server Side Request Forgery](exercises/03-ssrf.md)
* [RCE - Remote Code Execution & Reverse Shell](exercises/04-rce-reverse-shell.md)

