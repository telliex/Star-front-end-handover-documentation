# CSS 样式文档架构

全站的 CSS 样式，统一使用 SCSS 撰写，架构分别为 `base`、`generic`、`layout`、`modules`、`partials`、`vendor`

> 文党路径: `root/src/sass`  
> 转译后路径: `root/pubic/css`

```markdown
sass
├ base                                      # 基础样式设定资料夹
│ ├ _base-style-setting.scss                #    
│ ├ _grid-setting.scss                      #
│ └ _variables.scss                         #
├ generic                                   # 通用样式资料夹
│ ├ _common.scss                            #
│ ├ _extend.scss                            #
│ └ _maxin.scss                             #
├ layout                                    # 页面样式资料夹
├ modules                                   # 模组样式资料夹
│ ├ _module-anchor.scss                     #
│ ├ _module-article.scss                    #
│ ├ _module-button.scss                     #
│ ├ _module-checkbox.scss                   #
│ ├ _module-news-list.scss                  #
│ ├ _module-prod-list.scss                  #
│ ├ _module-recipe-list.scss                #
│ ├ _module-search-bar.scss                 #
│ ├ _module-selectbox.scss                  #
│ ├ _module-subtitle.scss                   #
│ ├ _module-tab.scss                        #
│ └ _module-topic-info.scss                 #
├ partials                                  # 元件样式资料夹
│ ├ _awards.scss                            # 
│ ├ _breadcrumb.scss                        # 面包屑样式
│ ├ _careers-temp.scss                      # 加入欣和
│ ├ _error.scss                             # 错误页面样式
│ ├ _footer-org.scss                        # 首页 Footer 样式
│ ├ _footer.scss                            # Footer 样式
│ ├ _go-top.scss                            # 回顶部 Button 样式
│ ├ _header-org.scss                        # 首页 Header 样式
│ ├ _header.scss                            # Header 样式
│ ├ _key-visual.scss                        # 首图样式
│ ├ _pre-loader.scss                        # Loader 样式
│ ├ _support-mess.scss                      # POP 提示讯息框
│ └ _topics-recommend.scss                  # 
├ vendor                                    # 套件样式资料夹
│ ├ carousel                                # Carousel 套件样式
│ ├ _fontello-embedded.scss                 # Fontello 自定 icon 字体样式 嵌入式
│ ├ _fontello-ie7.scss                      # Fontello 自定 icon 字体样式 for IE7
│ ├ _fontello.scss                          # Fontello 自定 icon 字体样式
│ └ _normalize.scss                         # CSS reset
├ global-org.scss                           #
├ errors.scss                               #
└ global.scss                               #
```



