node('master') {

	def MVNHOME = tool 'Maven'
	
stage ('checkout code'){
	checkout scm
}
	
stage ('build'){
	bat "${MVNHOME}/bin/mvn clean install"
}

}
