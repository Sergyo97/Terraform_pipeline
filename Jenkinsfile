pipeline {

  agent any

  environment {
    ARM_SUBSCRIPTION_ID='0f47e60a-7149-4a18-8076-8813c555a778'
    ARM_CLIENT_ID='46c04485-42e0-4d52-9d9a-895434bf7c66'
    ARM_CLIENT_SECRET='ffe6bba9-cd31-4279-8a4b-c78aefb37d02'
    ARM_TENANT_ID='50640584-2a40-4216-a84b-9b3ee0f3f6cf'
    ARM_ENVIRONMENT='public'
  }

  stages {
    stage('Check') {
      steps {
        checkout scm
        dir("ResourceGroup"){
          sh 'terraform init'
          sh 'terraform plan'
          sh 'terraform apply -auto-approve'
        }
      }
    }

    stage('Environment') {
      steps {
        dir("TerraformLAB"){
          sh 'terraform init'
          sh 'terraform plan'
          sh 'terraform apply -auto-approve'
        }
      }
    }
  } 
}
