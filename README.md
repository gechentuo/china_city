# ChinaCity 省市区级联选择

[![Build Status](https://travis-ci.org/saberma/china_city.png?branch=master)](https://travis-ci.org/saberma/china_city)

![china_city](http://cl.ly/image/3c212i1e3b1T/ScreenFlow.mp4.gif)

## 简介

这是一个基于 Rails Engine 开发的插件，为 Rails 项目增加省市区三级（或者省市 二级）选择框，可用于实现收货地址等信息的录入。

## 安装

### Gemfile

    gem 'china_city'

### app/assets/javascripts/application.js

    //= require 'jquery'
    //= require 'china_city/jquery.china_city'

### config/routes.rb

    mount ChinaCity::Engine => '/china_city' if defined?(ChinaCity)

## 使用

在页面中加入选择框，示例代码使用 slim 格式

```ruby
  .city-group
    select.city-select
      option --省份--
      = options_for_select(ChinaCity.list)
    select.city-select
      option --城市--
    select.city-select
      option --地区--
```

请留意：所有选择框都要有 `city-select` class，并都包含于 class='city-group' 的 DOM 元素之下。

选择后的值为国家地区编码，如深圳市的为 `440300`，可通过调用 `ChinaCity.get('440300')` 将编码转化为城市名称。

## 贡献

```bash
git clone git@github.com:saberma/china_city.git
cd china_city
cd test/dummy
rails server # http://localhost:3000/china_city
```
