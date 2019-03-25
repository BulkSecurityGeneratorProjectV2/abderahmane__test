#!/usr/bin/env groovy

node {
    stage('checkout') {
        checkout scm
    }
    stage('check java') {
        sh "java -version"
    }
    
    stage('clean') {
        sh "chmod +x mvnw"
        sh "./mvnw clean"
    }
    
    stage('install tools') {
		sh "./mvnw com.github.eirslett:frontend-maven-plugin:install-node-and-npm -DnodeVersion=v8.12.0 -DnpmVersion=6.4.1"
	}

	stage('npm install') {
		sh "./mvnw com.github.eirslett:frontend-maven-plugin:npm"
	}
	
	stage('generate war') {
        sh "./mvnw install -DskipTests"
    }
    
    stage('copy war') {
        sh "cp target/*.war /home/abda/wars/"
    }
}
