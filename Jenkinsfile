def APP_Proj='EmployeesApp/EmployeesApp.csproj'
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
      bat "dotnet build C:/Jenkins/workspace/emp-05/EmployeesApp/EmployeesApp.csproj --configuration Release"
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
