https://blog.csdn.net/kingsleytong/article/details/70176518
https://www.jianshu.com/p/3fc93c16ad2d
关键信息如下
ssh-add -l 查看当前ssh私钥存储情况
记得用不同的email生成不同的公钥私钥,有多少个账号就有多少个公钥私钥对,有多少个公钥私钥对就钥添加多少次ssh-add -K
> ssh-add -K ~/.ssh/github_id-A-rsa
> ssh-add -K ~/.ssh/github_id-B-rsa
其中~/.ssh/github_id-A-rsa与~/.ssh/github_id-B-rsa文件都是针对github.com网站的2个密钥文件
通过.ssh/config文件配置,其中指定的Host属性要与github的ssh地址匹配上
比如:github上面的地址是git@github.com:Scott20200207/JavaScript_TUT.git
而在~/.ssh/config文件中配置的内容是
Host a.github.com
HostName github.com
User Scott20200207
PreferredAuthentications publickey
IdentityFile ~/.ssh/github_id-protonmail-rsa
那么命令:
> git remote rm origin  //删除原是的路径
> git remote add origin git@a.github.com:Scott20200207/JavaScript_TUT.git //修改原是的路径
如果是使用git clone,记得也要修改github.com->a.github.com,此信息记录在当前repository所在目录的.git/config中
测试账号是否可用
> ssh -T git@a.github.com//通过a.github.com找到~/.ssh/config下的Host->HostName->IP地址,其中git为一个公用账号
//可以理解为ssh -Test 账号:密码@域名

git config --list 查看~/.gitconfig 配置情况
git config --shwo-origin --get <配置项> 可以查看配置项所在的文件位置
git config --show-origin --get credential.helper