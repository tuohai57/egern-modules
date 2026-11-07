# 脚本镜像清单

- 原始引用：1,018 条，唯一 URL 214 个
- 镜像成功：196 个（3.57 MB，去重后 168 个文件）
- 镜像失败：18 个（保留原始 URL）
- 使用 Loon/Surge 全局对象：196 个
- 使用 Egern ctx 体系：0 个
- 未做特征扫描（镜像补下时未记录）：0 个

## 失败清单

| 原始 URL | 原因 |
|---|---|
| `https://github.com/Biliverse/ADBlock/releases/download/v0.7.5/request.bundle.js` | all sources failed |
| `https://github.com/Biliverse/ADBlock/releases/download/v0.7.5/response.bundle.js` | all sources failed |
| `https://github.com/Biliverse/Global/releases/download/v0.9.3/request.bundle.js` | all sources failed |
| `https://github.com/Biliverse/Global/releases/download/v0.9.3/response.bundle.js` | all sources failed |
| `https://he2o.vercel.app/Resource/-Rewrite/anyehttp/wyy-s.js` | all sources failed |
| `https://loon.103516.xyz/Script/NeteaseMusic/CloudMusic.vip.js` | all sources failed |
| `https://loon.103516.xyz/Script/NeteaseMusic/NeteaseMusic.ads.js` | all sources failed |
| `https://loon.103516.xyz/Script/RedNote/RedNote.feedtime.js` | all sources failed |
| `https://loon.103516.xyz/Script/WeiBo/WeiBo.ads.js` | all sources failed |
| `https://raw.githubusercontent.com/ddgksf2013/Scripts/master/dict.js` | all sources failed |
| `https://raw.githubusercontent.com/ddgksf2013/Scripts/refs/heads/master/dict.js` | all sources failed |
| `https://raw.githubusercontent.com/fmz200/wool_scripts/main/Scripts/coolapk.js` | all sources failed |
| `https://royal-block-f6b1.q00.workers.dev/scripts/redbook.ads.js` | all sources failed |
| `https://rucu6.pages.dev/Scripts/amap.js` | all sources failed |
| `https://rucu6.pages.dev/Scripts/pinduoduo.js` | all sources failed |
| `https://rucu6.pages.dev/Scripts/weibo.js` | all sources failed |
| `https://rucu6.pages.dev/Scripts/xiaohongshu.js` | all sources failed |
| `https://rucu6.pages.dev/Scripts/zhihu.js` | all sources failed |

这些地址在当前网络返回 502/504 或 SSL EOF，备用 CDN（gitmirror / statically / gcore）同样不可达。
对应模块仍可使用规则与 MITM 部分，但依赖该脚本的功能不会生效。