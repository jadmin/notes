# 在Mac下使用linux下的ll命令

mac下有ls命令，但没有ll命令，可以通过如下步骤实现

* sudo vim /etc/profile，写入如下内容

```
alias ll='ls -alF'
alias la='ls -A' 
alias l='ls -CF'
```

* 保存生效

```
source /etc/profile
```
