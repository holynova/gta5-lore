# GTA5 · 洛圣都三叉戟

围绕麦克、富兰克林和崔佛，用六幕视频串起背叛、重逢与联合储蓄劫案。

A six-chapter Chinese recap of Michael, Franklin and Trevor’s intertwined story.

[在线体验](https://gta5-lore.xiaosang.cc/) · [源码](https://github.com/holynova/gta5-lore)

![GTA5 · 洛圣都三叉戟：真实页面截图](./assets/readme/screenshot.png)

## 可以做什么

- 沿人物关系与事件因果回顾主线。
- 提供在线成片和分幕工程文件。

## 观看与工程

打开在线页面播放，或选择章节定位观看。包含主线与结局剧透。

[打开成片](https://gta5-lore.xiaosang.cc/gta5_lore.mp4) · [仓库中的视频](./gta5_lore.mp4)

实测成片：1920 × 1080，30 fps，H.264 + AAC；时长 3:51，文件约 12.4 MiB。

`index.html` 是公开播放器；`composition.html` 与 `compositions/` 保留视频合成源码。旁白和配乐在 `assets/`。

## 本地预览

```bash
python3 -m http.server 8080
```

打开 http://localhost:8080/。播放器直接使用仓库成片，无需先渲染。

重新渲染需安装工程依赖和可用的 Chrome；在 HyperFrames 中使用 `composition.html` 合成入口，避免把播放器页面当作视频时间线。

影视化剧情是作者的剪辑与解释，游戏角色、官方素材及相关商标归各自权利人；这是非官方项目。

<img src="./assets/readme/qr.png" width="144" alt="扫码打开https://gta5-lore.xiaosang.cc/">

## 发布

```bash
npx --yes wrangler@4.128.0 deploy --dry-run --config wrangler.jsonc
npx --yes wrangler@4.128.0 deploy --config wrangler.jsonc
```

从 `main` 同一提交在本地手动发布到Cloudflare Workers。正式地址：[https://gta5-lore.xiaosang.cc/](https://gta5-lore.xiaosang.cc/)。 `.assetsignore` 限定公开播放器/站点资源，排除合成工程、开发文件与未供页面使用的大体积音频/字体。

视频通过 `worker/media.mjs` 提供HTTP字节范围读取，支持章节跳转；运行 `npm run test:media` 检查范围与校验器处理。
