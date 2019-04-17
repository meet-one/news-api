## 1. 查询快讯列表

### 1.1 功能描述
查询快讯列表

### 1.2 请求说明
> 请求方式：POST
请求URL ：[https://more.ethte.com/auth/newsflash](#)  

### 1.3 请求参数
字段         |字段类型      |字段说明
-------------|-------------|-----------
appid        |string(32)   |APP识别号（[点击获取测试id](https://github.com/meet-one/news-api/blob/master/Test.md)）
show_time    |int(10)      |快讯显示时间戳 第一页快讯数据以当前时间戳 每次分页则以最后一则快讯show_time请求下一页
lang         |string(2)    |快讯语言类型 zh-中文 en-英文
page_size    |int(2)       |每次加载分页快讯数量 最大值50 默认20 (非必传)
nonce_str    |string(32)   |随机字符串(用户随机生成)
sign         |string (32)  |通过签名算法(详见文档[Sign.md](https://github.com/meet-one/news-api/blob/master/Sign.md))计算得出的签名值

### 1.4 请求示例
```json
{
  "appid": "aa0c00b04ae19ff1d25ec035f1248753",
  "show_time": 1555401623,
  "lang": "zh",
  "page_size": 20,
  "nonce_str": "66f7f4c84569ddb5289921e12288983d",
  "sign": "3DF76D258C14EEDD706639284E5AB459"
}
```
### 1.5 返回结果
```json  
{
  "errorcode": 0,
  "message": "",
  "data": [{
    "id": 22294,
    "title": "Reddit 网友发帖：第一次用 EOS 购买胡萝卜蛋糕",
    "content": "今日有人在 Reddit 论坛上传了一段“第一次在马德里通过支付 EOS 购买胡萝卜蛋糕”的视频，该帖子引发了 Reddit 网友的热烈讨论：\n\n有网友回复：未来几年，这可能就变成了一块昂贵的胡萝卜蛋糕的故事，就像用比特币购买披萨的故事一样；有网友回复：看到这样的故事真的很兴奋；有网友回复：这有益于 EOS 的发展...（MEET.ONE 报道）",
    "img": "https://static.ethte.com/MoreOne/image/candy/2019_04_12/7476/微信图片_20190412152859.png",
    "url": "https://www.reddit.com/r/eos/comments/bbylmk/i_used_eos_for_the_first_time_to_pay_for_a_piece/",
    "show_time": 1555054046,
    "label_id": 13,
    "is_important": 1,
    "label_name": "社区"
    }]
}
```

### 1.6 返回参数
字段           |字段类型       |字段说明
--------------|-----------|-----------
id            |int        |快讯id
title         |string     |快讯标题
content       |string     |快讯内容
img           |string     |快讯图片
url           |string     |快讯原文链接
show_time     |int        |快讯上线时间戳
label_id      |int        |分类标签id
is_important  |int        |是否重要 0-否 1-是
label_name    |string     |分类标签名称


### 1.7 错误状态码
状态码      |说明
------------|-----------
4000        |参数问题
1001        |参数不为空
1002        |APP账号不存在
1003        |签名错误
1004        |超过限制访问次数
