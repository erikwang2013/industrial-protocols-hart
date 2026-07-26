# HART 协议包 — 4-20mA FSK 调制，支持 PV/回路电流读取，串口通信

> [English](README.en.md)

HART (Highway Addressable Remote Transducer) 协议，4-20mA 模拟信号上叠加 FSK 数字信号。通过 HART 调制解调器（USB/串口）通信。

## 安装

```bash
composer require erikwang2013/industrial-protocols-hart
```

## 架构

HartDriver（串口）→ HartFrame 帧编解码。支持主变量(PV)、回路电流、设备信息读取。

## 功能

主变量 PV 读取、回路电流(mA) 读取、设备信息（厂商/型号/版本）、FSK 帧编解码、HartException 异常

## 使用说明

```php
$conn = $kernel->getConnectionManager()->connect('hart-device');
$conn->read('pv');             // 主变量
$conn->read('loop_current');   // 回路电流
$conn->read('device_info');    // 厂商/型号/版本
```

## 配置示例

```php
'devices' => [
    'hart-device' => [
        'protocol' => 'hart',
        'device' => '/dev/ttyUSB1',  // HART 调制解调器
        'address' => 0,              // 0=单点, 1-15=多点
        'timeout' => 5000,
    ],
],
```

## 兼容框架

Laravel / Webman / Hyperf / ThinkPHP / Yii2 / Plain PHP

## 系统要求

- PHP >= 8.1
- HART 调制解调器（USB/串口）
- erikwang2013/industrial-protocols-kernel

## License

MIT — Copyright (c) 2026 erik <erik@erik.xyz> — https://erik.xyz
