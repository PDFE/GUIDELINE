# HTML Code Style

- 各种代码压缩工具生成的生产环境版本不在约束范围中
- 各种 HTML 风格的模板（比如 EJS、Swig、Tpl）也在规范的约束范围中


## 全局规范

- 4 空格缩进

> 可以使 HTML 文件的结构更清晰

- `UTF-8` 编码

> 这难道还有什么疑问吗？

- 所有标签和属性名称一律小写

> 谁知道我们以后会不会去写 Angular

- 属性值一律使用双引号

> 要不试试全局单引号？

## 省略规范

- 在没有特殊需求的情况下 不省略可选的结束标签

> 这样更容易看出标签的范围

- 在没有特殊的情况下 建议省略可选的自结束标签末尾斜杠

> 虽然这和 XHTML 规定的规范不同，但是这样文件看起来更干净
> 在上述第二条中一个特殊情况是外部标记语言在解析时遇到的问题  
> 在特殊情况中，需要 `/` 的自结束标签包含属性时在 `/` 应该加空格  
> 下述代码仅作为添加空格例子，实际上 img 标签结尾推荐不带 `/`

```html
<div>
    <img src="pdfe.svg" alt="Project Danmuku Front-End Icon" />
</div>
```

- 无值属性不写等号和空值

```html
<input type="checkbox" checked>
<script src="···" async defer></script>
```

> 操作 DOM 时再说

## 声明相关

- 使用 `<!DOCTYPE html>` 作为唯一的 DTD

> 简洁、兼容性好

- 在 `<head>` 之后紧跟 `<meta charset="UTF-8">`

> 虽然我们仍建议在 `Response Header` 中设置 `content-type:text/html; charset=utf-8`，但是前端没法不保证运维不会偷懒

- 必须有 `<title>`，并尽可能地在不同页面使用不同的标题

> 出于传统 SEO 考量，对于单页应用也可以改善用户体验

## 最佳实践

- 不要使用 input 来代替 button

```html
<!-- 对比用法 -->
<input type="button">
<input type="submit">
```

> 给这类 input 只设置 height 属性的话，在 safari 和 chrome 下并不会出现意料中的样式。同时 button 可以内嵌 HTML，实现更灵活的结构。

- 尽可能地简化 HTML 结构

> 反例： `view-source:https://suka.moe`

- 使用语义化 HTML

> 看起来舒服，搜索引擎爬虫也这么觉得

- 严格遵守标签嵌套规则，禁止让标签出现在不正确的地方

> 因为未来版本可能会不兼容

```
<!-- 用法 -->
<dl>
    <dt>...</dt>
    <dd>
      <ul>
        <li>...</li>
      </ul>
    </dd>
</dl>

<!-- 对比用法 -->
<dl>
    <dt>...</dt>
    <ul>
        <li>...</li>
    </ul>
</dl>
```

- 不允许在标签里内联样式标签和绑定事件

> 难以维护、非规范、容易发生冲突  
> 如果需要，建议进行封装

- 无障碍考量
  - 给图片添加 alt 属性
  - 给无文字超连接添加 title 属性
  - 为所有必需元素添加 aria-label
  - 给可视听的替换型元素内添加描述

```html
<audio>这是 GoligoliTV 的音效</audio>
<canvas>这是一个神奇的效果</canvas>
<iframe src="https://ads.example.com">这是一个广告</iframe>
```
