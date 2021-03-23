# java 세팅

## JAVA_HIOME  설정 
1. 버전 확인 
    java -version 

2. PATH 확인  
    echo $PATH 
    echo $JAVA_HOME 
    cat $JAVA_HOME 

3. 설치 된 자바 경로 확인 
    which java 


## JAVA_HOME 설정 방법1 
    1. JAVA를 원하는 위치에 설정. ex) /usr/java/jdk17.x 
    2. 심볼릭 링크 파일을 만들어준다. 
        ln -s /usr/java/jdk1.7.0 /usr/java/lastest 
        ln -s /usr/java/lastest /usr/java/default 
        -> 하나만 바로 만들어도 되나, 좀더 명확하게 하기 위함. 

    3. /usr/bin 하위에 심볼릭 링크를 생성 
        ln -s /usr/java/default/bin/jar /usr/bin/jar 
        ln -s /usr/java/default/bin/java /usr/bin/java 
        ln -s /usr/java/default/bin/javac /usr/bin/javac 
        ln -s /usr/java/default/bin/javadoc /usr/bin/javadoc 
        ln -s /usr/java/default/bin/javaws /usr/bin/javaws 
        ln -s /usr/java/default/bin/jcontrol /usr/bin/jcontrol 

    4. /usr/bin 하위에 있으면 path 설정 없이 사용가능해진다. 