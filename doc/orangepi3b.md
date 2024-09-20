# QVQ
- 有一个开发板香橙派3B，不幸的是以太网口用不了了
- 当时刷了好几遍系统，又发现一问题，1.0.4以上的进不了系统（只用过Ubuntu镜像）
- 以及server版没dosktop版的某些功能，比如终端图形化控制I2C、UART、SPI等开关（orangepi-config无法使用


# wiringPi库中wiringPiISR函数用不了
终于在大佬的研究下找到了BUG([zhaosj98提交的Issues](https://github.com/orangepi-xunlong/wiringOP/issues/118))  

wiringPi.c文件的第4535行sprintf (pinS, "%d", pin) ;应该改为sprintf (pinS, "%d", bcmGpioPin ) ;，否则会报错：“gpio: Unable to open GPIO direction interface for pin XX: No such file or directory”

```vim
:set nu
4535gg
```
vim不熟悉，忘记命令了