pipeline {

    agent any

    parameters {

        choice(
            name: 'ENV',
            choices: ['DEV','QA','STAGE'],
            description: 'Select Environment'
        )

        choice(
            name: 'TEST_TYPE',
            choices: ['Smoke','Sanity','Regression'],
            description: 'Select Test Type'
        )

        string(
            name: 'THREADS',
            defaultValue: '10',
            description: 'User Load'
        )
    }

    stages {

        stage('Display Parameters') {
            steps {
                echo "Environment: ${params.ENV}"
                echo "Test Type: ${params.TEST_TYPE}"
                echo "Threads: ${params.THREADS}"
            }
        }

        stage('Run JMeter Test') {

            steps {

                bat """
                C:\\Users\\HP\\OneDrive\\Desktop\\jmeter\\apache-jmeter-5.6.3\\bin\\jmeter.bat -n ^
                -t scripts\\pipelinejmeter.jmx ^
                -Jthreads=${params.THREADS} ^
                -l results\\result.jtl
                """
            }
        }

         stage('Generate Report') {
    steps {
        bat '''
        if exist reports rmdir /s /q reports

        C:\\Users\\HP\\OneDrive\\Desktop\\jmeter\\apache-jmeter-5.6.3\\bin\\jmeter.bat -g results\\result.jtl -o reports
        '''
    }
}