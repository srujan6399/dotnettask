node{
    stage("checkout"){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/asquarezone/CSharpAssesment.git']]])
    }
    stage("build"){
        bat "msbuild Assignments/ConsoleApplication1/ConsoleApplication1.sln"
    }
    stage("upload to artifactory"){
        def server = Artifactory.server('Artifactory')
        
        def uploadfile = """{
         "files": [
         {
            "pattern": "Assignments/ConsoleApplication1/ConsoleApplication1/*.csproj",
            "target": "projectjenkins/"
        }
        ]
        }"""

        server.upload(uploadfile)
        
    }
}