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
      bat 'dotnet restore D:/jenkins/workspace/test-dotnet/EmployeesApp/EmployeesApp.csproj'
     }
  }
  stage('Clean'){
    steps{
        bat "dotnet clean D:/jenkins/workspace/test-dotnet/EmployeesApp/EmployeesApp.csproj"
     }
   }
   stage('Build'){
   steps{
      bat "dotnet build D:/jenkins/workspace/test-dotnet/EmployeesApp/EmployeesApp.csproj --configuration Release"
    }
 }
 stage('Test: Unit Test'){
   steps {
     bat "dotnet test D:/jenkins/workspace/test-dotnet/EmployeesApp.Tests/EmployeesApp.Tests.csproj"
     }
  }
       
 stage('Test: Integration Test'){
    steps {
       bat "dotnet test D:/jenkins/workspace/test-dotnet/EmployeesApp.IntegrationTests/EmployeesApp.IntegrationTests.csproj"
      }
   }
   stage('Publish'){
     steps{
       bat "dotnet publish D:/jenkins/workspace/test-dotnet/EmployeesApp/EmployeesApp.csproj --output D:/jenkins/workspace/test-dotnet/publishfolder"
      
     }
}
  }
 
}
