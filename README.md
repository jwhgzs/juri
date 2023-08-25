# Juri
一个简单的 PHP 路由框架，已用在九尾狐工作室的 API 站上。

# 目录结构
* **/config** // 配置文件目录  
    * **index.php** // 主配置文件  
* **/model** // 模板文件目录  
    * **...**（模板目录结构见下文）  
* **/project** // 项目目录  
* **/require** // 插件程序目录  
    * **index.php** // Juri默认函数库（不可随便删除！！）  
* **index.php** // 程序入口（Juri核心程序）  
* **pseudo-static.txt** // 伪静态配置代码  

# 使用指南
* 设置伪静态（参见根目录下的`pseudo-static.txt`文件内容）。
* 在主配置文件config/index.php中配置好路由规则，如下：
```php
<?php
    class c {
        public static $ROUTER = [ // 路由规则配置
            '(*.)\.jwhgzs\.com' => [ // 格式：域名（正则） => 配置
                '/www', // 第一项为解析根目录（/project项目目录的子目录）
                'default' // 第二项为模板名称（/model模板目录的子目录名，无需加/）
            ],
            '(*.)\.jwh\.su' => [
                '/su'
                // 模板名称可不填，默认为default
            ]
        ];
        public static $CROSS_DOMAIN_CONTROL = true; // 是否开启Juri动态跨域设置（默认允许在上面的$ROUTER中指定的域名跨域）
    }
?>
```
* 模板目录结构：（页面最终渲染 = 公共部分头 + 内容 + 公共部分尾）  
* **/model**  
    * **/你的模板名称**  
        * **404.php** // 404 页  
        * **head.php** // 公共部分头  
        * **tail.php** // 公共部分尾  
# 默认路由规则
* 实际访问路径：站点的解析根目录 + 用户访问的 URI
* 访问文件夹不会返回 403 ，而是 404
* PHP 文件可省略后缀
