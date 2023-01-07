
- [webserver的本质](#webserver的本质)
- [一定要使用标准库吗](#一定要使用标准库吗)
- [web3.0](#web30)

# webserver的本质
webserver的本质，实际上就是接收，解析http请求传输的文本字符，理解这些文本字符的指令，然后进行计算，再将返回值组织成hhtp响应的文本字符，通过网络传输过去。



# 一定要使用标准库吗

对于webserver来说，golang提供了net库/http库，分别对应tcp层和http层，它们两个负责的就是http的接收和解析。
现在绝大部份web框架都是基于net/http标准库的。主要原因有两点:
1.  第一相信官方开源的力量。自己实现HTTP协议的解析，不一定会比标准库实现的更好，即使当前标准库有一些不足之处，我们也都相信，随着开源贡献者越来越多，标准库也会最终达到完美。
2.  web服务架构的变化。随着容器化，kubernetes等技术的兴起，业界逐渐达成共识。单机并发性能并不是评判web服务优劣的唯一标准了，易用性和扩展性也是底层库需要考量的。  

``` golang

// 创建一个Foo路由和处理函数
http.Handle("/foo", fooHandler)

// 创建一个bar路由和处理函数
http.HandleFunc("/bar", func(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Hello, %q", html.EscapeString(r.URL.Path))
})

// 监听8080端口
log.Fatal(http.ListenAndServe(":8080", nil))







# web3.0
 