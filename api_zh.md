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




#### 查询余额

* GET /api/account/balance/:currency/:uuid

* Response

  ```json
  {
      "code":0,
      "data":{
          "balance":0.999,
          "currency":"btc"
      }
  }
  ```

  ​

#### Admin转账

* POST /api/adminTransfer

* Body

  ```json
  {
      "uuid":"abcdefg",
      "from_addr":"0xaaaa",
      "to_addr":"0x99999",
      "amount":0.1,
      "currency":"btc"
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

  ​

  ​	

#### 转账

* POST /api/transfer

* Body

  ```json
  {
      "uuid":"abcdefg",
      "from_addr":"0xaaaa",
      "to_addr":"0x99999",
      "amount":0.1,
      "currency":"btc"
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



#### 根钱包创建(TODO)

* POST /api/wallet/root

* Response

  ​



#### 充值回调地址设置

* POST /api/rechargeCallback

* Body

  ```json
  {
      "callback_url":"http://www.callback.com/api/xx"
  }
  ```

* Response

  ```json
  {
      "code":0
  }
  ```



#### 充值回调

* POST 你的callback_url

* Body

  ```json
  {
      "currency":"btc",
      "charge_amt":0.011, //充值金额
      "uuid":"xaasad",
      "from_addr":"0x0000",
      "to_addr":"0x000",
      "tx":"0x0000"
  }
  ```

* No Response


