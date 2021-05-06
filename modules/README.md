
# 使用须知
开启MITM
## 微博
### 禁用微博视频流
https://raw.githubusercontent.com/broven/surge/main/modules/weibo/disableWeiboFeed/disableWbVideoFeed.sgmodule
## All Real ip
https://raw.githubusercontent.com/keyvchan/dotfiles/6bf85be84749f5a5d0226aaba5efa4399d8d3dbc/surge/module/Real%20IP%20for%20all%20domains.sgmodule


## 疑难杂症
### 脚本开启后无效?
有以下几种可能, 可能性依次递减
- 其他的脚本, 在添加hostname时, 没有使用 %APPEND%, 导致覆盖, 检查下 其他脚本
- 看看你的配置文件里有没有 `hostname-disabled`, 干掉
- 脚本弃坑了
