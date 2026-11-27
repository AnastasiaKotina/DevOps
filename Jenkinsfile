pipeline {
    agent any

    stages {
        stage('Подготовка окружения') {
            steps {
                echo 'Запуск установки Docker и клонирования репозиториев...'
                ansiblePlaybook(
                    playbook: 'ansible/firstPlaybook.yml',
                    inventory: 'ansible/inventory/stend1/hosts',
                    installation: 'ansible',
                    tags: 'install,deploy',
                    colorized: true
                )
            }
        }
        stage('Запуск приложений') {
            steps {
                echo 'Запуск микросервисов через docker compose...'
                ansiblePlaybook(
                    playbook: 'ansible/firstPlaybook.yml',
                    inventory: 'ansible/inventory/stend1/hosts',
                    installation: 'ansible',
                    tags: 'start',
                    colorized: true
                )
            }
        }
    }
}