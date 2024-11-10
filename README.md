<!--
 * @Author: yjjmh
 * @Date: 2023-11-16 09:51:51
 * @LastEditors: yjjmh hbczysls@163.com
 * @LastEditTime: 2024-11-10 17:49:10
 * @Description: 使用说明
-->

# 安装

方式一:
```sh
  yarn add @yjjmh/utils -S
```
方式二:
```sh
  npm install @yjjmh/utils -S
```
# 使用

方式一:

```JavaScript
  import utils from @yjjmh/utils

  utils.cookie.getItem({ key: "test" })
```
方式二:
```JavaScript
  import cookie from @yjjmh/utils;
  cookie.getItem({ key: "test" })
```
方式三:
```JavaScript
  import { cookieGetItem } from @yjjmh/utils
  cookie.getItem({ key: "test" })
  ```

# 当前支持的方法

## cookie

* getItem
  * 描述:
    * 从document.cookie中获取指定key的cookie值
  * 参数:
    * *key{String}: 要获取的cookie的key
  * 返回值：
    * {String}: 返回key对应的cookie值
    * {Undefined}: 不存在key对应的cookie值
  * 示例：
    * ```javascript
      getItem({ key: "test" })
      ```

* setItem
  * 描述:
    * 设置指定key的cookie值
  * 参数:
    * *key{String}: 设置cookie对应的名称
    * value{String}: 设置cookie对应的值
    * end{Number|Date|GMTString|String|Null|Infinity}: 过期时间，默认会话结束过期 Infinity永不过期
    * path{String|Null}: 设置cookie的路径，默认当前路径，路径必须绝对路径
    * domain{String|Null}: 设置cookie域名，默认为当前文档位置的路径的域名
    * secure{Boolean|Null}: 设置cookie是否只能被https传输
  * 返回值：
    * {Boolean}: 成功设置返回true，失败返回false
  * 示例：
    * ```javascript
      setItem({ key: "test", value: "123" })
      ```

* removeItem
  * 描述:
    * 从document.cookie中删除指定key的cookie值
  * 参数:
    * *key{String}: 要删除的cookie的key
    * path{String|Null}: cookie的路径，默认当前路径，路径必须绝对路径
    * domain{String|Null}: cookie域名，默认为当前文档位置的路径的域名
  * 返回值：
    * {Boolean}: 成功设置返回true，失败返回false
  * 示例：
    * ```javascript
      removeItem({ key: "test" })
      ```

* hasItem
  * 描述:
    * 从document.cookie中判断有没有对应的键值
  * 参数:
    * *key{String}: 要检测的cookie名称
  * 返回值：
    * {Boolean}: 存在返回true，不存在返回false
  * 示例：
    * ```javascript
      hasItem({ key: "test" })
      ```

* getAllKeys
  * 描述:
    * 从document.cookie中获取所有cookie名称组成的数组
  * 参数:
      无
  * 返回值：
    * {Array}: 包含所有cookie的名称组成的数组
  * 示例：
    * ```javascript
      getAllKeys()
      ```

* getAll
  * 描述:
    * 从document.cookie中获取cookie键值组成的对象
  * 参数:
      无
  * 返回值：
    * {Object}: 由cookie键值组成的对象，键为cookie名称，值为对应的值
  * 示例：
    * ```javascript
      getAll()
      ```
* removeAll
  * 描述:
    * 清空cookie中所有键值
  * 参数:
      无
  * 返回值：
    * {Boolean}: 成功清空返回true，失败返回false
  * 示例：
    * ```javascript
      removeAll()
      ```

## type

* getType
  * 描述:
    * 获取参数的类型
  * 参数:
    * payload{Any}: 需要获取类型的参数
  * 返回值：
    * {String}: 返回payload参数的类型 首字母大写 如 Boolean
  * 示例：
    * ```javascript
      getType({ payload: 123 }) // Number
      ```

