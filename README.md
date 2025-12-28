![聪音大头照](./pic/聪音.png)

# Chill With You 存档解析

本项目旨在解析 Chill With You 游戏的存档文件内容，方便玩家在需要修改存档的时候不用再反编译代码查找

> 文档命名参照存档文件命名，如不想看介绍可直接点击对应文档查看  
> 快查存档名与内容对应：[每个存档内容](#每个存档内容)

## 前言

### 游戏介绍

「放松时光：与你共享Lo-Fi故事」是一个与喜欢写故事的女孩聪音一起工作的有声小说游戏。您可以自定义艺术家的原创乐曲、环境音和风景，以营造一个专注于工作的环境。在与聪音的关系加深的过程中，您可能会发现与她之间的特别联系。  
Steam商店链接：[Chill with You : Lo-Fi Story](https://store.steampowered.com/app/3548580/LoFi/)

## 存档位置

一般位于  
`C:\Users\luochu\AppData\LocalLow\Nestopi\Chill With You\SaveData\Release\v2\76561198861016304`  
其中，`luochu` 是你的 Windows 用户名，`76561198861016304` 是你的 SteamID。

## 存档文件加解密

存档使用 Unity 商城的 Easy Save 插件保存
插件链接：[Easy Save - The Complete Save Game & Data Serializer System](https://assetstore.unity.com/packages/tools/utilities/easy-save-the-complete-save-game-data-serializer-system-768)
文档链接：[Easy Save 3 Documentation](https://docs.moodkie.com/product/easy-save-3/)。

存档文件后缀都为 `.es3`，实际上是一个 gzip 压缩包，解压后是一个没有后缀的 json 文件。  
想要解码存档，只需将`.es3`后缀改成`.gz`，然后使用解压软件解压即可。 json 加密回去同理，不再赘述。

如果怕麻烦，或者没有可以解压`.gz`后缀的解压软件，也可以使用这个网址：[EasySave3 Editor](https://es3.tusinean.ro/)   
比较麻烦的是加解密输出的是固定文件名称，当你需要替换存档或者标记是哪个存档文件时，得手动改一下名字。

## 存档内容解析

### 存档格式

所有存档格式遵循 json 语法，如下例：

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

## 每个存档内容

详细见每篇文章

- [窗外景色及环境声音数据](./-39941661.md)