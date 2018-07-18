# HelloWorld
这是对GitHub的学习
对分支的尝试

1.更改一
2018/4/17
关于iis 配置问题的解决方法之一
问题是[Win32Exception (0x80004005): 拒绝访问。]

[ExternalException (0x80004005): 无法执行程序。所执行的命令为 "C:\wwwroot\lanjia_qx57c6\web\bin\roslyn\csc.exe" /shared /keepalive:"10" /noconfig  /fullpaths @"C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Temporary ASP.NET Files\root\037c0e7d\a7f491d1\gq3pb2ov.cmdline"。]


-----解决方案1--------------------
具体的不是很清楚，但下面的可以参考下。
允许匿名访问 IIS 应用程序。
启用模拟为 Web 应用程序在本地 Web.config 文件中，如下所示： 
<configuration>
<system.web>	
<identity impersonate="true" />
</system.web>
</configuration>
运行 IIS Lockdown 工具，或 IUSR _ COMPUTERNAME 或 Csc.exe 文件上的 IWAM _ COMPUTERNAME 帐户拒绝访问您请求该页面之前。
-----解决方案1--------------------


-------------问题----------------
“/”应用程序中的服务器错误。
-----解决方案2--------------------
问题已解决，是因为 项目的互相引用，而各项目的 相同的 dll 版本不同。。比如 有 Toos 功能类库，有 web 应用程序，都引用了 Newtonsoft.Json   。Tools 里面是 2.1版本，web 里面是 1.8 版本。 而 web 又引用了 Toos项目 ，，这就导致 网站生成发布后 编译失败，所以，最终解决方案是：在 解决方案上面 右键 ，管理 nuget 包，合并 整个解决方案的 dll类库，使全部都同步版本。 。
-----解决方案2--------------------
