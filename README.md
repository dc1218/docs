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
    - rust 初探
      - centos8 安装rust

