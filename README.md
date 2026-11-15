# Knight

This is My First GameDev Program. Come 2 Watch How My Game Dev Improve. :)

一个跟着 Brackeys 新手教程从零搭起来的 Godot 4 **2D 平台跳跃**练习项目。

---

## 当前进度

目前是一个能跑能跳的雏形，已经实现的：

- **角色控制**（`Scences/player.gd`）：左右移动、跳跃、重力，全部在 `_physics_process` 中处理，用 `move_and_slide()` 驱动
- **瓦片关卡**（`Scences/Game.tscn`）：用 `world_tileset.png` 建成的 TileSet，地形瓦片带碰撞多边形，玩家可以站在上面
- **相机跟随**：`Camera2D` 挂在 Player 节点下，4 倍缩放，开启了位置平滑

还没做的：金币、敌人、计分、动画状态切换、关卡切换、UI。

## 运行方式

1. 安装 **Godot 4.7** 或更高版本（标准版，不是 .NET / C# 版）
2. 打开 Godot，导入本目录下的 `project.godot`
3. 按 `F5` 运行，或者直接双击 `Scences/Game.tscn` 后按 `F6` 运行当前场景

渲染器用的是 **Forward Plus**。第一次用编辑器打开时，Godot 会花几秒导入素材并生成 `.godot/` 缓存目录 —— 那是本地缓存，已经写进 `.gitignore`，不需要也不应该提交。

## 操作

| 动作 | 按键 |
|---|---|
| 左右移动 | `←` `→` |
| 跳跃 | `空格` / `回车` |

目前用的是 Godot 内置的 `ui_left` / `ui_right` / `ui_accept` 动作，所以是**方向键而不是 WASD**。改成自定义 Input Map 是下一步的计划之一。

## 项目结构

```
knight/
├── project.godot                        # 项目配置（Godot 4.7，Forward Plus）
├── icon.svg                             # 项目图标
├── Asets/                               # 素材目录
│   └── brackeys_platformer_assets/      # Brackeys 平台跳跃素材包
│       ├── fonts/                       # PixelOperator 字体
│       ├── music/                       # 背景音乐
│       ├── sounds/                      # 金币、受伤、跳跃、爆炸等音效
│       ├── sprites/                     # 角色、史莱姆、金币、瓦片图集
│       └── LICENSE & CREDITS.txt        # 素材授权与作者信息
└── Scences/                             # 场景与脚本
    ├── Game.tscn                        # 主场景：玩家 + 相机 + 瓦片地图
    ├── player.tscn                      # 玩家场景（可复用的实例）
    └── player.gd                        # 玩家移动逻辑
```

> 注：`Asets` 与 `Scences` 是建项目时的拼写笔误，本意是 `Assets` 和 `Scenes`。重命名会牵涉 `.tscn` 里的 `res://` 路径引用和 `.uid` 文件，需要单独做一次，暂不动。

## 素材授权

本项目使用的美术、音效、音乐和字体来自 **Brackeys Platformer Bundle**，全部为 **CC0（Creative Commons Zero）** 授权，可自由使用与分发。

- **SPRITES**：analogStudios_ —— [Camelot](https://analogstudios.itch.io/camelot)、[Dungeon Sprites](https://analogstudios.itch.io/dungeonsprites)、[Four Seasons Platformer Sprites](https://analogstudios.itch.io/four-seasons-platformer-sprites)
- **SPRITES**：RottingPixels —— [Four Seasons Platformer Tileset](https://rottingpixels.itch.io/four-seasons-platformer-tileset-16x16free)
- **SOUNDS**：Brackeys, Asbjørn Thirslund
- **MUSIC**：Brackeys, Sofia Thirslund
- **FONTS**：Jayvee Enaguas (HarvettFox96) —— [Pixel Operator](https://www.dafont.com/pixel-operator.font)

完整说明见 `Asets/brackeys_platformer_assets/LICENSE & CREDITS.txt`。

## 待办

- [ ] 把玩家输入从内置 `ui_*` 动作改成自定义 Input Map（`move_left` / `move_right` / `jump`），支持 WASD
- [ ] 补上动画状态切换：目前只有 `idle` 一组帧，走跑和滞空还没有对应动画
- [ ] 修正目录名拼写：`Asets` → `Assets`、`Scences` → `Scenes`
- [ ] 加金币：`Area2D` + `body_entered` 信号，捡到就加分
- [ ] 加敌人与伤害、生命值、死亡重生
- [ ] 加一个 Game Over / 重开流程

## 环境

| 项 | 版本 |
|---|---|
| 引擎 | Godot 4.7（Forward Plus） |
| 语言 | GDScript |
| 项目类型 | 2D |
