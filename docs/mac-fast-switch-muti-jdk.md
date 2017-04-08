# Mac下设置快速切换多版本jdk的环境变量

+ 前提条件：mac支持/usr/libexec/java_home命令，版本在Mac OS X 10.5以上
+ 安装各种版本的jdk
+ 在/etc/profile文件中下入以下内容

```
JAVA_6_HOME=`/usr/libexec/java_home -v 1.6`
JAVA_7_HOME=`/usr/libexec/java_home -v 1.7`
JAVA_8_HOME=`/usr/libexec/java_home -v 1.8`

# 诸如zk/maven等开源软件home的配置
MAVEN_HOME=/Users/chen/i/maven

# 系统path
export PATH_SYS=/usr/local/bin:$(getconf PATH)

# 这里追加你需要的path
export PATH_EXCLUDE_JAVA=$PATH_SYS:$MAVEN_HOME/bin

# 这里追加你需要的lib
export CLASSPATH_EXCLUDE_JAVA=.

# 默认环境
export JAVA_HOME=$JAVA_8_HOME
export CLASSPATH=$CLASSPATH_EXCLUDE_JAVA:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH_EXCLUDE_JAVA:$JAVA_HOME/bin


#alias命令动态切换JDK版本
alias jdk6="export JAVA_HOME=$JAVA_6_HOME CLASSPATH=$CLASSPATH_EXCLUDE_JAVA:$JAVA_6_HOME/lib/dt.jar:$JAVA_6_HOME/lib/tools.jar PATH=$PATH_EXCLUDE_JAVA:$JAVA_6_HOME/bin"
alias jdk7="export JAVA_HOME=$JAVA_7_HOME CLASSPATH=$CLASSPATH_EXCLUDE_JAVA:$JAVA_7_HOME/lib/dt.jar:$JAVA_7_HOME/lib/tools.jar PATH=$PATH_EXCLUDE_JAVA:$JAVA_7_HOME/bin"
alias jdk8="export JAVA_HOME=$JAVA_8_HOME CLASSPATH=$CLASSPATH_EXCLUDE_JAVA:$JAVA_8_HOME/lib/dt.jar:$JAVA_8_HOME/lib/tools.jar PATH=$PATH_EXCLUDE_JAVA:$JAVA_8_HOME/bin"
```

+ jdk版本环境切换，直接在终端里输入
jdk6 或 jdk7 或 jdk8

