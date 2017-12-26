# 新增与運維

### 前端工作流程
![](/images/star-work-flow.jpg)


欣和网站运维时会有几种需求：

1. 新页面的增加
![](/images/new-page.jpg)

    说明:
    - route
    > 文档路径：/routes/web.php
    > 功用:由网址的变化启动路
    
    - controller
    > 文档路径：/app/Http/Controllers
    > 功用:route 后需要执行怎样的动作与送进页面什么参数，可在此资料夹内建立

2. 调整个页面的 Meta 资讯
> 文档路径：/resources/views/layouts/meta.blade.php

    请见[1.5.3 PHP](xin-zeng-yu-wei-yun-f/php.md) # Meta

3. 新增或修改 footer 连结
> 文档路径：/resources/views/layouts/footer.blade.php

    请见[1.5.3 PHP](xin-zeng-yu-wei-yun-f/php.md) # Footer

4. 增加修改或调整子选单顺序
> 文档路径：/resources/views/layouts/header.blade.php
    
    请见[1.5.3 PHP](xin-zeng-yu-wei-yun-f/php.md) # Header

5. 已存在的页面进行内容修改
    - JS
    > 文档路径：/src/js/*.es6

    - PHP
    > 文档路径：/resources/views/front/*.blade.php

6. 开发机新建立 
请见[1.3.1 Laravel 开发环境建置](huan-jing-pei-zhi-yu-yun-xing.md)