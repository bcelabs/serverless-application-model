# Baidu Serverless Application Model (BSAM) -- README
可以使用BSAM来简洁的定义CFC函数应用。这个GitHub项目是BSAM的起点。 它包含BSAM规范，有关模型的一般信息以及常见应用程序的示例。

BSAM规范的定义和实现是在Apache 2.0许可下开源的。 当前版本的BSAM规范可在[BSAM 2018-08-30](versions/2018-08-30.md)中可获得。

## 使用SAM创建无服务器应用程序
要使用BSAM创建CFC应用程序，首先要创建BSAM模板：JSON或YAML配置文件，用于描述CFC函数和应用程序中的其他资源。然后，使用[BSAM Local CLI](https://github.com/bcelabs/bce-sam-cli)测试，上传和部署应用程序。在部署期间，BSAM CLI会自动填写任何未指定属性的默认值，并确定适当的映射和调用权限，以便为任何CFC函数进行设置。
[查看此文档](HOWTO.md)来了解如何定义和部署CFC应用。