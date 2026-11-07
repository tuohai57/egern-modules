# 模块转换明细

| # | 模块 | 文件 | 源格式 | 规则 | URL重写 | Body | 脚本 | MapLocal | MITM |
|---:|---|---|---|---:|---:|---:|---:|---:|---:|
| 0 | 0. 优先级补丁 | `00-override.yaml` | egern-yaml | 14 | 0 | 0 | 0 | 0 | 0 |
| 1 | HTTPDNS 拦截器 | `httpdns-blocker.yaml` | lpx | 162 | 6 | 0 | 0 | 0 | 4 |
| 2 | 广告平台拦截器 | `ad-platform-blocker.yaml` | lpx | 346 | 4 | 0 | 0 | 0 | 3 |
| 3 | 跳过代理检测 | `skip-proxy-detection.yaml` | lpx | 1 | 0 | 0 | 0 | 0 | 0 |
| 4 | 墨鱼去开屏 | `splash-moyu.yaml` | lpx | 5 | 442 | 17 | 42 | 0 | 437 |
| 5 | 广告拦截合集（loonlab） | `adblock-collection.yaml` | lpx | 0 | 925 | 30 | 71 | 0 | 669 |
| 6 | CMS 广告拦截 | `cms-adblocker.yaml` | lpx | 0 | 1 | 0 | 20 | 0 | 24 |
| 7 | 广告拦截（yfamilys） | `adblock-yfamilys.yaml` | module | 0 | 264 | 0 | 0 | 0 | 153 |
| 8 | 启动页去广告 Ultra+（yfamilys） | `splash-ultra.yaml` | sgmodule | 0 | 864 | 0 | 372 | 1323 | 1273 |
| 9 | 广告拦截&净化合集 | `adblock-clean-full.yaml` | module | 2993 | 517 | 0 | 255 | 801 | 931 |
| 10 | 知乎 | `app-zhihu.yaml` | lpx | 11 | 38 | 16 | 10 | 0 | 1 |
| 11 | 微博 | `app-weibo.yaml` | lpx | 38 | 19 | 1 | 22 | 0 | 3 |
| 12 | 小红书 | `app-xiaohongshu.yaml` | lpx | 6 | 5 | 4 | 13 | 0 | 10 |
| 13 | 闲鱼 | `app-xianyu.yaml` | lpx | 2 | 14 | 16 | 7 | 0 | 2 |
| 14 | 拼多多 | `app-pinduoduo.yaml` | lpx | 17 | 20 | 7 | 2 | 0 | 3 |
| 15 | 腾讯视频 | `app-tencent-video.yaml` | lpx | 29 | 0 | 0 | 0 | 0 | 0 |
| 16 | 百度网盘 | `app-baidu-netdisk.yaml` | lpx | 0 | 14 | 1 | 6 | 0 | 2 |
| 17 | 高德地图 | `app-amap.yaml` | lpx | 4 | 15 | 10 | 13 | 0 | 1 |
| 18 | 网易云音乐 | `app-netease-music.yaml` | lpx | 9 | 8 | 2 | 14 | 0 | 2 |
| 19 | B站净化（Sparkle） | `app-bilibili-sparkle.yaml` | sgmodule | 10 | 0 | 0 | 7 | 8 | 6 |
| 20 | B站重定向（BiliUniverse） | `app-bilibili-redirect.yaml` | sgmodule | 0 | 12 | 0 | 7 | 1 | 9 |
| 21 | B站去广告（BiliUniverse） | `app-bilibili-adblock.yaml` | sgmodule | 0 | 0 | 0 | 16 | 9 | 13 |
| 22 | B站全局（BiliUniverse） | `app-bilibili-global.yaml` | sgmodule | 0 | 0 | 0 | 18 | 1 | 8 |
| 23 | 哔哩哔哩 | `app-bilibili.yaml` | lpx | 11 | 3 | 9 | 5 | 0 | 6 |
| 24 | 酷安 | `app-coolapk.yaml` | lpx | 0 | 1 | 7 | 1 | 0 | 2 |
| 25 | 什么值得买 | `app-smzdm.yaml` | lpx | 1 | 9 | 16 | 0 | 0 | 12 |
| 26 | 滴滴出行 | `app-didi.yaml` | lpx | 43 | 18 | 30 | 0 | 0 | 21 |
| 27 | Spotify | `app-spotify.yaml` | lpx | 2 | 4 | 0 | 6 | 0 | 2 |
| 28 | YouTube | `app-youtube.yaml` | lpx | 4 | 1 | 0 | 9 | 0 | 7 |
| 29 | 爱奇艺 | `app-iqiyi.yaml` | sgmodule | 45 | 0 | 0 | 13 | 4 | 2 |
| 30 | 淘宝 | `app-taobao.yaml` | sgmodule | 32 | 0 | 0 | 2 | 9 | 3 |
| 31 | 京东 | `app-jd.yaml` | sgmodule | 16 | 1 | 0 | 1 | 0 | 2 |
| 32 | 快手 | `app-kuaishou.yaml` | sgmodule | 4 | 0 | 0 | 0 | 2 | 8 |
| 33 | 芒果TV | `app-mgtv.yaml` | sgmodule | 29 | 1 | 0 | 7 | 5 | 1 |
| 34 | QQ音乐 | `app-qqmusic.yaml` | sgmodule | 32 | 5 | 0 | 0 | 2 | 3 |
| 35 | 酷我音乐 | `app-kuwo.yaml` | sgmodule | 17 | 0 | 0 | 5 | 1 | 6 |
| 36 | 汽水音乐 | `app-qishui.yaml` | sgmodule | 59 | 4 | 0 | 0 | 2 | 6 |
| 37 | 喜马拉雅 | `app-ximalaya.yaml` | sgmodule | 9 | 0 | 0 | 0 | 15 | 8 |
| 38 | 优酷 | `app-youku.yaml` | sgmodule | 28 | 0 | 0 | 6 | 1 | 3 |
| 39 | 斗鱼直播 | `app-douyu.yaml` | sgmodule | 3 | 5 | 0 | 0 | 5 | 5 |
| 40 | 虎牙直播 | `app-huya.yaml` | sgmodule | 7 | 2 | 0 | 0 | 2 | 4 |
| 41 | 美团 | `app-meituan.yaml` | sgmodule | 10 | 0 | 0 | 0 | 0 | 0 |
| 42 | 懂车帝 | `app-dcar.yaml` | sgmodule | 2 | 0 | 0 | 0 | 0 | 0 |
| 43 | WPS / 金山 | `app-wps.yaml` | sgmodule | 33 | 0 | 0 | 0 | 0 | 0 |
| 44 | X 网页版 | `app-x-web.yaml` | module | 0 | 0 | 0 | 1 | 0 | 1 |
| 45 | Twitter (X) | `app-twitter.yaml` | sgmodule | 6 | 0 | 0 | 0 | 0 | 0 |
| 46 | Facebook | `app-facebook.yaml` | sgmodule | 3 | 0 | 0 | 0 | 0 | 0 |
| 47 | TikTok | `app-tiktok.yaml` | sgmodule | 2 | 0 | 0 | 0 | 0 | 0 |
| 48 | 得物 | `app-dewu.yaml` | lpx | 0 | 7 | 3 | 0 | 0 | 1 |
| 49 | 瑞幸咖啡 | `app-luckin.yaml` | lpx | 0 | 8 | 0 | 0 | 0 | 1 |
| 50 | 米游社 | `app-miyoushe.yaml` | lpx | 0 | 3 | 3 | 0 | 0 | 2 |
| 51 | 小黑盒 | `app-xiaoheihe.yaml` | lpx | 0 | 1 | 1 | 0 | 0 | 1 |
| 52 | 马蜂窝 | `app-mafengwo.yaml` | lpx | 1 | 1 | 2 | 0 | 0 | 1 |
| 53 | 淘票票 | `app-taopiaopiao.yaml` | lpx | 0 | 3 | 3 | 0 | 0 | 1 |
| 54 | 大麦 | `app-damai.yaml` | lpx | 0 | 2 | 3 | 0 | 0 | 1 |
| 55 | 起点读书 | `app-qidian.yaml` | lpx | 0 | 13 | 4 | 0 | 0 | 2 |
| 56 | 百度文库 | `app-baidu-wenku.yaml` | lpx | 0 | 8 | 4 | 0 | 0 | 2 |
| 57 | 粉笔 | `app-fenbi.yaml` | lpx | 0 | 10 | 2 | 0 | 0 | 4 |
| 58 | 小象超市 | `app-xiaoxiang.yaml` | lpx | 0 | 7 | 0 | 1 | 0 | 3 |
| 59 | 叮咚买菜 | `app-dingdong.yaml` | lpx | 3 | 12 | 7 | 0 | 0 | 3 |
| 60 | 番茄小说 | `app-fanqie.yaml` | lpx | 34 | 0 | 0 | 0 | 0 | 0 |
| 61 | 12306 | `app-12306.yaml` | lpx | 1 | 0 | 1 | 1 | 0 | 2 |
| 62 | 夸克 | `app-quark.yaml` | lpx | 0 | 2 | 1 | 0 | 0 | 2 |
| 63 | 豆瓣 | `app-douban.yaml` | lpx | 0 | 6 | 0 | 0 | 0 | 3 |
| 64 | 阿里云盘 | `app-aliyundrive.yaml` | lpx | 1 | 2 | 0 | 2 | 0 | 3 |
| 65 | Reddit | `app-reddit.yaml` | lpx | 0 | 0 | 0 | 0 | 0 | 2 |
| 66 | Line | `app-line.yaml` | lpx | 20 | 14 | 0 | 0 | 0 | 17 |
| 67 | 美颜相机 | `app-meiyan.yaml` | lpx | 1 | 2 | 2 | 1 | 0 | 1 |
| 68 | 凤凰新闻 | `app-ifeng.yaml` | lpx | 0 | 12 | 10 | 0 | 0 | 4 |
| 69 | 百度贴吧 | `app-tieba.yaml` | lpx | 2 | 5 | 10 | 1 | 0 | 2 |
| 70 | Google 搜索重定向 | `app-google-redirect.yaml` | lpx | 0 | 2 | 0 | 0 | 0 | 1 |
| 71 | 微信公众号 | `app-wechat-mp.yaml` | lpx | 1 | 2 | 0 | 0 | 0 | 1 |
| 72 | 微信小程序 | `app-wechat-mini.yaml` | lpx | 6 | 112 | 6 | 12 | 0 | 93 |
| 73 | 微信本体 | `app-wechat.yaml` | lpx | 12 | 166 | 7 | 24 | 0 | 117 |
| 74 | 微信外部链接解锁 | `app-wechat-link.yaml` | lpx | 0 | 0 | 0 | 1 | 0 | 2 |
| 75 | iRingo 天气 | `module-iringo-weather.yaml` | egern-yaml | 4 | 0 | 0 | 5 | 0 | 1 |
| 76 | iRingo 地图 | `module-iringo-maps.yaml` | egern-yaml | 6 | 0 | 0 | 6 | 0 | 1 |
| 77 | 网易云 SVIP 解锁 | `module-netease-svip.yaml` | sgmodule | 6 | 5 | 0 | 8 | 7 | 1 |
| 78 | B 站画质解锁 | `module-bilibili-quality.yaml` | module | 0 | 0 | 0 | 1 | 0 | 1 |
| 79 | B 站皮肤 | `module-bilibili-skin.yaml` | sgmodule | 0 | 0 | 0 | 3 | 0 | 2 |
| 80 | Sub-Store | `module-substore.yaml` | yaml | 0 | 0 | 0 | 0 | 0 | 0 |
| 81 | BoxJs | `module-boxjs.yaml` | sgmodule | 0 | 0 | 0 | 1 | 0 | 4 |
| 82 | 插件中心（QuantumultXMark） | `module-pluginhub.yaml` | egern-yaml | 0 | 0 | 6 | 0 | 0 | 1 |

合计：83 个模块，4143 条规则，3627 条 URL 重写，241 条 Body 重写，1018 条脚本，2198 条 Map Local，3939 个 MITM 主机。