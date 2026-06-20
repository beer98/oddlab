# 怪研所 · ODD LAB

> 生活冷研究 · 把生活里的怪问题，查到出结论。

稀奇古怪的问题 → 翻数据、扒研究 → 只留一个站得住的结论。一篇一页，能用图就不写废话。
跟投研站（[ALPHA VAULT](https://github.com/beer98/alpha-vault)）完全分开的另一座库。

**线上**：https://oddlab-wen98.pages.dev

## 架构

纯静态、零构建、零锁定。**GitHub = 唯一底本**，部署平台可换可并存。

```
oddlab/
├── index.html                       # 总页面（档案目录，会长大）
├── r/<slug>/index.html              # 每份研究一页
│   └── china-diet-health-map/       # №01 中国饮食健康地形图
├── .github/workflows/deploy.yml     # push 到 main → 自动部署 Cloudflare Pages
└── README.md
```

## 自动部署

push 到 `main` → GitHub Actions 跑 `wrangler pages deploy .` → 约 35s 上线。

仓库 Secrets（Settings → Secrets and variables → Actions）：

| 名称 | 值 |
| --- | --- |
| `CLOUDFLARE_API_TOKEN` | Cloudflare 的 Pages 编辑 token（写权限） |
| `CLOUDFLARE_ACCOUNT_ID` | 账号 ID（**必须小写**） |

没配 token 时 workflow 会优雅跳过部署，配好后下次 push 自动生效。

## 加一份研究

1. 新建 `r/<英文短slug>/index.html`（内页加 `← 怪研所` 返回导航）。
2. 在 `index.html` 复制一条 `<a class="entry">` 块：换编号 `№NN`、学科色（`--c-food/-body/-mind/-city/-nat`）、结论标题、take、来源、链接。
3. 更新顶部计数（`／ NN`、月份 `N 份`）与「更新」日期。
4. push → 自动上线。

公开署名 **wen98**。
