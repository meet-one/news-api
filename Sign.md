## 1. 签名算法

### 1.1 参数拼接
所有发送或者接收到的数据为集合M，将集合M内非空参数值的参数按照参数名ASCII码从小到大排序（字典序），使用URL键值对的格式（即key1=value1&key2=value2…）拼接成字符串string

注意事项：<br>
1、参数名ASCII码从小到大排序（字典序）<br>
2、如果参数的值为空不参与签名<br>
3、参数名区分大小写<br>
4、验证调用返回或主动通知签名时，传送的sign参数不参与签名，将生成的签名与该sign值作校验<br>
5、接口可能增加字段，验证签名时必须支持增加的扩展字段

例：
string="appid=aa0c00b04ae19ff1d25ec035f1248753&nonce_str=66f7f4c84569ddb5289921e12288983d&product=游戏充值钻石10个&total_eos=0.001&wallet=rrrrrr521314"


### 1.2 拼接密钥
在string最后拼接上key密钥

例：
string="appid=aa0c00b04ae19ff1d25ec035f1248753&nonce_str=66f7f4c84569ddb5289921e12288983d&product=游戏充值钻石10个&total_eos=0.001&wallet=rrrrrr521314" + "&key=c0901d8b5d783ee0835d87e9c433fb24"


### 1.3 生成签名
对字符串string进行MD5运算，再将得到的字符串所有字符转换为大写，得到sign值
