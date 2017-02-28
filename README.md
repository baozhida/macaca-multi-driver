# 简介
支持ios多台设备并行执行相同的case，也支持ios和android并行，或者android多台并行。

用Java基于wd.java编写的自动化测试框架，maven工程，集成testng和Ant维护用例和生成测试报告，底层框架全部来自https://github.com/macacajs

使用testng控制并发，改造了默认的report结果，在case错误时候，自动截屏保存图片，并把图片添加在报告文件中，方便检查定位。


# macaca多台ios真机设备并行 iproxy设置存在bug，多个设备都会使用8900端口，无法正常判断端口是否可用

此版本需要修改macaca-ios代码，初始化ios真机driver时候可以指定iproxy端口

替换原本中的,即可使用
```
macaca-ios.js
```
## 初始化时候传入代理端口

```
        porps.put("proxyPort", Integer.parseInt(proxyport));

```

# 环境信息

Eclipse: Mars.2 (4.5.2)

macaca: 1.2.0

macacaclient: 2.0.1

testng：9.6.10

ant: eclipse自带

# 下载Macaca套件

下载Macaca套件，全局安装，包括，macaca-cli macaca-ios app-inspector macaca-android

```
npm install macaca-cli -g

npm install macaca-ios -g

npm install macaca-android -g

npm install app-inspector -g
```

MAC全局安装的路径分别如下：

```
/usr/local/lib/node_modules/macaca-cli
/usr/local/lib/node_modules/macaca-ios
/usr/local/lib/node_modules/macaca-android
/usr/local/lib/node_modules/app-inspector
```

# WebDriverAgent项目重签名

查找WebDriverAgent项目发现有两个，都需要使用xcode重新签名

我使用的是自己的苹果账号，有个限制就是，有效期是7天，过期之后需要重新签名，有个开发者账号最好，没有也能用，过期了再签一次就可以了。

 ```
/usr/local/lib/node_modules/app-inspector/node_modules/.1.0.41@webdriveragent/WebDriverAgent
/usr/local/lib/node_modules/macaca-ios/node_modules/.1.0.41@webdriveragent/WebDriverAgent
```
或者
```
/usr/local/lib/node_modules/macaca-ios/node_modules/webdriveragent/WebDriverAgent
/usr/local/lib/node_modules/macaca-inspector/node_modules/webdriveragent/WebDriverAgent
```
