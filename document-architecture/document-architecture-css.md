# CSS 样式文档架构

全站的 CSS 样式，统一使用 SCSS 撰写，架构分别为 `base`、`generic`、`layout`、`modules`、`partials`、`vendor`，相對應的功能說明如下：

| 目录 | 说明 |
| :--- | :--- |
| base | 针对全站定义基础样式的资料夹，如：基础样式、栅栏系统、全站字型与颜色样式 |
| generic | 针对全站定义通用样式，将大量重复使用的样式，转为 Extend 或 maxin，利于重复使用 |
| layout | 客制每个页面样式的资料夹；若有新增页面需要定义该页的样式，请在此资料夹中新增 SCSS 档案 |
| modules | 特定功能模组化样式，如：菜谱列表、产品列表等；若有新增功能需要定义模组化样式，请在此资料夹中新增 SCSS 档案 |
| partials | 全站元件样式，如：Header、Footer、回顶部等；若有新增全站元件需要定义样式，请在此资料夹中新增 SCSS 档案 |
| vendor | 放置 CSS 样式套件的资料夹；若有套件样式，请在此资料夹中新增 SCSS 档案 |

若有新增元件相关的样式，请依照上述说明，放置对应的资料夹或更新档案。
<br/>
> 文档路径: `/src/sass`  
> 转译后路径: `/pubic/css`

```markdown
sass
├ base                                      # 基础样式设定资料夹
│ ├ _base-style-setting.scss                # 全站 reset css 设定   
│ ├ _grid-setting.scss                      # Susy Grid 设定
│ └ _variables.scss                         # 全站使用变数设定
├ generic                                   # 通用样式资料夹
│ ├ _common.scss                            # 全站通用样式
│ ├ _extend.scss                            # 全站继承样式代码
│ └ _maxin.scss                             # 全站混合指令样式代码
├ layout                                    # 页面样式资料夹
├ modules                                   # 模组样式资料夹
│ ├ _module-anchor.scss                     # 作者模组样式
│ ├ _module-article.scss                    # 文章模组样式
│ ├ _module-button.scss                     # 按钮模组样式
│ ├ _module-checkbox.scss                   # 多选模组样式
│ ├ _module-news-list.scss                  # 新闻列表模组样式
│ ├ _module-prod-list.scss                  # 产品列表模组样式
│ ├ _module-recipe-list.scss                # 菜谱列表模组样式
│ ├ _module-search-bar.scss                 # 搜寻模组样式
│ ├ _module-selectbox.scss                  # 下拉选单模组样式
│ ├ _module-subtitle.scss                   # 主标题模组样式
│ ├ _module-tab.scss                        # 页签模组样式
│ └ _module-topic-info.scss                 # 主题介绍模组样式
├ partials                                  # 元件样式资料夹
│ ├ _awards.scss                            # 认证与奖项模块样式
│ ├ _breadcrumb.scss                        # 面包屑样式
│ ├ _careers-temp.scss                      # 加入欣和模块样式
│ ├ _error.scss                             # 错误页面样式
│ ├ _footer-org.scss                        # 首页 Footer 样式
│ ├ _footer.scss                            # Footer 样式
│ ├ _go-top.scss                            # 回顶部 Button 样式
│ ├ _header-org.scss                        # 首页 Header 样式
│ ├ _header.scss                            # Header 样式
│ ├ _key-visual.scss                        # 首图样式
│ ├ _pre-loader.scss                        # Loader 样式
│ ├ _support-mess.scss                      # POP 提示讯息框
│ └ _topics-recommend.scss                  # 推荐主题模块样式
├ vendor                                    # 套件样式资料夹
│ ├ carousel                                # Carousel 套件样式
│ ├ _fontello-embedded.scss                 # Fontello 自订 icon 字体样式 嵌入式
│ ├ _fontello-ie7.scss                      # Fontello 自订 icon 字体样式 for IE7
│ └ _fontello.scss                          # Fontello 自订 icon 字体样式
├ global-org.scss                           # 配适首页客制的通用主样式
├ errors.scss                               # 错误页面主样式
└ global.scss                               # 全站内页的通用主样式
```
### 相关连结与文档
* 若需新增或运维样式请参考：[1.5.1 新增与运维 - CSS](/maintain/maintain-css.md)
* [SCSS \(Compass\) 官网](http://compass-style.org/)
* [Susy 2.2 中文文檔](https://www.w3cplus.com/preprocessor/susy-docs.html)
* [Owl Carousel 2 套件官网](https://owlcarousel2.github.io/OwlCarousel2/)
* [Fontello](http://fontello.com/) - 自订 icon font 网站




