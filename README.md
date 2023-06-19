AliyunOSS
---------

```
    ___     __    _                                    ____    _____   _____
   /   |   / /   (_)   __  __  __  __   ____          / __ \  / ___/  / ___/
  / /| |  / /   / /   / / / / / / / /  / __ \        / / / /  \__ \   \__ \
 / ___ | / /   / /   / /_/ / / /_/ /  / / / /       / /_/ /  ___/ /  ___/ /
/_/  |_|/_/   /_/    \__, /  \__,_/  /_/ /_/        \____/  /____/  /____/
                    /____/
```

AliyunOSS 是阿里云 OSS 官方 SDK 的 Composer 封装，支持任何 PHP 项目


## 更新记录

* 2023-06-29 `Release v1.0.0`

## 安装

安装有两种方式：

### ① 直接编辑配置文件

将以下内容增加到 composer.json：

```json
require: {
    "luminescent/aliyun-oss": "~2.0"
}
```

然后运行 `composer update`。

### ② 执行命令安装

运行命令：

```bash
composer require luminescent/aliyun-oss
```

## 使用（以 Laravel 为例）

### 构建 Service 文件

新建 `app/services/OSS.php`，内容可参考：[OSS.php](https://github.com/johnlui/AliyunOSS/blob/master/example/OSS.php)，然后修改配置：

```php
... ...

  private $city = '青岛';

  // 经典网络 or VPC
  private $networkType = '经典网络';
  
  private $AccessKeyId = '';
  private $AccessKeySecret = '';

... ...
```

### 放入自动加载

#### 遵循 psr-0 的项目（如Laravel 4、CodeIgniter、TinyLara）中：
在 `composer.json` 中 `autoload -> classmap` 处增加配置：

```json
"autoload": {
    "classmap": [
      "app/services"
    ]
  }
```
然后运行 `composer dump-autoload`。

#### 遵循 psr-4 的项目（如 Laravel 5、Symfony）中：

无需配置，保证目录 `App/Services` 和命名空间 `namespace App\Services;` 一致即可自动加载。

### 使用

```php
use App\Services\OSS;

// 在外网上传一个文件并指定 options 如：Content-Type 类型
// 更多 options 见：https://github.com/johnlui/AliyunOSS/blob/master/src/oss/src/Aliyun/OSS/OSSClient.php#L142-L148
OSS::publicUpload('bucket', '目标 object 名', '本地文件路径', [
    'ContentType' => 'application/pdf',
    ... ...
]);
```

更多用法等待着你去[发现](https://github.com/johnlui/AliyunOSS/blob/master/example/OSS.php)。

## 反馈

有问题请到 http://lvwenhan.com/laravel/425.html 下面留言。

## License
除 “版权所有（C）阿里云计算有限公司” 的代码文件外，遵循 [MIT license](http://opensource.org/licenses/MIT) 开源。


