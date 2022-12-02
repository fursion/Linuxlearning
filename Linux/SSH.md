# SSH免密登录

## ssh-keygen

生成免密登录需要的密钥对

```bash
ssh-keyagen -t rsa -f <filename> -C "tag"
```



## ssh-copy-id

将公钥发送到目标主机

```bash
# ssh-copy-id [-i [identity_file]] [user@]machine
# -i 后接身份文件(由ssh-keyagen生成的密钥对公钥)
ssh-copy-id -i ~/.ssh/fursion_rsa.pub  fursion@example.com
```

