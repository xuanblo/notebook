# shell

* check server type `curl -I www.baidu.com`

* 切片 `sed -n '5,$p'`

* 禁止个别用户登录
```
passwd -l test #使用-l指令将user1锁定，这样就不能登录了，但是可以从root账户切换到user1用户
passwd -S user1 # -S表示查看用户test的状态
passwd -u user1 #-u可以将锁定的用户密码解除
```

* 查看当前用户登录情况 `w`

* 看有哪些程序占用CPU，`top + H`

* 删除用户 `sudo userdel -f test #为了在删除用户时完全删除家目录，我们可以使用 -r 选项。这个选项同样会删除用户的邮件池，如果存在的话。`

* 针对这个全基因组位点的统计结果，我们很容易写脚本来计算每条平均的测序深度和各个染色体的覆盖度。
```
nohup time samtools mpileup P_jmzeng.final.bam |perl -alne '{$pos{$F[0]}++;$depth{$F[0]}+=$F[3]} END{print "$_\t$pos{$_}\t$depth{$_}" foreach sort keys %pos}' 1>coverage_depth.txt 2>coverage_depth.log &
```

## 用终端看电影
```shell
brew install mplayer # mac
mplayer -vo caca your_moive.name
```



# 服务器

- Ubuntu Apache
    - restart service `sudo /etc/init.d/apache2 restart`
    - conf file path `sudo vi /etc/apache2/apache2.conf`

lsb_release -a 查看ubuntu版本
uname -a 查看linux看系统是多少位的