# 任务
### 循环任务 crontab
1. 命令
```shell
> crontab -e //新建
> crontab -l //查看
> crontab -r //删除
> crontab -u //编辑他人任务计划
```  
2. 格式: 分 时 日 月 星期 命令
- 星号*: 站位符
- 逗号,: * * 1,2,3 * * /usr/bin/tar -zxvf backup.tar.gz /home/wwwroot   每月的1,2,3执行命令
- 短破折号-: * * * * 1-5 /usr/bin/tar -zxvf backup.tar.gz /home/wwwroot 周一到周五执行命令
- 斜杠/: /2 * * * * /usr/bin/tar -zxvf backup.tar.gz /home/wwwroot 每间隔2分钟执行命令
- 日 和 星期不能同时存在
- 命令必须是绝对完整路径,而非 tar -zxvf backup.tar.gz /home/wwwroot

3. 范围
|字段|说明|
|-|-|
|分|0~59整数|
|时|0~23整数|
|日|1~31整数|
|月|1~12整数|
|星期|0~7整数,0与7都指周日|


|column1|column2|column3|
|-|-|-|
|content1|content2|content3|


### 一次性任务 at
1. 命令 at 时间 进入编辑模式
```shell
> at 23:30
> at > systemctl restart httpd
> at > 按下ctrl+D结束编写任务计划
> at -l //查看已设置好,但未执行的一次性任务
> atrm 序号1 //根据序号删除未执行的一次性任务
```