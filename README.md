# 雷霆战机 · Thunder Fighter

一个纯前端、单文件的 2D 竖版飞行射击（STG）小游戏，用原生 Canvas 2D 绘制，零依赖、零构建，双击 `index.html` 就能玩。

![玩法](https://img.shields.io/badge/genre-vertical%20shmup-4de6ff) ![license](https://img.shields.io/badge/license-MIT-7cffb2)

## 玩法

| 操作 | 说明 |
| --- | --- |
| `W A S D` / `方向键` | 移动战机 |
| 鼠标（或手指）拖拽 | 拖动战机，手机端直接按在屏幕上滑 |
| 自动开火 | 不需要按键，火力持续输出 |
| `J` / `X` | 释放炸弹：清空全屏敌弹并造成大范围伤害 |
| `P` / `Esc` | 暂停 / 继续 |
| `M` | 静音开关 |
| `Enter` / `空格` | 开始游戏、重新开始 |

## 道具

- **P** — 火力升级，1 → 4 级（单发 → 双发 → 三发 → 主炮 + 侧翼斜射）
- **B** — 补充一枚炸弹
- **S** — 获得 8 秒护盾，可抵挡一次伤害

## 内容

- 4 种敌机：`scout` 蛇形侦察机、`dart` 俯冲机、`gunner` 悬停炮台、`tank` 重甲坦克
- 每关固定时长后进入 **BOSS 战**，BOSS 有三段血量阶段：扇形弹幕 → 瞄准连射 → 环形弹 + 螺旋弹，并会召唤小兵
- 击破 BOSS 后进入下一关，敌人血量、弹速、刷新频率随关卡提升
- 最高分保存在 `localStorage`

## 技术实现

- 单文件 HTML，CSS / JS 全部内联，无任何外部依赖与网络请求
- 480 × 800 逻辑分辨率 + `devicePixelRatio` 适配，任意窗口尺寸自动缩放
- 全部视觉元素（战机、敌机、BOSS、子弹、爆炸、星空）均由 Canvas 路径与渐变实时绘制，无贴图资源
- 音效由 WebAudio 实时合成（振荡器 + 噪声缓冲），无音频文件
- `requestAnimationFrame` 主循环，`dt` 上限裁剪，避免切后台后跳帧
- 对象用数组 + 倒序遍历原地增删，碰撞为圆-圆检测，单帧计算量很小，手机也能跑满帧

## 运行

```bash
# 方式一：直接双击
index.html

# 方式二：起个本地服务（可选）
python -m http.server 8000
# 浏览器打开 http://localhost:8000
```

## 目录结构

```
雷霆战机/
├── index.html   # 游戏本体（全部代码都在这里）
└── README.md
```

## License

MIT
