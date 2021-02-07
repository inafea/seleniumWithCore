def APP_PROJ='EmployeesApp/EmployeesApp.csproj'
def UNITTEST_PROJ='EmployeesApp.Tests/EmployeesApp.Tests.csproj'
def INTEGRATIONTEST_PROJ='EmployeesApp.IntegrationTests/EmployeesApp.IntegrationTests.csproj'
pipeline{
    agent {label 'test-win'}
    
    environment {
        dotnet ='C:\\Program Files (x86)\\dotnet\\'
        }
        
    triggers {
        pollSCM 'H * * * *'
    }  
    stages{
     stage('Checkout') {
      steps {
     git 'https://github.com/inafea/seleniumWithCore'
      }
     }
     stage('Restore packages & clean'){
   steps{
      bat 'dotnet restore C:/Jenkins/workspace/emp-05/EmployeesApp/EmployeesApp.csproj'
      bat "dotnet clean C:/Jenkins/workspace/emp-05/EmployeesApp/EmployeesApp.csproj"
     }
  }
  
   stage('Build'){
   steps{
      bat "dotnet build ${WORKSPACE}/${APP_PROJ} --configuration Release"
    }
 }
  
 stage('Test: Unit Test'){
   steps {
     bat "dotnet test ${WORKSPACE}/${UNITTEST_PROJ}"
     }
  }
       
 stage('Test: Integration Test'){
    steps {
       bat "dotnet test ${WORKSPACE}/${INTEGRATIONTEST_PROJ}"
      }
   }
   stage('Publish'){
     steps{
       bat "dotnet publish ${WORKSPACE}/${APP_PROJ} --output C:/Publish/empapp"
      
     }
     }
    
  }
 
}
