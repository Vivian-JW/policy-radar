# 中国城市人社惠企政策雷达系统 · 交付包说明

## 包内容

| 文件 | 说明 |
|---|---|
| `index.html` | 前端页面（已确认版式，纯静态单文件，无外部依赖，可直接部署） |
| `PRD.md` | 产品需求文档 v1.0（正式开发规格依据） |
| `README.md` | 本说明 |

## 当前版本状态（重要）

`index.html` 为**交互定稿版**：页面结构、表单、三级区域联动（全国 31 省级区划）、雷达图、政策库排序等均为正式交互；但页面内的政策、金额、日期、链接仍为**示例数据**（页面顶部有橙色标识横幅）。

真实政策数据、匹配引擎、后端 API 按 PRD 里程碑 M3–M5 接入。

## 立即部署（静态托管）

单文件、零依赖，任何静态托管环境均可：

**Nginx**
```nginx
server {
    listen 80;
    server_name your-domain.com;
    root /var/www/policy-radar;
    index index.html;
}
```

**或直接使用各类平台**：腾讯云 COS 静态网站 / CloudBase 静态托管 / Vercel / Netlify / GitHub Pages —— 上传 `index.html` 即可。

## 本地预览

```bash
cd policy-radar-release
python3 -m http.server 8080
# 浏览器打开 http://localhost:8080
```

## 后续开发路线（详见 PRD.md 第 7、8 节）

- M2：接入全量行政区划数据（民政部区划代码表）
- M3：政策库后端 + 首批城市真实政策核验入库（S1/S2 双来源）
- M4：十关卡匹配引擎 + 多主体企业画像
- M5：截止提醒与政策变更监测
- 技术栈建议：Vue3/React + FastAPI/NestJS + PostgreSQL + 定时采集管道

## 合规声明

本系统不构成政府审批承诺；匹配结论口径为「规则层面符合，最终以经办机构审核为准」；金额均为区间或上限口径；示例数据仅供版式确认，不得作为决策依据；禁止利用本系统进行任何虚假申报。
