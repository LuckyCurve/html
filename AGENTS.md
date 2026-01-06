# AGENTS.md - 开发指南

## 项目概述

这是一个HTML小工具库，每个工具都是独立的HTML文件，采用单文件架构设计。所有功能都自包含在单个HTML文件中，包括HTML结构、CSS样式和JavaScript逻辑，无需引用其他文件，便于直接部署和使用。

### 核心设计原则
- **单文件独立**：每个工具都是一个完整的HTML文件
- **自包含设计**：所有CSS、JS代码都内嵌在HTML中
- **零依赖部署**：无需额外配置或构建步骤
- **即开即用**：直接在浏览器中打开即可使用

## 构建和测试命令

### 本地开发
```bash
# 快速预览（推荐，Windows环境）
start *.html  # 在浏览器中直接打开HTML文件，无需服务器

# 或启动本地服务器（推荐使用 Python 3）
uv run python -m http.server 8000

# 或使用 Node.js serve
npx serve .

# 或使用 PHP 内置服务器
php -S localhost:8000
```

### 验证和测试
```bash
# HTML 验证
npx html-validator index.html
npx html-validator qr-code-generator.html
npx html-validator time-series-viewer.html

# CSS 验证
npx css-validator index.html
npx css-validator qr-code-generator.html
npx css-validator time-series-viewer.html

# JavaScript 语法检查
npx eslint index.html
npx eslint qr-code-generator.html
npx eslint time-series-viewer.html

# 检查控制台错误（手动）
# 在浏览器中打开页面，检查开发者工具控制台
```

### 部署
```bash
# 无需构建步骤，直接部署HTML文件
# 支持静态托管：GitHub Pages, Cloudflare Pages, Netlify等
# 每个HTML文件都可以独立部署和访问
```

## 代码风格指南

### HTML 结构
- 使用语义化HTML5标签
- 保持适当的缩进（4个空格）
- 属性顺序：`id` → `class` → `data-*` → 其他属性
- 自闭合标签使用`/>`：`<br/>`, `<img/>`

### CSS 规范
- 使用BEM命名约定（Block__Element--Modifier）
- 移动优先的响应式设计
- CSS变量定义在`:root`中
- 避免内联样式，使用类选择器

### JavaScript 约定
- 使用驼峰命名法（camelCase）
- 常量使用大写下划线：`STORAGE_KEY`
- 函数名使用动词开头：`getData()`, `renderChart()`
- 事件处理函数使用`on`前缀：`onClick`, `onLoad`

### 导入和依赖
- 外部库通过CDN引入，放在`<head>`底部
- 优先使用ES6+语法，保持浏览器兼容性
- 避免全局变量污染，使用IIFE或模块模式
- **严禁引用本地文件**：所有资源必须内嵌或使用CDN
- **保持单文件完整性**：确保HTML文件可独立运行

## 命名约定

### 文件和目录
- HTML文件：`kebab-case.html`（如：`time-series-viewer.html`）
- 资源文件：描述性命名（如：`icon-chart.svg`）

### CSS类名
```css
/* BEM规范 */
.component { }                    /* Block */
.component__element { }           /* Element */
.component--modifier { }          /* Modifier */
.component__element--modifier { } /* Element + Modifier */
```

### JavaScript变量
```javascript
// 常量
const STORAGE_KEY = 'qrGeneratorHistory'; // 或 'latestQRCode'
const MAX_VALUES = 100;

// 变量
let qrCode = null;
let currentQRData = null;

// 函数
function generateQR() { }
function setTemplate(type) { }

// 事件处理
function onInputChange(event) { }
```

## 错误处理规范

### 数据验证
```javascript
function validateInput(value) {
    if (typeof value !== 'number' || isNaN(value)) {
        throw new Error('请输入有效数值');
    }
    return true;
}
```

### 异常捕获
```javascript
try {
    const data = JSON.parse(stored);
    return data;
} catch (error) {
    console.error('数据解析失败:', error);
    return defaultValue;
}
```

### 用户反馈
- 使用`alert()`进行简单错误提示
- 表单验证提供即时反馈
- 网络错误显示友好提示

## 性能优化指南

### DOM操作
- 批量更新DOM，避免频繁重排
- 使用文档片段（DocumentFragment）
- 事件委托减少监听器数量

### 数据处理
- 大数据集使用虚拟滚动
- 图表数据懒加载
- 本地存储合理使用

### 资源加载
- 图片使用WebP格式
- CSS/JS压缩（生产环境）
- CDN加速外部资源

## 浏览器兼容性

### 目标浏览器
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

### Polyfill使用
- 使用`core-js`提供ES6+支持
- `fetch` API的兼容性处理
- CSS Grid和Flexbox的降级方案

## 安全考虑

### 数据安全
- 本地存储数据不包含敏感信息
- 输入数据严格验证
- XSS防护：避免`innerHTML`直接赋值

### 文件操作
- 文件读取限制类型和大小
- 导出文件名安全过滤
- 防止路径遍历攻击

## 调试和开发工具

### 浏览器开发者工具
- Console：查看日志和错误
- Network：监控资源加载
- Storage：检查localStorage数据
- Elements：实时调试DOM和CSS

### 调试技巧
```javascript
// 条件断点
console.log('Debug point:', data);

// 性能监控
console.time('render');
renderChart();
console.timeEnd('render');

// 数据快照
console.table(data.values);
```

## 部署和维护

### 静态托管配置
- GitHub Pages：直接部署
- Cloudflare Pages：零配置部署
- Netlify：拖拽部署

### 版本控制
- 使用语义化版本号
- 提交信息遵循约定式提交
- 标签标记重要版本

### 监控和分析
- 集成Google Analytics
- 错误日志收集
- 性能指标监控

## 扩展开发

### 添加新功能
1. 在HTML中添加UI元素
2. 编写对应的CSS样式
3. 实现JavaScript逻辑
4. 更新数据模型（如需要）
5. 测试功能完整性

### 代码重构
- 提取可复用函数
- 优化算法复杂度
- 改进用户体验
- 增强错误处理

### 第三方集成
- 评估库的必要性和大小
- 检查许可证兼容性
- 考虑CDN稳定性
- 准备降级方案