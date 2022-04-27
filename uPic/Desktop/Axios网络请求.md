# Axios网络请求

## 1、Axios简单介绍

### 1.1 前端ajax框架选型

**XMLHTTPRequest**

**jQuery**

**Vue & axios**

* Vuel.x -> vue-resource
* Vue2.x -> axios

### 1.2 axios简介及优势

* 基于Promise
* 用在浏览器和Node JS环境
* 是一个HTTP请求类库

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_11-15-26.png)

### 1.3 支持多种请求方法

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_11-22-41.png)

### 1.4 浏览器兼容性

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_11-23-32.png)

## 2、Axios的基本用法

### 2.1 安装使用axios

* 文件引用方式
* npm安装方式 `npm i axlos --save`
* yarn安装方式
* 在vue项目中引入axios模块

### 2.2 axios基本概念

* 提供免费的HTTP请求及相应服务网站http://httpbin.org
* 使用axios(config)发送http请求,config为该请求的配置信息对象
* axios是基于Promise的HTTP客户端,所以可以
* 使用then、catch对请求结果进行处理.

### 2.3 axios发送GET请求

* axios.get等同于axios使用methodget
* get请求可以在url上带参数,或者使用params传参

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_11-39-20.png)

#### 2.4 axios发送POST请求

* axios.post等同于axios使用method:post
* post请求使用data传参

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_11-43-54.png)

#### 2.5 axios发送并行请求

* 某些异步网络请求结果处理有一定的顺序
* axios.all()

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_11-43-54.png)

## 3、Axios的配置详情

#### 3.1 常用数据格式

* JSON数据格式
* 表单数据格式

#### 3.2 数据的转换



#### 3.3 文件上传与下载进度

* onDownloadProgress
* onUploadProgress

#### 3.4 axios请求配置

| url                    | method       | baseURL        | Headers                | Params           |
| ---------------------- | ------------ | -------------- | ---------------------- | ---------------- |
| paramsSerializer       | data         | timeout        | withCredentials(false) | apapter          |
| auth(Authorization 头) | responseType | xsrfCookieType | xsrfHeaderName         | maxContentLength |
| validate Status        | maxRedirects | httpAgent      | httpsAgent             | proxy            |
| cancelToken            |              |                |                        |                  |

```json
params: {
  id: 123,
  name: "aaa"
}
```

> data: string\obj\formData\file\blob
>
> responseType: json\blob\document\text\stream\arraybuffer

#### 3.5 axios响应数据结构

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_13-11-37.png)

#### 3.6 axios全局配置

* 针对大部分一致的内容，可以采用全局配置。
* 请求服务端根地址baseURL，通常是很多api使用统一的地址提供服务。
* Authorization的用户名密码信息等，不需要每次请求都进行设置
* timeout请求超时时间，也不需要每次请求都单独设置
* 全局设置的方式
* 配置的优先级：当defaults全局配置与局部config配置发生冲突的时候，
* 局部config配置的优先级要高于全局配置。

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_11-35-24.png)

## 4、Axios的实例与拦截器

#### 4.1 axios多实例的必要性

根据请求不同的服务主体，创建多个axios实例

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_13-17-49.png)

#### 4.2 创建axios实例

![](https://cdn.jsdelivr.net/gh/shiyouhan/img@master/uPic/Snipaste_2022-04-23_13-20-16.png)

#### 4.3 axios拦截器 

* 拦截器的作用就是针对所有请求和响应做拦截，所谓的拦截就是统一修改请求或响应的内容、参数、配置等信息

**request拦截器**

* 统一给请求加上JWT令牌
* loading处理

**response拦截器**

* 统一响应数据解析
* 统一的异常处理