<!-- markdownlint-disable-file MD041 -->

<div align="center">

<a href="https://store.steampowered.com/app/3548580/LoFi/">
    <img src="./pic/Chill With You.png" width="50%"  alt="Chill With You">
</a>

</div>

# Chill With You 存档解析

这个项目的目的是帮助想要自行修改存档的玩家可以轻松修改，不用反编译游戏文件，去阅读难以理解的代码，即可了解存档的加解密，以及存档文件的数据与游戏内相关元素的对应关系。

> 文档命名参照存档文件命名，如不想看介绍可直接点击对应文档查看  
> 快查存档名与内容对应：[存档内容详细说明](#存档内容详细说明)

## 前言

### 游戏介绍

「放松时光：与你共享Lo-Fi故事」是一个与喜欢写故事的女孩聪音一起工作的有声小说游戏。您可以自定义艺术家的原创乐曲、环境音和风景，以营造一个专注于工作的环境。在与聪音的关系加深的过程中，您可能会发现与她之间的特别联系。 <!-- markdownlint-disable-line line-length -->

Steam商店链接：[Chill with You : Lo-Fi Story](https://store.steampowered.com/app/3548580/LoFi/)

## 存档位置

一般位于  

> C:\Users\你的用户名\AppData\LocalLow\Nestopi\Chill With You\SaveData\Release\v2\你的SteamID

- **你的用户名**：Windows 用户名。
- **你的 SteamID**：您的 Steam 账户 ID。

## 存档文件加解密

存档文件后缀为 `.es3`，实际上是一个 gzip 压缩包，解压后会得到一个无后缀的 JSON 文件。以下是加解密步骤：

1. 解密存档：将 .es3 文件后缀改为 .gz，然后使用解压软件解压。
2. 加密存档：将 JSON 文件压缩为 .gz，再将后缀改回 .es3。

如果你不想手动操作，也可以使用这个在线工具：[EasySave3 Editor](https://es3.tusinean.ro/)
注意：该网站输出的文件名是固定的，替换存档时需要手动修改文件名。

## 存档内容解析

### 存档格式

存档文件遵循 JSON 格式，示例如下：

```json
{
    "-39941661" : {
        "__type" : "Bulbul.EnviromentData,Assembly-CSharp",
        "value" : {
            "WindowViewDic" : {0:{
                    "WindowViewType" : 0,
                    "IsActive" : false
                }
            }
        }
    }
}
```

- "-39941661": hash码，标识该存档文件，具体算法没看懂。
- "__type": 存档数据类型，格式为 "命名空间.类名,程序集名称"。
- "value": 存档数据内容，具体字段根据数据类型不同而不同。

## 存档内容详细说明

详细见每篇文章

- [-39941661: 窗外景色及环境声音数据](./-39941661.md)
