# HTML 小工具库

一个轻量级的HTML小工具集合，每个工具都是独立的HTML文件，采用单文件架构设计，无需构建即可直接使用。

## 🚀 特性

- **单文件独立**：每个工具都是一个完整的HTML文件
- **零依赖部署**：所有CSS、JS代码都内嵌在HTML中
- **即开即用**：直接在浏览器中打开即可使用
- **响应式设计**：支持桌面和移动设备
- **数据持久化**：使用localStorage保存用户数据

## 📦 工具列表

### 📱 二维码生成器
- **文件**：`qr-code-generator.html`
- **功能**：生成自定义二维码，支持多种格式和配置选项
- **特性**：
  - 支持URL链接、纯文本、WiFi网络等格式
  - 可自定义二维码大小（128px-512px）
  - 支持多种容错级别（L/M/Q/H）
  - 6种颜色预设方案
  - 实时容量检查和字符计数
  - PNG图片下载和Base64复制
  - 本地记录保存和恢复

### 📈 月度时间序列可视化
- **文件**：`time-series-viewer.html`
- **功能**：月度数据的时间序列可视化分析工具
- **特性**：
  - 支持自定义起始月份
  - 柱状图显示数值趋势
  - 折线图显示环比变化率
  - 显示环比变化值（绝对差值）
  - 数据导入/导出（JSON格式）
  - 本地数据存储
  - 单条数据删除功能

## 🛠️ 技术栈

- **前端框架**：原生HTML5 + CSS3 + JavaScript ES6+
- **图表库**：ECharts 5.4.3
- **数据存储**：localStorage
- **样式规范**：BEM命名约定
- **响应式**：Flexbox + CSS Grid

## 📋 使用方法

### 本地运行
```bash
# 克隆项目
git clone <repository-url>
cd html

# 启动本地服务器
python -m http.server 8000

# 或使用其他服务器
npx serve .
# 或
php -S localhost:8000
```

### 直接使用
1. 下载对应的HTML文件
2. 双击在浏览器中打开
3. 开始使用工具

## 🏗️ 项目结构

```
html/
├── README.md                    # 项目文档
├── AGENTS.md                    # 开发指南
├── index.html                   # 工具库主页
├── qr-code-generator.html       # 二维码生成器
├── time-series-viewer.html      # 时间序列可视化工具
└── tools/                       # 更多工具（待添加）
    ├── tool-name.html
    └── ...
```

## 🎨 开发规范

### 代码风格
- **HTML**：语义化标签，4空格缩进
- **CSS**：BEM命名约定，移动优先
- **JavaScript**：驼峰命名，ES6+语法

### 文件命名
- HTML文件：`kebab-case.html`
- CSS类名：`block__element--modifier`
- JavaScript函数：`verbNoun()` 格式

### 设计原则
- **单文件完整性**：确保HTML文件可独立运行
- **零外部依赖**：除CDN资源外不引用本地文件
- **浏览器兼容**：支持Chrome 90+、Firefox 88+、Safari 14+

## 🔧 自定义开发

### 添加新工具
1. 创建新的HTML文件（遵循命名规范）
2. 实现HTML结构、CSS样式和JavaScript逻辑
3. 确保单文件独立运行
4. 更新README文档

### 代码模板
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>工具名称</title>
    <!-- CSS样式 -->
</head>
<body>
    <!-- HTML结构 -->
    <script>
        // JavaScript逻辑
    </script>
</body>
</html>
```

## 📱 浏览器支持

| 浏览器 | 最低版本 |
|--------|----------|
| Chrome | 90+ |
| Firefox | 88+ |
| Safari | 14+ |
| Edge | 90+ |

## 🤝 贡献指南

1. Fork 项目
2. 创建特性分支：`git checkout -b feature/new-tool`
3. 提交更改：`git commit -m 'Add new tool'`
4. 推送分支：`git push origin feature/new-tool`
5. 提交Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🔗 相关链接

- [ECharts官方文档](https://echarts.apache.org/)
- [MDN Web文档](https://developer.mozilla.org/)
- [Can I Use](https://caniuse.com/)

## 📞 联系方式

如有问题或建议，请通过以下方式联系：
- 提交 Issue
- 发送邮件
- 创建讨论

---

⭐ 如果这个项目对你有帮助，请给个星标支持！