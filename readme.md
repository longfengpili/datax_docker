# 使用指引
+ [官方链接](https://github.com/alibaba/DataX/blob/master/userGuid.md)
# jobs
+ 执行任务
`python3 /datax/target/datax/datax/bin/datax.py /jobs/job.json`
# 支持mysql8.0
1. 修改根目录下的`pom.xml`中的mysql驱动  
`<mysql.driver.version>8.0.11</mysql.driver.version>`
2. 修改`zeroDateTimeBehavior`的值`convertToNull`为`CONVERT_TO_NULL`
3. 修改jdbc驱动的名称`com.mysql.jdbc.Driver`为`com.mysql.cj.jdbc.Driver`
4. jdbc链接追加useSSL=false设置  
`python datax.py file.json`，file.json的配置项："jdbcUrl":"jdbc:mysql://user:password/database?useUnicode=true&characterEncoding=UTF-8&useSSL=false"
# ERROR
1. `Failed to execute goal on project hdfsreader: Could not resolve dependencies for project com.alibaba.datax:hdfsreader:jar:0.0.1-SNAPSHOT: The following artifacts could not be resolved: com.alibaba.datax:plugin-unstructured-storage-util:jar:0.0.1-SNAPSHOT, org.apache.parquet:parquet-format:jar:2.3.0: Could not find artifact com.alibaba.datax:plugin-unstructured-storage-util:jar:0.0.1-SNAPSHOT in central (https://maven.aliyun.com/repository/central)`
解决方案：
1. 访问[阿里云云效Maven仓库](https://developer.aliyun.com/mvn/guide)
2. 在仓库文件中搜寻`parquet-format:jar`, 找到可以支持的版本
3. 在对应的pom.xml修改对应版本
