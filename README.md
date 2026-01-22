# 正方教务管理系统成绩推送

<img src="https://raw.githubusercontent.com/NianBroken/ZFCheckScores/main/img/7.jpg" style="zoom:60%;" />

## 简介

**使用本项目前：**

早晨睡醒看一遍教务系统、上厕所看一遍教务系统、刷牙看一遍教务系统、洗脸看一遍教务系统、吃早餐看一遍教务系统、吃午饭看一遍教务系统、睡午觉前看一遍教务系统、午觉醒来看一遍教务系统、出门前看一遍教务系统、吃晚饭看一遍教务系统、洗澡看一遍教务系统、睡觉之前看一遍教务系统

**使用本项目后：**

成绩更新后**自动发通知到微信** 以节省您宝贵的时间

## 测试环境

正方教务管理系统 版本 V8.0、V9.0

如果你的教务系统页面与下图所示的页面**完全一致**或**几乎一致**，则代表你可以使用本项目。

<img src="https://raw.githubusercontent.com/NianBroken/ZFCheckScores/main/img/9.png" style="zoom:60%;" />

## 目前支持的功能

1. 主要功能

   1. 每隔 30 分钟自动检测一次成绩是否有更新，若有更新，将通过微信推送及时通知用户。

2. 相较于教务系统增加了哪些功能？

   1. 显示成绩提交时间，即成绩何时被录入教务系统。
   2. 显示成绩提交人姓名，即成绩由谁录入进教务系统。
   3. 成绩信息按时间降序排序，确保最新的成绩始终在最上方，提升用户查阅效率。
   4. 计算 `GPA`
   5. 计算百分制 `GPA`
   6. 对于没有分数仅有级别的成绩，例如”及格、良好、优秀“，可以强制显示数字分数。
   7. 显示未公布成绩的课程，即已选课但尚未出成绩的课程。

## 使用方法

在main.py中找到下列代码进行配置

```python
local_env = {
    "URL": "http://jwxt.cumt.edu.cn/jwglxt/",//教务系统网站，'jwglxt'的添加看自己学校
    "USERNAME": 'xxx',//学号
    "PASSWORD": 'xxx',//密码
    "TOKEN": 'xxx',//推送token
    "FORCE_PUSH_MESSAGE": "False",//强制推送，成绩是否有更新都进行推送
    "CHECK_INTERVAL_SECONDS": "360",//推送时间间隔
    "LOCAL_COOKIES": 'JSESSIONID=xxx; route=xxx',//教务系统token，优先配置该项
}
```

推送token在https://push.showdoc.com.cn/获取

比如https://push.showdoc.com.cn/server/api/push/f82b3276cfd5f6458fe4eb64209cfb50c2545a47f61e837a8a14a1c1b09e3f26
推送token就是f82b3276cfd5f6458fe4eb64209cfb50c2545a47f61e837a8a14a1c1b09e3f26

## 程序逻辑

1. 清空文件 B 中的内容
2. 将文件 A 中的内容写入到文件 B
3. 清空文件 A 中的内容
4. 将获取到的成绩进行 MD5 加密
5. 将加密后的成绩写入到文件 A
6. 比对文件 A 与文件 B 的内容是否一致
7. 若一致则表示成绩未更新，若不一致则表示成绩已更新

_若是第一次运行程序，上述步骤会执行两遍_

## 许可证

`Copyright © 2024 NianBroken. All rights reserved.`

本项目采用 [Apache-2.0](https://www.apache.org/licenses/LICENSE-2.0 "Apache-2.0") 许可证。简而言之，你可以自由使用、修改和分享本项目的代码，但前提是在其衍生作品中必须保留原始许可证和版权信息，并且必须以相同的许可证发布所有修改过的代码。

## 特别感谢

[openschoolcn/zfn_api](https://github.com/openschoolcn/zfn_api "openschoolcn/zfn_api")

## 其他

欢迎提交 `Issues` 和 `Pull requests`
