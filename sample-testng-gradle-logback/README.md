# sample-testng-gradle-logback

Your guide to run the first Java + TestNG test with reporting to Zebrunner.

## Prerequisites

Before you can start performing Java automation testing with Selenium, you would need to:
- A Java Development Kit (JDK), version 8 or higher - for example [AdoptOpenJDK](https://adoptopenjdk.net/)
- [Gradle](https://gradle.org/install/) build tool
- [Chrome](https://www.google.com/chrome/) browser for running Selenium Web tests

## Configuration
### _Step 1: Basic project setup_
Clone the Zebrunner's [samples](https://github.com/zebrunner/java-agent-samples) repository and navigate to the code directory as shown below:

```
git clone https://github.com/zebrunner/java-agent-samples.git
cd java-agent-samples/sample-testng-gradle-logback
```

### _Step 2: Setup your authentication_
In Zebrunner:
- Navigate to "Account and profile" section by clicking on the User icon from the top right side;
- Click on "API Tokens" tab;
- Press "Token" button, create a token and copy it before closing the dialog (you won't be able to see the token later).

### _Step 3: Select project for your launches_
In Zebrunner:
- Click on "Projects" dropdown from the top left side;
- Select "View all Projects";
- Find out a project where you would like to see your launches and copy its `KEY`.

> You need to be an Admin of the workspace to have the ability to create projects

### _Step 4: Configure your agent.properties file_
The `agent.properties` file holds all the required configuration to enable reporting of your tests on Zebrunner.

- Open the file located inside `java-agent-samples/sample-testng-gradle-logback/src/test/resources` directory of cloned repository;
- Update the `agent.properties` config file with:
  - `reporting.server.access-token` with `token` from step #2;
  - `reporting.project-key` with `KEY` from step #3 (if not defined, `DEF` will be used by default);
  - `reporting.server.hostname` with your Zebrunner workspace;
  - `reporting.run.display-name` with launch name you wish to see in Zebrunner.

```
reporting.enabled=true
reporting.project-key=<project_key>
reporting.server.hostname=https://<workspace>.zebrunner.com/
reporting.server.access-token=<token>
reporting.run.display-name=<display_name>
```

### _Step 5: Run sample test_
Run a sample test with Zebrunner reporting:
```
gradle test -Psuite=basic.xml
```

Refer to the [documentation](https://zebrunner.com/documentation/reporting/carina-testng/) for more information.