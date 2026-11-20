# 立体波场与质点振动 · 3D 交互课件

用于大学物理「第十章 机械波」的课堂演示：把一列波想象成一排学生，每个质点只在平衡位置附近上下振动，而“谁高谁低”的相位状态沿队列传播。

页面使用原生 Canvas 2D 做透视投影，不依赖 Three.js、CDN 或任何网络资源，单个 `index.html` 即可离线运行。

![桌面端预览](assets/preview-desktop.png)

## 功能

- 3D 透视波场：41 个质点排成一列，各自在平衡位置附近上下振动
- 每个质点带有竖直参考线，地面有透视网格与坐标方向
- 鼠标拖动旋转视角，滚轮缩放；手机端单指拖动旋转
- 点击任意质点，或拖动 `x₀` 滑块，把该质点“请出队列”
- 选中质点移动到队列前方，带高亮圆环、位移竖线和连接线
- 下方实时绘制选中质点的 `y-t` 振动曲线
- 参数调节：振幅 `A`、频率 `f`、波长 `λ`、初相位 `φ`、动画速度
- 实时读数：`t / T / λ / v / f`，波速自动由 `v = λf` 计算
- 播放 / 暂停、重置、重置视角
- 桌面端与 390px 手机端响应式布局

![手机端预览](assets/preview-mobile.png)

## 操作

| 操作 | 效果 |
| --- | --- |
| 拖动舞台 | 旋转 3D 视角 |
| 滚轮 | 缩放舞台 |
| 点击质点 | 选中并把它请到前排 |
| 拖动 `观察质点 x₀` | 精确选择观察位置 |
| `Space` | 暂停 / 播放 |
| `R` | 重置参数、时间和观察点 |
| `←` / `→` | 移动观察点到相邻质点 |

## 物理模型

波函数取右行波形式：

```text
y(x, t) = A sin(ωt − kx + φ)
```

固定观察位置 `x₀` 后：

```text
y₀(t) = A sin(ωt + φ − kx₀)
```

因此该质点做简谐振动；不同 `x₀` 的振动曲线形状相同，相位依次相差：

```text
Δφ = 2π Δx / λ
```

波速：

```text
v = λf = ω/k
```

## 文件结构

```text
.
├── index.html
├── README.md
├── .nojekyll
└── assets
    ├── preview-desktop.png
    └── preview-mobile.png
```

## 本地预览

直接双击 `index.html` 即可。也可以在当前目录启动静态服务器：

```bash
python -m http.server 8000
```

然后访问 `http://localhost:8000/`。

## 部署到 GitHub Pages

1. 新建公开仓库，例如 `wave-field-3d`。
2. 将本目录中的 `index.html`、`README.md`、`.nojekyll` 和 `assets/` 上传到仓库根目录。
3. 打开仓库 **Settings → Pages**。
4. **Build and deployment** 选择：
   - Source：**Deploy from a branch**
   - Branch：**main**，目录 **/(root)**
5. 点击 **Save**，等待约 1 分钟。
6. 访问：

```text
https://<你的用户名>.github.io/wave-field-3d/
```

## 浏览器建议

建议使用较新的 Chrome、Edge、Firefox 或 Safari。页面使用 Canvas 2D、CSS Grid/Flex、`ResizeObserver` 和 Pointer Events，不支持 Internet Explorer。

## 说明

- 上一版二维课件《波函数与质点振动-交互课件.html》保持独立，未被本页面覆盖。
- 本页面是课堂示意模型，质点数量、坐标和振幅比例为教学展示服务，不表示真实空间尺度。
