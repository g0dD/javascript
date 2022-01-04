## 队头阻塞

#### HTTP/2
HTTP/2解决了HTTP的队头阻塞问题，但是并没有解决TCP队头阻塞问题!
HTTP/2仍然会存在TCP队头阻塞的问题，那是因为HTTP/2其实还是依赖TCP协议实现的。

#### http 1.1 keep-alive
HTTP/1.1相比较于HTTP/1.0来说，最主要的改进就是引入了持久连接(keep-alive)。
所谓的持久连接就是：在一个TCP连接上可以传送多个HTTP请求和响应，减少了建立和关闭连接的消耗和延迟。

对于管道连接还是有一定的限制和要求的，其中一个比较关键的就是服务端必须按照与请求相同的顺序回送HTTP响应。

#### TCP 队头阻塞
TCP传输过程中会把数据拆分为一个个按照顺序排列的数据包，这些数据包通过网络传输到了接收端，接收端再按照顺序将这些数据包组合成原始数据，这样就完成了数据传输。
但是如果其中的某一个数据包没有按照顺序到达，接收端会一直保持连接等待数据包返回，这时候就会阻塞后续请求。这就发生了TCP队头阻塞。

#### 网络延迟又称为 RTT(Round Trip Time)。
他是指一个请求从客户端浏览器发送一个请求数据包到服务器，再从服务器得到响应数据包的这段时间。RTT 是反映网络性能的一个重要指标。