* isType
  * 描述:
    * 判断传入的参数是否是某个类型
  * 参数:
    * payload{Any}: 待检测的数据
    * type{String}: 期望的数据类型
  * 返回值：
    * {Boolean}: 返回检测的结果 与预期类型相同返回true 否则返回false
  * 示例：
    * ```javascript
      isType({ payload: 123, type: "Number" }) // true
      ```

## date

* formatDate

  * 描述:
    * 格式化日期为指定的字符串格式
  * 参数:
    * date{Date|Number|String}: 要格式化的日期，省略默认为当前时间，支持时间戳，时间字符串或日期对象
    * format{String}: 格式化字符串，默认"yyyy-MM-dd HH:mm:ss", 注意大小写，大写M表示月份，小写m表示分钟， 大写H表示24小时制，小写h表示12小时制，大写S表示毫秒，小写s表示秒
  * 返回值：
    * {String}: 返回格式化后的日期字符串
  * 示例：
    * ```javascript
      formatDate({date: 1735660800000, format: "yyyy-MM-dd HH:mm:ss.S"})
      ```
* getBoundaryTime

  * 描述:
    * 获取某天的开始时间和结束时间对象
  * 参数:
    * date{Date|String}: 需要获取时间戳的日期
  * 返回值：
    * {Object}: 返回一天的开始和结束时间戳
  * 示例：
    * ```javascript
      getBoundaryTime({ date: "2020-1-1" }) // {"start": Date(), "end": Date()}
      ```


## utils

* formatNumber
  * 描述:
    * 格式化数字位数
  * 参数:
    * *payload{Number}: 要格式化的数值
    * int{Number}: 整数部分长度,默认为2位
    * dec{Number}: 小数部分长度,默认位0位
    * padInt{String}: 整数部分补位字符,默认使用0
    * padDec{String}: 小数部分补位字符,默认使用0
    * type{String}: 格式化类型 round 四舍五入 floor 向下取整 ceil 向上取整 discard 舍弃 默认为空，调用toFixed方法四舍五入
  * 返回值：
    * {String}: 格式化后的数值
  * 示例：
    * ```javascript
      formatNumber({payload:123.4567,int:4,dec:2}) // 0123.46
      ```

* getEnv
  * 描述:
    * 获取当前开发环境
  * 参数:
    * customRule{String}: 自定义校验规则-正则表达式,用于校验地址栏地址
  * 返回值：
    * {String}: dev - 开发环境  prod - 生产环境
  * 示例：
    * ```javascript
      getEnv({customRule: "dev-*"})
      ```
  
* pageTo
  * 描述:
    * 跳转到一个新地址
  * 参数:
    * *url{String}: 要跳转的地址
    * newTab{Boolean}: 是否用一个新的窗口打开
  * 返回值：
    无
  * 示例：
    * ```javascript
      pageTo({url:"https://www.baidu.com",newTab:true})
      ```

* deepCopy
  * 描述:
    * 获取当前开发环境
  * 参数:
    * *payload{Any}: 对象/数组或其他值
  * 返回值：
    * {Any}: 返回一个和传入的payload一样的值
  * 示例：
    * ```javascript
      deepCopy({payload:{a:1,b:[2,3],c:{d:4}}})
      ```

* downloadFile
  * 描述:
    * 下载文件
  * 参数:
    * *url{String}: 文件地址
    * name{String}: 保存文件名称
    * newTab{Any}: 是否打开一个新的窗口
    * forceDownload{Any}: 是否强制下载，不预览
    * MIMEType{String}: MIME类型,默认为"application/octet-stream"
  * 返回值：
    * {Object}: {status：下载是否成功， message：提示信息}
  * 示例：
    * ```javascript
      downloadFile({url:"https://www.baidu.com/img/bd_logo1.png",name:"logo"}).then(res=>{console.log(res)}).catch(err=>{console.log(err)})
      ```
