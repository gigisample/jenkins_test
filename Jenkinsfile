pipeline {
    agent any
    
    // ▼ ここでビルドパラメータを定義します ▼
    parameters {
        // 1) 文字列パラメータ
        string(
            name: 'GREETING', 
            defaultValue: 'Hello', 
            description: '挨拶メッセージを入力してください'
        )
        
        // 2) 選択式パラメータ
        choice(
            name: 'ENVIRONMENT', 
            choices: ['dev', 'staging', 'prod'],
            description: 'デプロイ先の環境を選択してください'
        )
        
        // 3) ブールパラメータ (ON/OFF)
        booleanParam(
            name: 'SKIP_TESTS', 
            defaultValue: false, 
            description: 'テストをスキップする場合はチェックを入れてください'
        )
        
        // 4) マルチラインテキストパラメータ
        text(
            name: 'RELEASE_NOTES', 
            defaultValue: 'ここにリリースノートを記述してください', 
            description: '複数行のテキストを入力できます'
        )
    }
    
    stages {
        stage('Print Greeting') {
            steps {
                echo "Your greeting is: ${params.GREETING}"
            }
        }
        
        stage('Test or skip') {
            when {
                // SKIP_TESTS が true ならこのステージをスキップする
                expression {
                    return !params.SKIP_TESTS
                }
            }
            steps {
                echo 'Running tests...'
                // 実際のテストコマンドやスクリプトを置き換えてください
                sh 'echo "Tests passed!"'
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying to environment: ${params.ENVIRONMENT}"
                echo "Release notes:\n${params.RELEASE_NOTES}"
                // 実際のデプロイ処理 (shellスクリプト、Ansible、kubectl等) をここに追加
            }
        }
    }
}
