pipeline {
  agent any
  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/antgonz-22/playjenkins.git'
      }
    }

    stage('Build image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }

      }
    }

    stage('Push Image') {
      steps {
        script {
          docker.withRegistry( "" ) {
            dockerImage.push()
          }
        }

      }
    }

    stage('Deploy App') {
      steps {
        kubeconfig(serverUrl: 'https://10.95.0.21:6443', caCertificate: 'LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUMvakNDQWVhZ0F3SUJBZ0lCQURBTkJna3Foa2lHOXcwQkFRc0ZBREFWTVJNd0VRWURWUVFERXdwcmRXSmwKY201bGRHVnpNQjRYRFRJek1ETXdNakl6TVRjMU1sb1hEVE16TURJeU56SXpNVGMxTWxvd0ZURVRNQkVHQTFVRQpBeE1LYTNWaVpYSnVaWFJsY3pDQ0FTSXdEUVlKS29aSWh2Y05BUUVCQlFBRGdnRVBBRENDQVFvQ2dnRUJBTmFJCmpDL2VkYU1ta2ZqYmpqU25ldS8xYU5YeldFdmQ0OTB0d1d0N3l3MWpJSC8yZk0zQ2llNWNqOGVtSnlRMzdFYjMKUCtkcDZqd1BvbGo3UkVLUjROSE5ESlJpc0l2bzJkK2k0NW1hT005ejlTYnh6cVRVRHg2emZDUjBKYWcyRUxJeQo0bkpJR2ZPZTBucXZXYUJyRHhxUWdlSGFBU3hQTVVjTFhIQkNYSmU0bXowc0s3bFJLM2lFS3JtUHh5eFVVakJDCnJBQ09SL0ZLeGh3TU5VbGowZ1dISHNVWFUxN3FYaURJNWFtcFRuSGtyY2pVVG94aUVUMXE0bDl3aExmUEU5azkKRER0UmwyWTExczZNaFdCbXl4TFZid3pkeCtLTmlSWVQzMVpzUXhDWElpVmVhVm1FWTJtYUdWbVJjU0Y3eVQ0LwpldEdmWEF1N1V4SEgyQmtBODhjQ0F3RUFBYU5aTUZjd0RnWURWUjBQQVFIL0JBUURBZ0trTUE4R0ExVWRFd0VCCi93UUZNQU1CQWY4d0hRWURWUjBPQkJZRUZPMVllZXRjcmpBWFkzbHdZSVJHaTQvMmtGcldNQlVHQTFVZEVRUU8KTUF5Q0NtdDFZbVZ5Ym1WMFpYTXdEUVlKS29aSWh2Y05BUUVMQlFBRGdnRUJBQmJIdEg4ZjZUbTdrZUYxck5GbAo0QXAvTDE3aDRNbTR1VDJIdTI0RXRpaUJKeExWekRyOFFYWmxTNFJqQ0dGOVdPcGMvYW5WNkVheFY3bHR2a1NUCldiTlpWQSt6dGZLYzVSSjl1aWxLVU5ZRm5JUmUxZld2ZkRlUExQOVd2S0EzM0FsNXVUV2x5WWtUOTV4QjI5TVUKNTBCdmthblhuK25GdWJWcGNMNDczckZCWElmNXl2WC9FTEo0dDNwaFRaN1dxOFptSVRJdUVRVlV4bnkrV0lTaQoyeTdzTk1hc2d3Y1ZsNW1YQ2FHcnBzcFJDVlhrMDFrSTdhdU1yVFlNUE95UWg4bk90QUVrbUVpblhab3RyNTBTCnNZL3lMem9uc3BiaDJCaDIvN3FXWVdKUGJSaVpNRDVhSkpJVHNKc1VsQ1pkWmxuM3Excmttd0JNQ1ZZQlZDOVEKUldNPQotLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0tCg==', credentialsId: 'kube-admin')
      }
    }

  }
  environment {
    registry = '10.95.0.19:5000/justme/myweb'
    dockerImage = ''
  }
}