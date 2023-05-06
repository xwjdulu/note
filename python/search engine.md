直接运行python程序时，__name__的值为“__main__”
而在其它程序中导入.py文件运行时，__name__的值为文件名，即模块名
区分py文件直接被运行，还是被引入其他程序中。

只要是带着@的,基本上就是装饰器
 装饰器本质上是一个Python函数(其实就是闭包)，它可以让其他函数在不需要做任何代码变动的前提下增加额外功能
 127.0.0.1 本地地址

 @app.route('URL')
def index():
    return <body class="cos-pc   open-homepage-tts s-manhattan-index" ssr="n" style="">
z直接从百度的开发者模式单击元素：以html编辑：copy 记得加引号

网页模板 render_template 函数的第一个参数是模板的文件名，后面的参数都是键值对
Python 内置了 requests 模块，该模块主要用来发 送 HTTP 请求，requests 模块比 urllib 模块更简洁

result = requests.get('https://www.baidu.com/s?wd={}',format(keyword)) wd就是word意思
将请求头设置为：F12:网络：usragent    破反爬虫

1）request是python 自带的，使用 import urllib.request;而 requests需要pip install
（2）request 采用的是urlopen 然后read后进行decode获得网页内容，若需要加header之类的，需要增加request中的Request类来定义header；
而requests更加便捷，直接设置header 和数据格式即可
（3）返回的内容：request返回的一般是utf-8的字符串，requests可以定义返回的类型是json ，或者 byte等
（4）request是先构造get post 请求，再发起；而requests是构造get post 并行发起

