
node() {
//    git 'https://github.com/jenkinsci/parallel-test-executor-plugin-sample.git'
//    stash name: 'SHARD', includes: 'us1,us2,us3'
    stage("TEST STAGE"){
        echo "From the Jenkinsfile"
    }
}
def splits = 3
def SHARDS = ["us1", "us2", "us3"]
SHARDS[0] = "us1"
SHARDS[1] = "us2"
SHARDS[2] ="us3"

def branches = [:]
//for (int i = 0; i < SHARDS.size(); i++) {
SHARDS.each {
    def index = i // fresh variable per iteration; i will be mutated
    branches["us${i}"] = {
        node() {
            stage("TEST"){
//                echo SHARDS.get(index)
                echo it
            }
//            deleteDir()
//            unstash 'SHARD'
//            def exclusions = splits.get(index);
//            writeFile file: 'exclusions.txt', text: exclusions.join("\n")
//            sh "${tool 'M3'}/bin/mvn -B -Dmaven.test.failure.ignore test"
//            junit 'target/surefire-reports/*.xml'
        }
    }
}
parallel branches