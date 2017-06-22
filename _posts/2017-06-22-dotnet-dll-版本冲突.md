---
date: 2017-06-21 09:50:47+00:00
layout: post
title: '.net解决程序集版本冲突的方法'
categories: 文档
tags:  'dll版本'
---

以log4net为例，分为两种情况

##1 不同version，相同publicKeyToken
在bin里放较新版本的dll

并在web|app.config的<configuration>下放

````
<runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="log4net" publicKeyToken="1b44e1d426115821" culture="neutral" />
                <bindingRedirect oldVersion="0.0.0.0-1.2.10.0"
                                 newVersion="1.2.11.0"/>
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
````

##2 不同version，不同publicKeyToken

在bin里创建不同版本的文件夹，并放入对应版本的dll,并在web.config的<configuration>下放:

````
<runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="log4net" publicKeyToken="681549d62126b7b8" />
        <codeBase version="1.2.9.0" href="bin/log4net1.2.9.0/log4net1.2.9.0.dll" />
      </dependentAssembly>
      <dependentAssembly>
        <assemblyIdentity name="log4net" publicKeyToken="1b44e1d426115821" />
          <codeBase version="1.2.10.0" href="bin/log4net1.2.10.0/log4net1.2.10.0.dll" />
      </dependentAssembly>
      <dependentAssembly>
        <assemblyIdentity name="log4net" publicKeyToken="669e0ddf0bb1aa2a" />
          <codeBase version="1.2.11.0" href="bin/log4net1.2.11.0/log4net1.2.11.0.dll" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
  ````

