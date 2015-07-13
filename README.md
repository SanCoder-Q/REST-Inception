

# REST — Representational State Transfer
---

REST 的设计思想试图通过统一对资源的标识、请求方式、操作方式来规范 Web 信息传递和表达的方式。

REST 到 ROA (Resources Oriented Architecture)

## 怎样才能 RESTful

    在面向资源的 Web 设计中，资源是设计的主体。因此，ROA 从资源的标识、关联、获取方式等角度对设计提出了不同的要求。

- 采用 URL 标识资源

    一个可获取、可表现、可操作的资源必须具有一个或者多个标识。
    资源的标识应具有良好的 **可读性** 。
    
    URL 应用广泛，具有良好的语意表达结构，是标识资源的最佳工具。
    
    例如：
    ```http://www.tw.com/employess/528491```
    ```http://www.amazon.com/orders/2015/07/14/27149```
    
    同事，URL 也是 HTTP 请求的重要信息之一。
    
- 使用“链接”关联相关的资源，为资源在表现层的状态转换提供支持

    资源在表现层的状态转变可分为两类，一是相同资源的不同表现形式的转变，二是不同资源表现的转变。**URL** 为第一类转变提供支持，而 **超链接** 则为第二类提供支持。
    
    从另一个角度将“超链接”为 URL 提供了应用基础，而 URL 又是“超链接”的实现基础。
    
    例如，要采用xml展现一部电影的信息，我们可以定义为：
    
    ```
    <movie>
        <name>Inception</name>
        <genre>剧情|悬疑|科幻</genre>
        <directors>
        <add ref="http://www.imdb.com/directors/christopher-nolan">克里斯托弗·诺兰</add>
        </directors>
        <starring>
            <add ref = "http://www.imdb.com/actors/leonardo-dicaprio">莱昂纳多·迪卡普里奥</add>
            <add ref = "http://www.imdb.com/actors/marion-cotillard ">玛丽昂·歌迪亚</add>
        </starring>
        <language>英语</language>
        <poster ref = "http://www.imdb.com/posters/inception"/>
        <story>...</story>
    </movie>
    ```
    超链接是资源间各种关联的重要良好表现形式。因此，一个RESTful的Web应用设计应尽可能在表现层采用这种形式描述各类资源的关联。
    
- 使用统一的 CRUD 接口

    在设计业务逻辑行为时，根据不同的关注对象，可以分为面向行为的设计和面向资源的设计。其中，面向行为的设计更加关注操作行为，而REST的思想更加提倡采用面向资源的设计。当设计面向资源时，对其的操作便可简单归纳为 CRUD，以保证对不同资源操作的一致性。
    
    例如，在控制器中，將对不同资源的操作划分为不同的控制器，采用不同的 URL 路由来处理请求。
    
    从另一个角度来看，这样的设计也可以与 HTTP 请求类型相契合。

- 使用标准的 HTTP 方法

    常用的 HTTP 请求类型有：POST、GET、UPDATE、DELETE
    与资源操作的CRUD相互对应。
    
    同时，REST 还提倡在合适的语意环境利用其他的 HTTP 请求类型，如：PUT、HEAD、PATCH、OPTIONS 等来描述对资源的不同操作。
    
- 保证请求的安全性

    对不安全的资源操作，应尽可能保证其 **幂等性**，即保证任意多次执行该操作所产生的影响与单次执行的影响相同。

- 合理的表示资源的不同表示方式

    **应根据请求携带的信息来识别资源表示。**
    
    例如，利用 HTTP 请求的 Content-Type 报头携带的媒体类型返回相应形式的资源表现。

- 尽可能采用无状态的请求

    **状态** 指的是任意一个Web请求必须完全与其他请求隔离，当请求端提出请求时，请求本身包含了相应端为相应这一请求所需的全部信息

    HTTP 协议本身是无状态的，因此在连续的操作中保留状态是一种“费力”的“危险”行为。当连接暂时终端或采用分布式服务器处理请求时，状态很难被保留。因此，REST 提倡采用无状态请求，因为其更强的鲁棒性、可见性和可伸缩性。
    
## 总结

REST 的设计思想旨在通过统一对资源的标识、请求方式、操作方式来规范 Web 信息传递和表达的方式，简化 Web 应用结构的设计过程，增强代码的可读性，提高 Web 应用的适应性和稳定性，促进 Web 应用开发的工程化。

