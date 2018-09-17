#如何使用SAM创建CFC应用程序

无服务器应用程序模型（SAM）描述了CFC应用程序中使用的资源。
您可以将无服务器应用程序定义为SAM模板 - JSON或YAML
配置文件，描述CFC函数。 使用命令工具，可以打包，并上传部署他们到线上的CFC环境中。
		
## 编写 SAM Template
查看[这里](https://github.com/bcelabs/serverless-application-model/blob/bsam_alpha/versions/2018-08-30.md)，以获取有关如何编写SAM模板的详细信息

## Generate-Event
sam generate-event 生成度秘、BOS 事件

## Local Invoke
现阶段支持本地调用nodejs、python 函数，具体可执行`sam local invoke --help`获取细节。

## Packing Artifacts
在部署CFC应用之前，应首先将功能代码打包生成zip。可以选择手动执行此操作或使用`sam package`命令。该命令会检查当前路径下的template.yaml文件，获取函数的函数名和代码路径`CodeUri` ，以函数名为包名，`CodeUri`为打包路径，生成template.yaml中所有描述的函数对应的zip包。

要使用此命令，请将`CodeUri`属性设置为相应函数的用户代码路径

```YAML
MyFunction:
    Type: BCE::Serverless::Function
    Properties:
        CodeUri: ./code
        ...
```


## Deploy
将应用打包后，可以上传至CFC的线上环境中。`sam deploy`命令会去`~/.bce/credential`中读取用户的`AK/SK`,并读取`~/.bce/config`中的`region`设置，将`sam package`命令生成的代码包上传。如果之前在同类cli工具中配置过相应的设置项则命令可正常工作，否则可以运行`sam config`命令，并按提示设置相应的选项。