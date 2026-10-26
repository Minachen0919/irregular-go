# 异形棋盘

四周随机侵蚀的围棋盘。可以本机对弈，也可以把邀请链接发给朋友联机下。

- 9 / 13 / 19 路，边缘侵蚀程度可调，可在中间挖洞
- 立方体棋盘：棋子下在立方体六个面上，棱把相邻的面连起来，没有边，8 个角只有 3 口气；拖动旋转、点击落子
- 双色、三色、四色：黑 → 白 → 红 → 蓝 轮流落子，多色模式按数子排名、不贴目，认输的人退出轮转
- 14 种棋子样式：Ink、Shell、Cinnabar、Ultramarine、Jade、Celadon、Lavender、Rouge、Forest、Amber、Gold、Frost、Tortoise、Galaxy。每位玩家点「换棋子」自己挑，别人在用的会标出是谁、不能重复选
- 提子、禁着点，劫按全局同形（不能还原出现过的局面）判定
- 双方停一手后进入数子：点选死子，中国规则数子 + 贴目
- 联机：创建房间得到 4 位房间号，邀请链接形如 `https://<用户名>.github.io/irregular-go/#K7QX`，点开自动加入
- 联机悔棋需要对方同意；刷新页面会自动回到原来的房间

## 联机配置（Firebase Realtime Database）

1. 在 [Firebase 控制台](https://console.firebase.google.com) 新建项目。
2. Build → Realtime Database → 创建数据库，位置选 Singapore (asia-southeast1)。
3. 在数据库的 Rules 标签里粘贴 `database.rules.json` 的内容并发布。
4. 项目设置里添加一个 Web 应用，把 `firebaseConfig` 填进 `config.js`。

`config.js` 没填时，网站照常能用，只是只有本机对弈。

规则允许任何知道房间号的人读写这个房间，适合朋友之间玩，不适合存重要数据。

## 本地预览

```
python3 -m http.server 8000
```

然后打开 http://localhost:8000 。
