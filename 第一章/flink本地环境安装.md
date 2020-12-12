一 flink下载
	官网 
		https://github.com/apache/flink
	clone源代码 
		git clone https://github.com/apache/flink.git

二 编译
	mvn clean package -DskipTests # this will take up to 10 minutes
	期间可能会报错，针对性处理，如我这边就碰到几个问题。

	1）找不到依赖方
	[ERROR] Failed to execute goal on project flink-avro-confluent-registry: Could not resolve dependencies for project org.apache.flink:flink-avro-confluent-registry:jar:1.12-SNAPSHOT: Failure to find io.confluent:kafka-schema-registry-client:jar:5.5.2 in http://mvnrepo.alibaba-inc.com/mvn/repository was cached in the local repository, resolution will not be reattempted until the update interval of tbmirror-all has elapsed or updates are forced -> [Help 1]

	手动从官网去下载:
	http://packages.confluent.io/maven/io/confluent/kafka-schema-registry-client/
	http://packages.confluent.io/maven/io/confluent/kafka-avro-serializer/

	然后通过mavan安装到本地环境：
	mvn install:install-file -DgroupId=io.confluent -DartifactId=kafka-schema-registry-client -Dversion=5.5.2 -Dpackaging=jar -Dfile=kafka-schema-registry-client-5.5.2.jar

	mvn install:install-file -DgroupId=io.confluent -DartifactId=kafka-avro-serializer -Dversion=5.5.2 -Dpackaging=jar -Dfile=kafka-avro-serializer-5.5.2.jar


	然后再次进行编译