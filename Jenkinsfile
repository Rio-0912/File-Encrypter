stage('Test') {
    steps {
        sh '''
        cd "Password Protection"
        
        # 1. Force download if the file is tiny/corrupted (less than 1MB)
        if [ ! -s junit-platform-console-standalone.jar ]; then
            echo "Downloading JUnit standalone..."
            curl -L -o junit-platform-console-standalone.jar https://repo1.maven.org/maven2/org/junit/platform/junit-platform-console-standalone/1.10.0/junit-platform-console-standalone-1.10.0.jar
        fi

        mkdir -p test-build
        
        # 2. Compile tests - Ensure you point to your test source folder!
        # Assuming your tests are in a 'test' directory
        javac -cp "junit-platform-console-standalone.jar:build" -d test-build src/test/*.java
        
        # 3. Run the tests
        java -jar junit-platform-console-standalone.jar --class-path "build:test-build" --scan-class-path
        '''
    }
}
