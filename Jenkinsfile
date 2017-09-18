
node() {
//    git 'https://github.com/jenkinsci/parallel-test-executor-plugin-sample.git'
//    stash name: 'SHARD', includes: 'us1,us2,us3'
    stage("TEST STAGE"){
        echo "From the Jenkinsfile"
    }
}
def splits = 3
def SHARDS = new String[3]
SHARDS[0] = "us1"
SHARDS[1] = "us2"
SHARDS[2] ="us3"

def branches = [:]
for (int i = 0; i < SHARDS.size(); i++) {
    def index = i // fresh variable per iteration; i will be mutated
    branches["split${i}"] = {
        node() {
            stage("Multi test: " + splits.get(index)){
                echo splits.get(index)
                echo "SHARD US${i}"
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