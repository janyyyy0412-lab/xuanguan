# 和式伝統建築 玄関土間 交互式3D図解

## 项目概览
纯前端3D交互式建筑教学图解网页，展示日式传统建筑玄关土间的45°斜等轴测模型。用户可点击各构件查看日文文化释义，支持拖拽旋转和滚轮缩放。

## 技术栈
- 原生 HTML/CSS/JavaScript（单文件应用）
- Three.js r160（ES Module，CDN引入）
- OrbitControls（正交相机等轴测视图）
- Google Fonts: Noto Serif JP, Noto Sans JP

## 构建与运行
```bash
# 开发环境（已由 .coze 配置自动启动）
python -m http.server 5000 --bind 0.0.0.0
```
无构建步骤，直接通过静态服务器提供 index.html。

## 文件结构
```
index.html          # 完整应用（HTML + CSS + JS 内联）
.coze               # 项目配置（native-static 模板）
AGENTS.md           # 本文件
```

## 8个建筑构件
| Key | 日文名 | 假名 | 颜色 |
|-----|--------|------|------|
| kurumayose | 車寄せ | くるまよせ | #C4B8A4 |
| shikigawara | 式瓦 | しきがわら | #7A7062 |
| doma | 土間 | どま | #A69880 |
| kutsunugiishi | 沓脱石 | くつぬぎいし | #B5A99A |
| kekomiita | 蹴込み板 | けこみいた | #C4A882 |
| shikidai | 式台 | しきだい | #D4C4A8 |
| agarikamachi | 上がり框 | あがりかまち | #B89B72 |
| yukaita | 床板 | ゆかいた | #C9B896 |

## 坐标系
- X轴：宽度方向（3.64m总宽，居中于X=0）
- Y轴：高度方向（地面Y=0）
- Z轴：进深方向（前方为负Z，内部为正Z）

## 高度层级
- Y=0.00: 土間/車寄せ/式瓦（地面基准）
- Y=0.07: 沓脱石顶面
- Y=0.21: 蹴込み板顶部 / 式台顶面
- Y=0.30: 上がり框/床板顶面

## 交互逻辑
- 点击构件 → 高亮描边（蓝色边缘+emissive发光）→ 弹出日文释义弹窗
- 再次点击同一构件 → 取消高亮并关闭弹窗
- 点击空白处 → 关闭弹窗并取消高亮
- 拖拽旋转 / 滚轮缩放（OrbitControls）
- 左侧图例可点击触发高亮
- 左上标高栏显示高度层级
