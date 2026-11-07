# 无法映射的语法清单

共 17 条。这些不是解析失败，而是 Loon/Surge 的语法在 Egern 里没有等价字段，
或语义需要人工判断。全部保留来源模块与原始行，未静默丢弃。

## rewrite（12）

- **高德地图** — 无法映射的动作: response.json.jq_file("https://loon.103516.xyz/JQLang/Amap/A
  ```
  response if ${url} ~= /^https:\/\/m5\.amap\.com\/ws\/shield\/scene\/recommend\?/i then response.json.jq_file("https://loon.103516.xyz/JQLang/Amap/Amap.recommend.jq")
  ```
- **哔哩哔哩** — 无法映射的动作: response.body.mock("json", `{"code":0,"message":"OK","ttl":1
  ```
  response if ${url} ~= /^https:\/\/app\.bilibili\.com\/x\/v2\/splash\/list\?/i then response.body.mock("json", `{"code":0,"message":"OK","ttl":1,"data":{"max_time":0,"min_interval":31536000,"pull_interval":31536000,"keep_ids":[],"show":[],"list":[{}],"splash_request_id":""}}`, 200)
  ```
- **哔哩哔哩** — 无法映射的动作: response.body.mock("json", `{"code":-404,"message":"-404","t
  ```
  response if ${url} ~= /^https:\/\/ap[ip]\.bilibili\.com\/x\/(resource\/(top\/activity|patch\/tab(\/v2)?)|v2\/search\/square|vip\/ads\/materials)\?/i then response.body.mock("json", `{"code":-404,"message":"-404","ttl":1,"data":null}`, 200)
  ```
- **哔哩哔哩** — 无法映射的动作: response.body.mock("json", `{"code":0,"data":{"closeType":"c
  ```
  response if ${url} ~= /^https:\/\/api\.bilibili\.com\/pgc\/activity\/deliver\/material\/receive\?/i then response.body.mock("json", `{"code":0,"data":{"closeType":"close_win","container":[],"showTime":""},"message":"success"}`, 200)
  ```
- **哔哩哔哩** — body.mock 返回固定二进制体，需 map_locals 承载
  ```
  response if ${url} == "https://grpc.biliapi.net/bilibili.app.interface.v1.Teenagers/ModeStatus" then response.body.mock("text", "AAAAABMKEQgCEgl0ZWVuYWdlcnMgAioA", 200, true) | response.header.set("grpc-status", "0")
  ```
- **哔哩哔哩** — body.mock 返回固定二进制体，需 map_locals 承载
  ```
  response if ${url} == "https://grpc.biliapi.net/bilibili.app.interface.v1.Search/DefaultWords" then response.body.mock("text", "AAAAACEaHeaQnOe0ouinhumikeOAgeeVquWJp+aIlnVw5Li7KAE=", 200, true) | response.header.set("grpc-status", "0")
  ```
- **哔哩哔哩** — body.mock 返回固定二进制体，需 map_locals 承载
  ```
  response if ${url} ~= /^https:\/\/grpc\.biliapi\.net\/bilibili\.app\.(view\.v1\.View\/TFInfo|viewunite\.v1\.View\/(PlayPause|ViewEndPage))$/i then response.body.mock("text", "AAAAAAA=", 200, true) | response.header.set("grpc-status", "0")
  ```
- **哔哩哔哩** — 无法映射的动作: response.json.jq_file("https://loon.103516.xyz/JQLang/Bilibi
  ```
  response if ${url} ~= /^https:\/\/app\.bilibili\.com\/x\/resource\/show\/tab\/v2\?/i then response.json.jq_file("https://loon.103516.xyz/JQLang/Bilibili/Bilibili.tab.jq")
  ```
- **哔哩哔哩** — 无法映射的动作: response.json.jq_file("https://loon.103516.xyz/JQLang/Bilibi
  ```
  response if ${url} ~= /^https:\/\/app\.bilibili\.com\/x\/v2\/account\/mine(\/ipad)?\?/i then response.json.jq_file("https://loon.103516.xyz/JQLang/Bilibili/Bilibili.mine.jq")
  ```
- **粉笔** — body.mock 返回固定二进制体，需 map_locals 承载
  ```
  response if ${url} ~= /^https:\/\/keapi\.fenbi\.com\/app\/(iphone|ipad)\/position_resource\/get_home_banners\?.*position_resource_type=1/i then response.body.mock("json", "{\"code\":1,\"msg\":\"\",\"data\":{\"positionResourceType\":1,\"payload\":{\"items\":[{\"id\":17868,\"courseSetId\":2,\"content\
  ```
- **Reddit** — 无法映射的动作: response.json.jq_file("https://kelee.one/Resource/JQLang/Red
  ```
  response if ${url} ~= /^https?:\/\/gql(-fed)?\.reddit\.com/i then response.json.jq_file("https://kelee.one/Resource/JQLang/Reddit/Reddit_remove_ads.jq")
  ```
- **百度贴吧** — body.mock 返回固定二进制体，需 map_locals 承载
  ```
  response if ${url} ~= /^https?:\/\/tieba\.baidu\.com\/mo\/q\/search\/startPage\?/i then response.body.mock("json", "{\"no\":0,\"error\":\"success\"}", 200)
  ```

## script（3）

- **启动页去广告 Ultra+（yfamilys）** — 缺少 script-path
  ```
  spotify-qx-header=type=http-response,pattern=^https:\/\/(spclient\.wg\.spotify\.com|.*-spclient\.spotify\.com(:443)?)\/user-customization-service\/v1\/customize$ url script-request-header https://raw.githubusercontent.com/app2smile/rules/master/js/spotify-qx-header.js
  ```
- **YouTube** — 缺少 script-path
  ```
  cron "0 * * * *" then script("https://raw.githubusercontent.com/devchristian1337/loon-plugins/refs/heads/main/Scripts/YouTube/request.min.js", {${blocked_channels_url}}) with tag="YouTube 定时更新屏蔽频道列表", timeout=10
  ```
- **YouTube** — 缺少 script-path
  ```
  generic then script("https://raw.githubusercontent.com/devchristian1337/loon-plugins/refs/heads/main/Scripts/YouTube/request.min.js", {${blocked_channels_url}}) with tag="YouTube 手动更新屏蔽频道", img_url="person.crop.circle.badge.xmark.system", timeout=10
  ```

## rewrite-header（2）

- **Spotify** — header 动作需人工映射
  ```
  request if ${url} ~= /^https:\/\/(spclient\.wg\.spotify\.com|.*-spclient\.spotify\.com(:443)?)\/user-customization-service\/v1\/customize/i then request.header.del("if-none-match")
  ```
- **YouTube** — header 动作需人工映射
  ```
  response if ${url} ~= /^https:\/\/(?:[\w-]+\.)*googlevideo\.com(?::443)?\//i then response.header.set("Alt-Svc", "clear")
  ```
