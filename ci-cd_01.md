### 1) Установить Jenkins 
- https://www.jenkins.io/doc/book/installing/linux/#debian-stable
- https://www.jenkins.io/doc/book/installing/linux/#unlocking-jenkins
### 2) Создать элементарный декларативный пайплайн по шагам
#### 2.1. Создать item
<img width="284" height="342" alt="image" src="https://github.com/user-attachments/assets/6c1d1767-e983-4ff6-b1f4-c5a96018d0b2" />

<img width="1049" height="680" alt="image" src="https://github.com/user-attachments/assets/bef7271a-5797-4aac-b355-1731f3eb3437" />

#### 2.2 Перейти к пункту Pipeline
<img width="1426" height="749" alt="image" src="https://github.com/user-attachments/assets/5b09d323-1a36-4d60-845d-0da6ffaae36b" />

Definition оставить как есть - "Pipeline script"

#### 2.3 Написать пайплайн
```jenkinsfile
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "${BUILD_NUMBER} run stage 'building the project'..."
            }
        }
        
        stage('Test') {
            steps {
                echo "${BUILD_NUMBER} run stage 'tests'..."
            }
        }
        
        stage('Deploy') {
            steps {
                echo "${BUILD_NUMBER} run stage start deploying the application..."
            }
        }
    }
}
```
Нажать "Save" внизу
#### 2.4 Запустить пайплайн
<img width="277" height="359" alt="image" src="https://github.com/user-attachments/assets/ed3de0eb-efe0-44f1-a30f-f49d7abfd24b" />

слева внизу будут отображаться все запущенные и прошедшие сборки

<img width="274" height="199" alt="image" src="https://github.com/user-attachments/assets/270bec9b-1299-4d38-979d-040774f0b654" />

если нажать на красный или зеленый кружок - можно попасть в логи сборки (там видно, если она упала и почему)
<img width="849" height="647" alt="image" src="https://github.com/user-attachments/assets/2ff6fc26-b78c-4ffe-b322-2ff9002ec922" />

### 3) Создать пайплайн для сборки и тестирования Python-проекта
```jenkinsfile
pipeline {
    agent any
    
    environment {
        BASE_DIR="/var/lib/jenkins/apps"
        PRJ_NAME="py-app"
        GIT_URL="https://github.com/AnastasiyaGapochkina01/py-jenkins-app.git"
    }
    
    stages {
        stage('Clone repo'){
            steps{
                sh """
                    mkdir -p ${env.BASE_DIR} || true
                    git clone ${env.GIT_URL} ${env.BASE_DIR}/${env.PRJ_NAME}  || true
                    echo -ls ${env.BASE_DIR}/${env.PRJ_NAME}
                """
            }
        }
        stage('Setup Environment') {
            steps {
                sh """
                    cd ${env.BASE_DIR}/${env.PRJ_NAME}
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -e .
                    pip install -r requirements.txt
                """
            }
        }
        stage('Security Scan') {
            steps {
                sh """
                    cd ${env.BASE_DIR}/${env.PRJ_NAME}
                    . venv/bin/activate
                    bandit -r app/ -f json -o bandit_results.json || true
                """
            }
        }
        stage('Run Unit Tests') {
            steps {
                sh """
                    cd ${env.BASE_DIR}/${env.PRJ_NAME}
                    . venv/bin/activate
                    PYTHONPATH=src pytest -v tests/ --junitxml=test-results.xml
                """
            }
        }
        stage('Package Application') {
            steps {
                sh """
                    cd ${env.BASE_DIR}/${env.PRJ_NAME}
                    . venv/bin/activate
                    python setup.py sdist bdist_wheel
                    ls -la dist/ || echo "Папка dist не существует"
                """
                //archiveArtifacts artifacts: 'dist/python_calculator_app-0.1.0.tar.gz', fingerprint: true
            }
        }
    }
}
```
