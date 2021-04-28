一般来说，只要确保的下载的是VL批量版本并且没有手动安装过任何key，

你只需要使用管理员权限运行cmd执行一句命令就足够：

<img src="https://i.loli.net/2021/04/28/fKMcqVnR2whbJP9.png" width = "300" height = "300" alt="" align=center />

```Shell
slmgr /skms kms.03k.org
```

这句命令的意思是，把kms服务器地址设置（set kms）为kms.03k.org，设置成功之后：

```Shell
slmgr /ato
```

这句话是让系统检查激活，完成后会有弹窗显示结果。