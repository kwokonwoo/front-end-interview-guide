首先是**解析URL**，判断输入的是一个合法的URL还是一个待搜索的关键词，并且根据输入的内容进行自动完成、字符编码等操作。

接下来会检查浏览器自带的“预加载HSTS（HTTP严格传输安全）”列表，如果所请求的网站在此列表中，浏览器会使用HTTPS而不是HTTP协议，否则，最初的请求会使用HTTP协议发送。（如果一个网站不在HSTS列表中，也可以要求浏览器对自己使用HSTS政策访问。浏览器向网站发出第一个HTTP请求后，网站会返回浏览器一个响应，请求浏览器只使用HTTPS发送请求。之所以预置HSTS列表是因为第一个HTTP请求可能导致用户受到downgrade attack威胁。）

除此之外，浏览器还会进行一些额外的操作，比如安全检查、访问限制（比如之前国产浏览器限制996.icu）。

接下里进行**DNS查询**，浏览器首先会检查自己的缓存，如果缓存中没有，就会调用系统库函数进行查询：在进行DNS解析之前，会先检查域名是否在本地Hosts中
