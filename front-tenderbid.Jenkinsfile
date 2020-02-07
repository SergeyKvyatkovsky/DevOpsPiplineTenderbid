node(){
	stage('Test own desk') {
		sh label: '', script: 'ip addr'
	}
}
node('node01') {
	stage('Test node01') {
		sh 'ip addr'
	}
	stage('Front-end') {
	    sh 'git remote -v'
		sh 'git pull originf master'
		sh 'git checkout master'
		sh 'ls'
		sh 'npm install;npm run build'
		sh 'nohup npm start > logfron.log &'
		sh 'echo "Front started!"'
	}
}