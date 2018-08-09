node('master') {

	def MVNHOME = tool 'Maven'
	
stage ('checkout code'){
	checkout scm
}
	
stage ('build'){
	sh "${MVNHOME}/bin/mvn clean install"
}

}
