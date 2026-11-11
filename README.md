# 英语学习卡 · GitHub Pages 部署

纯静态站点，无需构建。包含两个板块：

- `phonetics/` — 44 张国际音标学习卡（浏览 / 筛选 / A4 打印）
- `lesson-01/` — Lesson 01《The Perfect Hamburger》图文精读课 + 26 张配套卡片

## 目录结构

```
site/
├── index.html          首页（板块导航）
├── .nojekyll           跳过 GitHub Pages 的 Jekyll 处理
├── phonetics/          音标卡片板块
│   ├── index.html
│   └── cards/          01.png – 44.png
└── lesson-01/          精读课板块
    ├── index.html      课文页
    ├── cards.html      配套卡片页
    ├── cards/          26 张卡片
    └── images/web/     配图
```

## 部署步骤（GitHub Pages）

1. 在 GitHub 上新建一个仓库（如 `english-cards`，Public）。

2. 在 `site/` 目录下执行：

```bash
git init
git add .
git commit -m "init: english learning cards site"
git branch -M main
git remote add origin https://github.com/<你的用户名>/english-cards.git
git push -u origin main
```

3. 开启 Pages：仓库 **Settings → Pages → Build and deployment**
   - Source 选 `Deploy from a branch`
   - Branch 选 `main`，目录选 `/ (root)`，保存

4. 一两分钟后访问：
   `https://<你的用户名>.github.io/english-cards/`

> 若稍后更新内容：把新文件放进 `site/` 对应目录，`git add . && git commit -m "update" && git push` 即可自动重新发布。

## 本地预览

```bash
cd site
python -m http.server 8080
# 打开 http://127.0.0.1:8080
```

## 重新生成卡片（可选）

- 音标卡：`python scripts/make_cards.py` → 输出到 `音标卡片/cards/`，复制到 `site/phonetics/cards/`
- 课文/词汇/句型卡：`python scripts/make_lesson_cards.py`、`python scripts/make_text_cards.py` → 输出到 `英语短文_汉堡/cards/`，复制到 `site/lesson-01/cards/`
