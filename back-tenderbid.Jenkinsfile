node(){
	stage('Test own desk') {
		sh label: '', script: 'ip addr'
	}
}
node('node01') {
	stage('Test node01') {
		sh 'ip addr'
	}
	stage('Back-end') {
	    sh 'git init'
	    sh 'git pull https://gitlab.com/aliaksandr_shulha/tenderbid.git master'
	//    sh 'mvn package'
	    sh 'export VAR=`ps -eaf |grep java| grep tender-| awk \' /\'tender\'/ {print $2} \'`;for x in $VAR; do kill $x; done'     // Проверка пидов и находим в нём с подстрокой java и tender- и потом берём второй столбец где номера пидов и записываем в вар переменную.
	    sh 'echo vvvv $VAR' 
		sh 'ls'
		//sh 'source /var/workspace/buildBack/job.sh'
		 script{
                   withEnv(['JENKINS_NODE_COOKIE=dontkill']) {   // обёртка что б дженкинс не закрывал дерево 
                       sh "nohup java -jar /var/workspace/buildBack/target/tender-0.0.3-SNAPSHOT.jar >logback.log 2>warn.log &"  
                   }
               }
		//sh 'nohup java -Dhudson.util.ProcessTree.disable=true -jar /var/workspace/buildBack/target/tender-0.0.3-SNAPSHOT.jar >logback.log 2>warn.log &'
		sh 'ps -eaf'
	//	sh 'ps -eaf |grep java| grep tender-| awk \' /\'tender\'/ {print $2}'
		sh 'echo "Back-end started!"'
	    
	}
    
}