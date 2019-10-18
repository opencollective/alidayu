# 阿里大于(鱼) - v2.0

[![Latest Stable Version](https://poser.pugx.org/flc/alidayu/v/stable)](https://packagist.org/packages/flc/alidayu)
[![Total Downloads](https://poser.pugx.org/flc/alidayu/downloads)](https://packagist.org/packages/flc/alidayu)
[![Financial Contributors on Open Collective](https://opencollective.com/alidayu/all/badge.svg?label=financial+contributors)](https://opencollective.com/alidayu) ![php>=5.4](https://img.shields.io/badge/php->%3D5.4-orange.svg?maxAge=2592000)
[![License](https://poser.pugx.org/flc/alidayu/license)](https://packagist.org/packages/flc/alidayu)
[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)
[![LICENSE](https://img.shields.io/badge/license-Anti%20996-blue.svg)](https://github.com/996icu/996.ICU/blob/master/LICENSE)

> PS：**阿里短信** [https://github.com/flc1125/dysms](https://github.com/flc1125/dysms)

## 更新

#### v2.0.6 (2017-08-12)

- fixed [#6](https://github.com/flc1125/alidayu/issues/6)

#### v2.0.5 (2017-01-25)

- 修复autoload.php https://github.com/flc1125/alidayu/issues/5

#### v2.0.4 (2016-10-25)

- 新增自动载入功能（不依靠composer）
- 新增Client::request快捷调用方法

#### v2.0.3 (2016-10-12)

- 新增沙箱配置

## 功能

- `通过` [短信发送](docs/alibaba_aliqin_fc_sms_num_send.md)
- `通过` [短信发送记录查询](docs/alibaba_aliqin_fc_sms_num_query.md)
- `通过` [文本转语音通知](docs/alibaba_aliqin_fc_tts_num_singlecall.md)
- `通过` [语音通知](docs/alibaba_aliqin_fc_voice_num_singlecall.md)
- `待测` [多方通话](docs/alibaba_aliqin_fc_voice_num_doublecall.md)
- `待测` [流量直充](docs/alibaba_aliqin_fc_flow_charge.md)
- `待测` [流量直充查询](docs/alibaba_aliqin_fc_flow_query.md)
- `待测` [流量直充分省接口](docs/alibaba_aliqin_fc_flow_charge_province.md)
- `通过` [流量直充档位表](docs/alibaba_aliqin_fc_flow_grade.md)
- [辅助方法](docs/support.md)

> **`待测`**：因个人开发者，阿里大于权限相对较低。暂时无法测试；功能已开发，如测试可用，请告知~~

## 环境

- PHP >= 5.4
- [composer](https://getcomposer.org/)

## 安装

```shell
composer require flc/alidayu
```

或

```php
require '/path/to/alidayu/autoload.php';
```

## 使用

```php
<?php
use Flc\Alidayu\Client;
use Flc\Alidayu\App;
use Flc\Alidayu\Requests\AlibabaAliqinFcSmsNumSend;
use Flc\Alidayu\Requests\IRequest;

// 配置信息
$config = [
    'app_key'    => '*****',
    'app_secret' => '************',
    // 'sandbox'    => true,  // 是否为沙箱环境，默认false
];


// 使用方法一
$client = new Client(new App($config));
$req    = new AlibabaAliqinFcSmsNumSend;

$req->setRecNum('13312311231')
    ->setSmsParam([
        'number' => rand(100000, 999999)
    ])
    ->setSmsFreeSignName('叶子坑')
    ->setSmsTemplateCode('SMS_15105357');

$resp = $client->execute($req);

// 使用方法二
Client::configure($config);  // 全局定义配置（定义一次即可，无需重复定义）

$resp = Client::request('alibaba.aliqin.fc.sms.num.send', function (IRequest $req) {
    $req->setRecNum('13312311231')
        ->setSmsParam([
            'number' => rand(100000, 999999)
        ])
        ->setSmsFreeSignName('叶子坑')
        ->setSmsTemplateCode('SMS_15105357');
});

// 返回结果
print_r($resp);
print_r($resp->result->model);
?>
```

## 帮助

- 意见、BUG反馈： https://github.com/flc1125/alidayu/issues

## 支持

- 官方网址： https://www.alidayu.com/
- 官方API文档： https://api.alidayu.com/doc2/apiList.htm
- composer： https://getcomposer.org/

## 捐赠

如果你觉得本扩展对你有帮助，请捐赠以表支持，谢谢~~

<table>
    <tr>
        <td align="center"><img src="https://flc.io/static/images/wechat.jpg" width="220"><p>微信</p></td>
        <td align="center"><img src="https://flc.io/static/images/alipay.jpg" width="220"><p>支付宝</p></td>
    </tr>
</table>

## Contributors

### Code Contributors

This project exists thanks to all the people who contribute. [[Contribute](CONTRIBUTING.md)].
<a href="https://github.com/flc1125/alidayu/graphs/contributors"><img src="https://opencollective.com/alidayu/contributors.svg?width=890&button=false" /></a>

### Financial Contributors

Become a financial contributor and help us sustain our community. [[Contribute](https://opencollective.com/alidayu/contribute)]

#### Individuals

<a href="https://opencollective.com/alidayu"><img src="https://opencollective.com/alidayu/individuals.svg?width=890"></a>

#### Organizations

Support this project with your organization. Your logo will show up here with a link to your website. [[Contribute](https://opencollective.com/alidayu/contribute)]

<a href="https://opencollective.com/alidayu/organization/0/website"><img src="https://opencollective.com/alidayu/organization/0/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/1/website"><img src="https://opencollective.com/alidayu/organization/1/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/2/website"><img src="https://opencollective.com/alidayu/organization/2/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/3/website"><img src="https://opencollective.com/alidayu/organization/3/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/4/website"><img src="https://opencollective.com/alidayu/organization/4/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/5/website"><img src="https://opencollective.com/alidayu/organization/5/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/6/website"><img src="https://opencollective.com/alidayu/organization/6/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/7/website"><img src="https://opencollective.com/alidayu/organization/7/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/8/website"><img src="https://opencollective.com/alidayu/organization/8/avatar.svg"></a>
<a href="https://opencollective.com/alidayu/organization/9/website"><img src="https://opencollective.com/alidayu/organization/9/avatar.svg"></a>

## License

- MIT
- Anti 996
