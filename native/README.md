# Egern 原生模块（Loon / Surge 重写版）

把 v11.1/v11.2 使用的 83 个模块从 Loon `.lpx` / Surge `.sgmodule` 重写为 **Egern 原生 YAML 模块**，并把它们引用的脚本全部镜像到本仓库，避免依赖国内不可达的源站。

## 目录

```
native/
├── modules/     83 个 Egern YAML 模块
├── scripts/     168 个脚本文件（覆盖 196 个原始 URL）
├── reports/     转换明细、未映射清单、脚本清单
└── README.md
```

主配置使用 `native/modules/<name>.yaml`，脚本地址为
`https://cdn.jsdelivr.net/gh/tuohai57/egern-modules@main/native/scripts/<sha1>.js`。

## 转换结果

| 项 | 数量 |
|---|---:|
| 源模块 | 83 |
| 转换成功 | **83 / 83** |
| 规则（rules） | 4,143 |
| URL 重写（url_rewrites） | 3,627 |
| Body 重写（body_rewrites） | 241 |
| 脚本（scriptings） | 1,018 |
| Map Local（map_locals） | 2,198 |
| MITM 主机（各模块内去重） | 3,939 |
| 无法映射的语法 | **17**（详见 `reports/unsupported.md`） |

## 字段映射依据

全部按 Egern 官方文档（egernapp.com/docs/configuration）执行，不是改后缀：

| Loon / Surge | Egern |
|---|---|
| `[Rule]` `DOMAIN/DOMAIN-SUFFIX/...` | `rules: - domain/domain_suffix/...` |
| `AND/OR/NOT` 条件规则 | `rules: - and/or/not: match: [...]` |
| `[Rewrite]` `reject()` | `url_rewrites: location: http://reject/` |
| `reject_dict/reject_array/reject_img` | `http://reject-dict/` / `-array/` / `-img/` |
| `redirect(302, url)` | `url_rewrites: location + status_code: 302` |
| `response.json.delete/replace` | `body_rewrites: response_jq: filter` |
| `[URL Rewrite]` | `url_rewrites` |
| `[Map Local]` | `map_locals` |
| `[Script]`（Loon 与 Surge 两种写法） | `scriptings: http_request/http_response` |
| `[MitM] hostname` | `mitm.hostnames` |
| `[Argument]` | `compat_arguments` + `compat_arguments_desc` |
| `#!name/#!desc/#!icon` | `name/description/icon` |

正则做了统一处理：Loon 的 `/.../i` 去掉斜杠与 `i`，转为 `(?i)` 前缀；`${urlMatch.1}` 转为 `$1`。

## 关于“能否生效”，需要分两层看

**第一层：模块结构（确定生效）**
规则、URL 重写、Body 重写、Map Local、MITM 主机、脚本绑定关系都是 Egern 文档定义的字段，产物全部通过 `yaml.safe_load` 校验，没有残留非法字段。这一层不依赖任何运行时兼容性。

**第二层：脚本执行（依赖 Egern 的 Loon 兼容层）**
1,018 条脚本全部沿用原始 JS，没有重写。抽查与全量特征扫描结果：

- 196 个脚本中，**187 个使用 `$httpClient` / `$persistentStore` / `$notification` / `$done`**（Loon/Surge 全局对象）
- 少数脚本是纯 JSON 处理，不依赖网络 API

Egern 官方文档只承诺 `ctx` 体系（`export default async function(ctx)`），并未把上述全局对象写进 JS API 参考。它们能跑，依据是：

1. Sub-Store 官方仓库的 `config/Egern.yaml` 直接引用其通用构建，而 Sub-Store 的 Egern 分支就是按 `$httpClient` 实现的；
2. `@nsnanocat/util` 的平台对照表把 Egern 的 HTTP / 通知 / 持久化 / 结束脚本全部标为 `$httpClient` / `$notification.post` / `$persistentStore` / `$done`。

两个独立项目的适配都指向"Egern 内置了 Loon 脚本兼容层"。但**我没有在真机上验证过**，所以不能承诺 100% 执行成功。建议首次导入后按下面的自查表过一遍。

## 脚本镜像

原始 1,018 条脚本引用指向 214 个唯一 URL，其中 **760 条指向 `raw.githubusercontent.com`**——国内直连基本拉不到，这是"模块看着启用但脚本一直下载中"的主因。

处理方式：全部下载后按内容哈希存为 `scripts/<sha1>.js`，模块里的 `script_url` 改写为自建 jsDelivr 地址。

- 成功镜像 **196 / 214**（3.16 MB，去重后 168 个文件）
- 失败 18 个，保留原始 URL，清单见 `reports/scripts.md`

失败的 18 个集中在：`github.com` releases 资产（Biliverse ADBlock/Global 的 4 个 bundle）、`loon.103516.xyz`（4 个）、`rucu6.pages.dev`（5 个）、以及零散的 `workers.dev` / `vercel.app` / raw 文件。这几个源在当前网络返回 502/504/SSL EOF，备用 CDN（gitmirror、statically、gcore）也全部不通。

## 已知差异（需要你注意）

1. **`$argument` 无法传递**：Loon 的脚本参数（`argument="[...]"`）在 Egern 的 `scriptings` 里没有对应字段，已从产物中剥离。依赖参数切换功能的脚本（如 B 站 Sparkle 的净化开关）会走脚本内置默认值。
2. **`pre-matching` 已丢弃**：Egern 没有 DNS 前匹配概念，但 domain 类规则本身就在 DNS 后按域名匹配，行为等价。
3. **`body.mock` 返回固定二进制体**（5 处，B 站 protobuf 响应）无法用 `body_rewrites` 表达，已列入 `unsupported.md`，需要 `map_locals` 承载二进制体。
4. **`jq_file()` 远程加载 jq 规则**（4 处）未内联，已列入 `unsupported.md`。

## 导入后自查

| # | 位置 | 期望 |
|---|---|---|
| 1 | 工具 → 模块 | 83 个，名称可读，无"下载失败" |
| 2 | 工具 → 脚本 | 全部"已下载"，无长期失败 |
| 3 | 工具 → MITM | 主机数数百条，银行/政务不在列表 |
| 4 | 知乎 / 微博 / 小红书 | 信息流无广告，刷新正常 |
| 5 | B 站 | 无开屏、无信息流广告 |
| 6 | 某个脚本 | 在 `工具 → 脚本` 里点开日志，确认有执行记录（不是仅下载成功） |

第 6 项是判断兼容层是否生效的关键：脚本"已下载"只说明能拉到文件，只有日志里出现执行记录才说明 `$httpClient` 那套 API 在 Egern 里真的可用。

## 回退

模块全部在 `native/modules/`，主配置改回 v11.2 的 `modules:` 段即可回到原状态，两者互不覆盖。
