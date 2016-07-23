title: Composer
speaker: Victor
url: https://github.com/ksky521/nodePPT
transition: cards
files: /js/demo.js,/css/demo.css

[slide]

# 为什么我们要引入 Composer
## 演讲者：Victor

[slide style="background-image:url('/img/bg1.png')"]

# 现代化的 PHP 框架都有哪些特点？
## 使用 Composer 管理依赖
## 遵循 PSR 规范
## 完善的测试支持
## 日志和异常处理机制
## ......

[slide]

# 进入正题，Composer 是什么？
<blockquote> Dependency Manager for PHP </blockquote>
<blockquote>Composer 是 PHP 的依赖管理工具，类似于 nodejs 的 npm 和 ruby 的 bundle。而不是（传统意义上的）包管理工具，比如 yum，apt。</blockquote>

[slide]

# Composer 解决了哪些问题？
* 自动加载 {:&.moveIn}
* 依赖管理

[slide]

# 什么是自动加载
<blockquote> require() 和 include() 的区别是什么？ </blockquote>

[slide]

# 代码示例：不使用自动加载
<div class="columns-1">
<pre><code class="php">
include_once("./myClass.php");
include_once("./myFoo.php");
include_once("./myBar.php");

$obj = new myClass();
$foo = new Foo();
$bar = new Bar();
</code></pre>
</div>

[slide]

# 代码示例：__autoload

<div class="columns-1">
<pre><code class="php">
function __autoload($classname) {
    $filename = "./". $classname .".php";
    include_once($filename);
}

$obj = new myClass();
$foo = new Foo();
$bar = new Bar();
</code></pre>
</div>

[slide]

# 代码示例：spl_autoload_register

<div class="columns-1">
<pre><code class="php">
spl_autoload_register(function ($classname) {
    $filename = "./". $classname .".php";
    include_once($filename);
});

$obj = new myClass();
$foo = new Foo();
$bar = new Bar();
</code></pre>
</div>

[slide]

# Composer 如何实现自动加载

<div class="columns-1">
<pre>composer.json<code class="json">
{
    "require": {
        "monolog/monolog": "1.0.*"
    },
    "autoload": {
        "classmap": ['models/', 'libs/']
    }
}
</code></pre>
<pre>index.php<code class="php">
require __DIR__ . 'vendor/autoload.php';

$obj = new myClass();
$foo = new Foo();
$bar = new Bar();
</code></pre>
</div>

[slide]

# DRY

* Don't Repeat Yourself {:&.moveIn}
* Don't Repeat Others
* Don't Reinvent The Wheel
