# 合约仓位模拟器

U 本位与币本位（SOL）永续合约的**强平价格 / 盈亏 / 收益率**估算工具，纯静态页面，无需构建、无需后端。

## 功能

- U 本位 / 币本位切换（切换时自动换算保证金单位）
- 做多 / 做空、全仓 / 逐仓
- 实时计算强平价、距开仓价幅度、风险提示条
- 目标价情景下的持仓数量、名义价值、毛盈亏、手续费、资金费用、净盈亏、ROI
- 价格变动情景表（-10% ~ +10%），自动标记已强平仓位
- 可配置开仓/平仓费率、资金费率与结算次数、其他仓位盈亏与维持保证金
- 移动端（iPhone / Android）自适应，支持添加到主屏幕离线使用
- 参数自动保存在本机浏览器（localStorage）

> 结果为估算，实际强平价以交易所显示为准。

## 使用

### 本地预览

```bash
python3 -m http.server 8899
# 打开 http://localhost:8899/index.html
```

直接双击 `index.html` 也能用，但 Service Worker（离线缓存）需要 http(s) 环境才生效。

### 部署到 GitHub Pages

仓库已包含 `.github/workflows/pages.yml`，推送到 `main` 后：

1. 仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**
2. 访问 `https://<用户名>.github.io/<仓库名>/`

若用 `gh` CLI：

```bash
gh api --method POST repos/<用户名>/<仓库名>/pages \
  -f source[branch]=main -f source[path]=/
```

## 文件结构

```
index.html              # 主页面（全部 HTML/CSS/JS 内联）
manifest.webmanifest    # PWA 清单
sw.js                   # Service Worker，离线缓存
icons/                  # 应用图标
```

## 浏览器支持

iOS Safari 15+、Android Chrome、桌面 Chrome / Edge / Firefox / Safari。
