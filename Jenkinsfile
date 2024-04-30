pipeline {
    agent any
    
    stages {
        stage('Monitor RAM Stats') {
            steps {
                script {
                    // Execute shell command to fetch RAM stats and capture the output
                    def memoryStats = sh(script: 'free -m', returnStdout: true).trim()
                    
                    // Create a table format for RAM stats
                    def ramTable = "```\nMemory Stats:\n${memoryStats}\n```"
                    
                    // Send RAM stats to a Slack channel in a table format
                    slackSend channel: 'deployment-team',
                              color: 'good',
                              message: ramTable,
                              teamDomain: 'digital-lync-tec',
                              tokenCredentialId: 'slack',
                              username: 'jenkins-bot'
                }
            }
        }
        
        stage('Monitor Disk Stats') {
            steps {
                script {
                    // Execute shell command to fetch disk stats and capture the output
                    def diskStats = sh(script: 'df -h', returnStdout: true).trim()
                    
                    // Create a table format for disk stats
                    def diskTable = "```\nDisk Stats:\n${diskStats}\n```"
                    
                    // Send disk stats to a Slack channel in a table format
                    slackSend channel: 'deployment-team',
                              color: 'good',
                              message: diskTable,
                              teamDomain: 'digital-lync-tec',
                              tokenCredentialId: 'slack',
                              username: 'jenkins-bot'
                }
            }
        }
    }
}
