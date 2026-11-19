# LinkClean - 链接净化

[English](../README.md) | 中文 | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

分享链接之前，先把上面的追踪尾巴摘干净。粘贴一个网址，LinkClean 会列出删掉的每一个参数，拆开跳转链接与 AMP 页，再给你一条干净链接。全部在本机完成，链接不会离开浏览器。

## 亮点

- **一次粘贴，一条干净链接** —— 粘网址，或直接取当前标签页。
- **删了什么一目了然** —— 每个被移除的参数按名字列出，附带站点原本会拿到的值，不做静默改动。
- **复制为纯网址或 Markdown** —— Markdown 用真实页面标题生成 `[标题](网址)`。
- **批量模式** —— 既吃「一行一个网址」，也吃整段文字、邮件、聊天记录；只改写里面的链接，前后文字原样保留。
- **保留功能参数** —— 只删 58 个已知追踪参数名与 11 个前缀系列（`utm_`、`ga_`、`mtm_`、`piwik_`、`_hs` 等），其余一律不动。
- **Pro：跳转壳拆解** —— Google、YouTube、Facebook、Reddit、DuckDuckGo、LinkedIn、知乎、豆瓣、简书、少数派、VK、Slack、Outlook Safe Links、Skimlinks、Tumblr、Medium、Pocket，加上 Bing、微博、Proofpoint 与通用 `/redirect?url=`，最多递归三层，全程本机。
- **Pro：AMP 还原** —— `cdn.ampproject.org/c/s/`、`google.com/amp/s/`、结尾 `/amp` 都回到正式页面。
- **Pro：站点规则** —— 让 `amazon.com` 保留 `th`、`psc`，其它照删；越具体的域名优先级越高，子域自动继承。在结果里点一下某个被删参数，它就永久加入本站保留名单。
- **Pro：历史与统计** —— 按链接/标题/域名搜索历史，一键复制回原始链接，导出 JSON；另有累计清理链接数与删除参数数。

## 免费 vs Pro

| | 免费 | Pro |
|---|---|---|
| 单条净化（完整内置参数库） | ✅ | ✅ |
| 复制 Markdown / 读剪贴板 / 锚点开关 | ✅ | ✅ |
| 清理后自动复制 | ✅ | ✅ |
| 批量条数 | 10 条 | 不限 |
| 导出 TXT | ✅ | ✅ |
| 导出 CSV / JSON | — | ✅ |
| 段落里夹着多个链接 | 10 条以内 | ✅ |
| 跳转壳与 AMP 还原 | 仅提示 | ✅ |
| 站点级规则 + 一键保留 | — | ✅ |
| 历史 | 10 条 | 100 条，可搜索、可还原原始链接 |
| 规则包导入导出 | — | ✅ |
| 最常处理站点榜 | — | ✅ |

一个授权码可在两个浏览器激活；移除授权即释放名额。约每 2 小时校验一次，离线凭缓存授权可用；校验失败不会锁功能。

## 使用流程

1. 点 LinkClean 图标。当前页面如果带追踪参数，输入框已经替你填好。
2. 点「清理链接」。结果会显示干净网址、每个被删参数的标签；有授权且命中跳转壳时，还会显示拆开的跳转链。
3. 复制链接、复制 Markdown、直接打开，或者把这条链接丢进批量继续处理。
4. 发现某个参数不该删？在结果里点它一下，就加入本站保留名单。

## 隐私

- 链接不离开浏览器。所有规则都是本机字符串运算，**不会为了知道跳转去哪而真的去请求那个地址**。
- 无统计、无遥测、无广告标识、无追踪像素。
- 历史、设置、计数存于 `chrome.storage.local`，随时可以清空。
- 唯一的网络请求是 Pro 授权激活/校验：授权码、随机安装标识、插件 id 与基础浏览器信息。
- 只有你点「粘贴」时才读剪贴板；只有点复制或开启自动复制时才写剪贴板。

## 权限说明

| 权限 | 用途 |
|---|---|
| `storage` | 本地保存设置、自定义规则、历史与授权状态 |
| `activeTab` | 只在你点击图标后读取当前页面地址 |
| `clipboardWrite` | 点复制或开启自动复制时写入干净链接 |
| `clipboardRead` | 只在你点「粘贴」时读剪贴板，绝不在后台读取 |
| `https://api.annmax1983.com/*` | 仅用于授权激活与校验，从不传输链接 |

没有内容脚本，没有 `<all_urls>` 站点权限，没有 `tabs` 权限，也没有 `downloads` 权限——LinkClean 看不到任何页面的文字。

## 支持浏览器

Chrome 与 Edge（Manifest V3，Chrome 116+）。Firefox 版在计划中。

## 开发

```bash
npm install        # 仅开发依赖：terser
npm run locales    # 由 tools/make-locales.js 生成六语 _locales
npm run icons      # 生成图标
npm test           # node --test：净化、跳转壳、站点规则、i18n、弹窗接线
npm run build      # 压缩 + 打包 → publish/linkclean-v{version}.zip
node tools/shoot.js  # 用真 Chrome 渲染 1280×800 商店截图与 promo 图
```

在 `chrome://extensions` 开启开发者模式，加载仓库根目录即可试用。

## 链接

- 官网：https://annmax1983.com
- 扩展页面：https://annmax1983.com/extensions/linkclean
- 授权与定价：https://annmax1983.com/checkout?plugin=linkclean
