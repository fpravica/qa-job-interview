# Filip interview

Test automation is made with Postman tool and it is possible to use it with CI/CD pipeline. The requirement is to install Newman program for test execution.

Automatizirani testovi su kreirani za Postman alat i mogu se integrirati sa CI/CD procesom. Potrebno je instalirati program Newman koji izvršava testove.

## Postman Auth
> postman login --with-api-key $POSTMAN_API_KEY


## Command for starting the test run is: / Komanda za pokretanje testova je: 
`newman run filip.postman_collection.json -d filip.input_data.json`


## How to install Newman / Upute za instalaciju

`npm install -g newman`


> https://learning.postman.com/docs/collections/using-newman-cli/installing-running-newman/



### Test collection / suite
The test collection contains mock server data. Also, documentation and the endpoint are available online on two environments:
* test mock server based on this Postman collection


Kolekcija testova sadrži i fiksne odgovore za mock server. Dokumentacija i endpoint su dostupni online:
* test mock server baziran na ovoj Postman kolekciji

## Online documentation
> https://documenter.getpostman.com/view/4544976/2sA2xh1sCK


## Mock development
### Base URL 
> https://16aab6de-01de-4143-a881-07846e94c726.mock.pstmn.io


## CI/CD integracija
### Jenkins
```
pipeline {
  agent any
  tools {nodejs "{nodejs_configured_tool_name}"}
  stages {
    stage('Install Postman CLI') {
      steps {
        sh 'curl -o- "https://dl-cli.pstmn.io/install/linux64.sh" | sh'
      }
    }
    stage('Postman CLI Login') {
      steps {
        sh 'postman login --with-api-key $POSTMAN_API_KEY'
      }
    }
    stage('Running collection') {
      steps {
        sh 'postman collection run "4544976-e2e01c39-2b93-41dd-b0c4-b787b47c1799"'
      }
    }
  }
}
```

