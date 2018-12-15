# YeeWallet

目前支持BTC,ETH,USDT以及所有基于ERC20开发的代币

#### HTTP API

* 接口调用说明

  * [校验]所有接口需要在header带上参数:"sk"

  * [参数类型]包含双引号的即为string,没有即为number

  * [Response约定]

    ```json
    通常code=0,即接口调用正常, code小于0,接口失败:
    {
        "code":0,
    }
    返回数据都放在data下面:
    {
        "code":0,
        "data":{
            "test":"hello"
        }
    }
    ```

    ​

* 带※的接口,没有特别说明不需要对接

#### 创建钱包

* Post /api/wallet

* Body

  ```json
  {
      "uuid":"abcdefg",
      "currency":"btc",
      "pwd":"1234567"
  }
  ```

* Response

  ```json
  {
      "code": 0,
      "data": {
          "addr": "mxuzZuktKBSmLGtYGJovGFernSWrXi7NC5"
      }
  }
  ```




#### ※获取钱包地址(无特殊需求请不要用此接口)

* POST /api/address

* Body

  ```json
  {
  	"uuid":"300101",
  	"currency":"usdt",
  	"pwd":"123456"
  }
  ```

* Response

  ```json
  {
      "code": 0,
      "data": {
          "addr": "msZ9f93Lj5UR8rTEsTUNMwXSkV8qXRgBA6"
      }
  }
  ```

  ​

#### 获取管理员钱包信息

* GET /api/admin/balance

* Response

  ```json
  {
      "code": 0,
      "data": {
          "btc": [
              {
                  "addr": "aaaaa",
                  "balance": 0.00000546
              }
          ],
          "usdt": [
              {
                  "addr": "bbbb",
                  "balance": 200
              }
          ]
      }
  }
  ```

  ​

  ​

#### 校验地址合法性(请在服务器调用，勿在客户端调用)

* GET /api/validate/:addr

* Response

  ```json
  {
      "code": 0
  }
  
  // 错误:
  {
      "code": -1000,
      "message": "wrong hex"
  }
  ```





#### 获取应用热钱包余额情况

* GET 

* Response 

  ```json
  {
      "code": 0,
      "data": {
          "eth": "4.318481598",
          "hrc": "999954616.0799999999992136"
      }
  }
  ```


#### 提币

* POST /api/admin/withdraw

* Body

  ```json
  {
  	"to_addr":"mfm1ZJiYJjieobtiTJM2EMAPRPZ9B1g2WS",
  	"currency":"lt",
  	"pwd":"123456",
  	"amount":0.1
  }
  ```

* Response

  ```json
  {
      "code":0,
      "data":{
  		"tx":"0x123123"//交易hash
      }
  }
  ```

  ​



#### 充值回调

* POST 你的callback_url

* Body

  ```json
  {
      "currency":"btc",
      "token":"",
      "charge_amt":0.011, //充值金额
      "uuid":"xaasad",
      "from_addr":"0x0000",
      "to_addr":"0x000",
      "tx":"0x0000"
  }
  ```

* No Response


