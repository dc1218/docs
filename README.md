# 记录
## 第1个记录
  - makefile 示例
  ```
  # Makefile for building:helloRect
  # CC是C语言编译器
  CC	= gcc
  # CXX是C++编译器
  CXX	= g++
  # 链接器
  LINKER	= g++
  # 链接器参数
  LFLAGS	= -lm -static

  # 编译得到的目标文件
  OBJECTS	= rect.o helloRect.o
  # 可执行的目标文件
  DSTTARGET	 = helloRect
  # 默认生成规则（它的下一行没有命令，如何生成$(DSTTARGET)需要往下看）
  all: $(DSTTARGET)

  # 生成$(DSTTARGET)需要$(OBJECTS),有了目标文件之后执行命令
  # 调用连接器$(LINKER)、 根据链接器参数$(LFLAGS) 
  # $@表示冒号左边要生成的目标$(DSTTARGET)生成目标文件$(OBJECTS)
  # 注意$(LINKER之前一定要是tab制表符，不能是四个空格键
  $(DSTTARGET): $(OBJECTS)
    $(LINKER) $(LFLAGS) -o $@ $(OBJECTS)

  # $@表示冒号左边要生成的目标helloRect.o
  # $<表示冒号右边第一个依赖文件helloRect.cpp
  helloRect.o: helloRect.cpp
    $(CXX) -c -o $@ $<

  # $@表示冒号左边要生成的目标rect.o
  # $<表示冒号右边第一个依赖文件rect.cpp
  rect.o: rect.cpp
    $(CXX) -c -o $@ $<

  # 清除命令
  clean:
    rm $(OBJECTS) helloRect.exe
  ```
  ## 第2个记录
    # centos7 部署django环境
    ## 部署mysql
    - 离线安装mysql
    ## 部署redis
    - 离线安装redis
    ## 部署python依赖环境
    - 离线安装python依赖
    ## 部署python
    - 离线安装python
    # 在线安装
    - 参考：https://www.cnblogs.com/ianduin/p/7679239.html
    ```
    //换源
    mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
    wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
    yum makecache
    yum update
    yum upgrade
    wget http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm
    yum localinstall mysql57-community-release-el7-8.noarch.rpm
    yum repolist enabled | grep "mysql.*-community.*"
    yum install mysql-community-server
    systemctl start mysqld
    systemctl enable mysqld
    systemctl daemon-reload
    //查看默认root密码
    grep 'temporary password' /var/log/mysqld.log
    //修改mysql默认密码
    shell> mysql -u root -p
    mysql> show variables like '%password%';
    mysql> set global validate_password_policy=0;
    mysql> set global validate_password_length=1;
    mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'mm123'; 
    mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'mm123' WITH GRANT OPTION;
    mysql> FLUSH  PRIVILEGES;
    //python依赖
    yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel libffi-devel gcc make
    //python 升级
    wget -P /usr/local  http://www.python.org/ftp/python/3.8.5/Python-3.8.5.tgz
    cd /usr/local
    tar -xzvf Python-3.8.5.tgz -C /usr/local
    mkdir /usr/local/python3
    cd /usr/local/Python3.8.5
    ./configure --prefix=/usr/local/python3
    make && make install
    mv /usr/bin/python /usr/bin/python_old2
    ln -s /usr/local/python3/bin/python3 /usr/bin/python
    ```


