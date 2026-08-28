# 素材加载清单

框架已就绪，下列素材位均已用**彩色占位图**自动填充，游戏现在就能跑。
你把真实素材放到对应路径即可无缝替换，**无需改代码**。

> 规则：文件名必须与下表一致；图片用 PNG（带透明）或 JPG；动画用序列帧编号。

## 一、角色（已就位 9 张）
路径：`assets/characters/<职业>/`
| 职业 | 立绘(选角UI) | 三视图(参考) | 像素立绘(地图战斗) |
|------|-------------|-------------|-------------------|
| 战士 | warrior_portrait.jpg | warrior_turnaround.jpg | warrior_pixel.jpg |
| 法师 | mage_portrait.jpg | mage_turnaround.jpg | mage_pixel.jpg |
| 召唤师 | summoner_portrait.jpg | summoner_turnaround.jpg | summoner_pixel.jpg |

像素立绘建议尺寸 96×96，立绘建议 240×320。

## 二、敌人（待提供）
路径：`assets/enemies/`，命名 `<key>.png`，建议 110×110
| key | 名称 | 来源 |
|-----|------|------|
| slime.png | 史莱姆 | 普通战斗 |
| goblin.png | 哥布林 | 普通战斗 |
| skeleton.png | 骷髅兵 | 普通战斗 |
| bat.png | 巨型蝙蝠 | 普通战斗 |
| elite_knight.png | 堕落骑士 | 精英战 |
| boss_dragon.png | 腐化巨龙 | BOSS |

## 三、场景背景（待提供）
路径：`assets/scenes/`，命名 `<name>.jpg`，建议 1280×720
| 文件名 | 用途 |
|--------|------|
| battle_battle.jpg | 普通战斗背景 |
| battle_elite.jpg | 精英战背景 |
| battle_boss.jpg | BOSS战背景 |

（场景名规则：`battle_<节点类型>.jpg`）

## 四、UI（待提供，可选）
路径：`assets/ui/`，目前用代码绘制，提供后会替换。
如需自定义按钮/血条框等，命名后告知，我接进 `asset_loader.load_ui_image()`。

## 五、动画/特效（待提供，可选）
路径：`assets/animations/`，序列帧编号如 `attack_001.png ~ attack_008.png`。
框架已预留 `Animation` 类用法（见下），素材到位后我接入战斗特效层。

## 六、过场视频（待提供，可选）
路径：`assets/cutscenes/`。视频在 pygame 中需用 `pygame._movie` 或外部解码，
建议提供 MP4，届时我负责接入播放层与跳过逻辑。

---

## 代码里素材怎么被调用（参考）
```python
from asset_loader import load_character_pixel, load_enemy_image, load_scene
img = load_character_pixel("warrior", (96, 96))   # 找不到自动占位
```
所有加载走 `asset_loader.load_image(相对路径, 尺寸, 占位色, 占位文字)`，
**缺素材不报错**，直接生成带文件名的彩色方块。
