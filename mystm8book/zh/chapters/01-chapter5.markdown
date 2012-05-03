# STM8编程实战之基础篇 #
本章从一个呼吸灯实验入手，再逐步加入中断、计时器等。带







## STM8官方库函数简介 ##
为了便于使用者快速开发程序，意法半导体公司为STM8开发了库函数，并带有详尽的使用文档和使用案例。这样一来程序
我们要找的库函数文件在<http://www.st.com/internet/com/SOFTWARE_RESOURCES/SW_COMPONENT/FIRMWARE/stm8_stdperiph_lib.zip>。这个库函数适用于STM8S以及STM8A的芯片

## STVD以及STVP##

要对我们的STM8芯片编程，
<http://www.st.com/internet/com/SOFTWARE_RESOURCES/TOOL/TOOLSET/sttoolset.zip>

### 使用STVD建立自己的工程文件 ###

STVD的地址：

![STVD的界面](figures/stvd.jpg)

这节写的比较纠结，因为IDE的东西，操作说得太絮叨了。如果可以的话，根据上节所讲的知识，自己试试看建立自己的工程文件吧。

## COSMIC编译器 ##

在这个案例开始前，我们必须要清楚STM8的时钟以及GPIO。

## 时钟 ##


分为Fmaster、Fcpu

Master时钟源有四种选择:

*1-24MHz高速外加晶振震荡时钟源（HSE）

*低于24Mhz一个外加时钟频率信号（HSE user-ext）

*芯片自带的一个16MHz高速RC震荡时钟源（HSI）

*芯片自带的一个128KHz低速RC震荡时钟源（LSI）


默认情况下，系统默认使用HSI/8的时钟源，也就是说系统默认的运行速率是2Mhz。

### 时钟树 ###

## GPIO ##

### GPIO的几种状态 ###



## 中断 ##


## 计时器 ##
