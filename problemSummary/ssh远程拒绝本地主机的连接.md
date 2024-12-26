
```
报错信息:
Cloning into 'imca_engineering'...
kex_exchange_identification: Connection closed by remote host
Connection closed by 198.18.0.10 port 22
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
- 198.18.0.10是我本地主机的IPV4地址，22是github.com与我主机进行信息交互的端口号
- 本条报错信息是不能从远程仓库读取，没有访问权或者是该仓库不存在，貌似这时候，我的github还没添加成功ssh密钥，导致没有访问权
- 终端输入：

```
ssh git@github.com
#测试ssh设置是否成功
```
- 输出提示信息：
```
kex_exchange_identification: Connection closed by remote host
Connection closed by 198.18.0.104 port 22
```
- 关闭代理或者vpn后重新测试
###总结
- 大概失败原因是因为我的ssh密钥前面没有成功添加至github导致的
- 因为添加成功后，利用ssh git@github.com命令测试是否成功添加时，他说拒绝连接，那就是他它查看了自己已有的ssh密钥，没发现有相同的，就拒绝了我的连接，最后也没为我生成主机验证密钥。
- 并且，我的ip地址正确，如果是ip地址被代理更改，不应该是我在局域网中被分配的那个ip地址
- 测试正确添加ssh

```
ssh -T git@github.com
```