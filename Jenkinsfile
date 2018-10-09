!groovy
@Library('latest-stable') _
//Use latest tag to reference most recently deployed version of shared libraries
//@Library('latest-stable') _
//Use latest-stable to reference latest-1 version of shared libraries
dynamicVersionPattern = "timestamp"
def date = new Date()
def TIMESTAMP = date.format("yyyyMMddHHmm")
def verVar="2019.02.70"+TIMESTAMP+"-SNAPSHOT"
mavenPipelinePlugin {
 //  ait = "xxxxx"
//   spk = "ABCD"
   repo = "VProfile"
  
// Artifactory
    artifactoryRepo = "maven"
  
// Workspace Cleanup
   cleanWorkspace = true
  
// Build Parameters
    buildParameters = "clean install"
    pipelineBuildToolName = "apache-maven-3.0.5"
    pipelineJdkToolName = "JDK18"
   buildDefinitionFile = "pom.xml"
  
// Specify known versions of JDK and Maven if needed       
     // javaLocation = "/efs/jdk/1.8/bin/"   
     // mavenLocation = "/efs/apache/maven/3.1.0/"
    mavenLocation= "/efs/dist/maven/core/3.1.1/common"
	javalocation= "/efs/dist/oracle/jdk/1.8/exec"
// Unit Test
   executeUnitTest = true
   unitTestFramework = "junit"
   unitTestFailFast = true
   junitTestResultPath = "**/target/surefire-reports/*.xml"
  
// Package & Publish
    executeCreateArtifact = true 
    executePublishArtifact = true
  
// FILE_SPEC   
    publishMode = "FILE_SPEC"          
    publishFileList = [        
    ["groupId": "com.baml.gbamcch.ichgbam_build", "artifactId": "gbam-ich-ear", "version": verVar, "artifactLocation":"gbam-ich-ear/target/*.ear"],        
   // ["groupId": "com.baml.test.demo_java", "artifactId": "Sample_Java_Plugin", "version":"2.13-SNAPSHOT", "artifactLocation":"target/**/*.jar"]    
    ]
  
// Code Scan
   executeCodeScan = true
    pipelineScanServerToolName = "Enterprise_Sonar_1"
    pipelineScanClientToolName = "sonar"
   scanFailFast = true
   sonarPropertyFile = "sonar-project.properties"
        binariesPath=""
  
// prependPath & appendPath
    prependPath = "/sample/test/prepend1:/sample/test/prepend2"        
    appendPath = "/sample/test/append1:/sample/test/append2"
  
// DG Email Notification
      //  notificationDG = "test@bankofamerica.com","test@baml.com"
// Dev Deploy 
        executeDeploy=false 
        deliveryPipelineJobName="ETASCONB/maven_Delivery/feature-deployment" 
