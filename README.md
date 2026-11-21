# moodmapcold

> 有些地方，白天是交通节点，凌晨是无出口的圈。

一个极简的冷酷值计算器。输入地点或经纬度，结合时间光照、地理人口、天气体感、文化心理四个维度，输出 0–100 的「冷酷值」。支持 Open-Meteo 实时天气、Nominatim 地名解析、Unsplash 地点配图。

> 本地使用：克隆仓库后，在目录执行 `python3 -m http.server 8000`，访问 `http://localhost:8000`。

## 算法

| 维度 | 权重 | 说明 |
|------|------|------|
| 时间光照 | 30% | 太阳高度角公式，凌晨封顶 80 分 |
| 地理人口 | 25% | 偏远度 ×0.6 + 荒废度 ×0.4 |
| 天气体感 | 25% | 气温越低、风越大、雨雾越重分越高 |
| 文化心理 | 20% | 地名氛围、都市传说、工业孤寂感 |

各维度独立封顶 80 分，加权求和得总分（0–100）。

## 示例

| 地点 | 时间 | 天气 | 冷酷值 | 档位 |
|------|------|------|--------|------|
| 担杆山交汇处 | 凌晨 2:00 | 22℃ 微风 | ~72 | 压抑空旷 |
| Bergen Nordnes | 21:00 | 12℃ 小雨 | ~42 | 冷感显著 |
| 旺角 | 凌晨 2:00 | 25℃ 闷热 | ~38 | 普通偏冷 |

## 内置预设

担杆山交汇处、大屿山、索罟湾、魔鬼山、旺角、维多利亚港、Bergen Nordnes 等。输入别名（如 `Tam Kon Shan Interchange`）也能命中。

## 数据源

- **天气**：[Open-Meteo](https://open-meteo.com/)（免费，无需 API Key）
- **地名**：[Nominatim](https://nominatim.openstreetmap.org/)（OpenStreetMap）
- **图片**：[Unsplash Source](https://source.unsplash.com/)（按关键词搜索）

## 部署到 GitHub Pages

1. 进入仓库 Settings → Pages
2. Source 选择 `main` 分支，文件夹选 `/ (root)`
3. 保存后访问 `https://fhadufhlsadfhlsuajf.github.io/moodmapcold/`

## 许可证

[MIT](LICENSE)

---

*有些地方，绕一圈没有一辆车。*