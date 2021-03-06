## 回顾HTTP/2

HTTP/2协议规范（[RFC 7540](https://httpwg.org/specs/rfc7540.html)）于2015年5月发表，从那之后，它被广泛地在Internet和WWW上实现。

2018年初，前1000大网站中约40%实现了HTTP/2协议，在Firefox发出的HTTPS请求中，近70%的请求由HTTP/2回复。主流的浏览器、服务器、代理均支持了HTTP/2。

HTTP/2的出现揭露了HTTP/1中的很多问题，其中相当一部分对于开发者来说非常麻烦。在HTTP/2之前开发者要用很多变通方法来解决，而HTTP/2的出现解决了这些问题。

HTTP/2的一个主要特性是复用（multiplexing）。通过复用，多个逻辑数据流可以共享一个TCP连接。复用使得很多事情变得更好更快：更好的拥塞控制、更好的带宽利用、更长的TCP连接————这些都使得相比以前，链路更容易实现全速的传输。另外，头部压缩技术减少了带宽的使用。

以前，每个主机和浏览器需要 *六个* 连接，通过HTTP/2，我们只需要 *一个* TCP连接。其实，HTTP/2使用的连接聚合（connection coalescing）和“去分片”（desharding）技术还可以把连接数进一步缩小。

用了HTTP/2之后，HTTP的队头拥塞（head of line blocking）问题好像被解决了。以前客户端发请求之前，必须等待前边的请求回复回来，那样的日子已经一去不复返了。

![http2 man](../images/h2-man.jpg)
