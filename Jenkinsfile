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
     stage('Restore packages'){
   steps{
      bat 'dotnet restore C:/Jenkins/workspace/emp-05/EmployeesApp/EmployeesApp.csproj'
     }
  }
  stage('Clean'){
    steps{
        bat "dotnet clean C:/Jenkins/workspace/emp-05/EmployeesApp/EmployeesApp.csproj"
     }
   }
   stage('Build'){
   steps{
      bat "dotnet build C:/Jenkins/workspace/emp-05/EmployeesApp/EmployeesApp.csproj --configuration Release"
    }
 }
  stage('Sonar'){
       steps{
        bat 'SonarScanner.MSBuild.exe begin /k:"Employee-demo-test" /d:sonar.host.url="http://localhost:9000" /d:sonar.login="63914d3b5f2b1cf5002a052a5c306a7ee82cd946"'
        bat 'MsBuild.exe /t:Rebuild'
        bat 'SonarScanner.MSBuild.exe end /d:sonar.login="63914d3b5f2b1cf5002a052a5c306a7ee82cd946"'
       }
     }
 stage('Test: Unit Test'){
   steps {
     bat "dotnet test C:/Jenkins/workspace/emp-05//EmployeesApp.Tests/EmployeesApp.Tests.csproj"
     }
  }
       
 stage('Test: Integration Test'){
    steps {
       bat "dotnet test C:/Jenkins/workspace/emp-05/EmployeesApp.IntegrationTests/EmployeesApp.IntegrationTests.csproj"
      }
   }
   stage('Publish'){
     steps{
       bat "dotnet publish C:/Jenkins/workspace/emp-05/EmployeesApp/EmployeesApp.csproj --output C:/Publish/empapp"
      
     }
     }
    
  }
 
}
