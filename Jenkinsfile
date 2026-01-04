pipeline{
    agent any
        stage('checkout')
        {
            scm checkout
        }
    
    stages{
        stage('BUild')
        {
            steps{
                echo 'Building brooo'
            }
        }
        stage('Test')
        {
            steps{
                echo 'Testing broo'
            }
        }
        stage('Deploy')
        {
            steps{
                echo 'Deploying broo'
            }
        }
    }
}