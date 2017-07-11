node('EPBYMINW1766') {
    stage('Preparation') {
        echo "==> Preparation stage begins."
        git branch: 'amaslakou', url: 'https://github.com/MNT-Lab/mntlab-pipeline.git'
    }
    
    stage('Build') {
        echo "==> Building stage begins."
        sh '/opt/gradle/gradle-4.0.1/bin/gradle build'
    }

    stage('Test'){
        echo "==> Testing stage begins."
        parallel (
                phase1: {echo "==> Unit Test  stage begins."; sh '/opt/gradle/gradle-4.0.1/bin/gradle test' },
                phase2: {echo "==> Jacoco Test stage begins."; sh '/opt/gradle/gradle-4.0.1/bin/gradle jacocoTestReport' },
                phase3: {echo "==> Cucumber Test stage begins."; sh '/opt/gradle/gradle-4.0.1/bin/gradle cucumber' }
        )
    }
}
