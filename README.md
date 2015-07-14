# ReactEurope Conf 参会感想

React 带来的革命性创新是前端世界过去几年最激动人心的变化。自从接触 React 以来，我深信 React 会改变客户端开发者（包括前端、iOS 和 Android）的开发体验。这次在巴黎举办的 [ReactEurope Conf](https://www.react-europe.org/2015.html) 大会是继第一次在 Facebook 总部举办后最大的 React 活动。超过10位来自React、GraphQL、Relay 团队的核心技术成员也出席大会进行分享。这次代表 [Strikingly](https://www.strikingly.com/)（似乎也是国内唯一家公司）去参加，想写下一些参会感想。

Keynote [1] 讲师是来自 Facebook 的 Christopher Chedeau (vjeux)。他分享了 React 生态系统四大方面 （Data, Targets, Language, Packager）的变化。这次大会所有的内容我觉得也都是这四方面的延伸。我印象最深的是 Data 和 Targets，也是这篇文章主要想分享的内容。

# Data

React 定义自己为 MVC 中的 View。这让前端开发者从 V 开始去思考 UI 设计。但现在针对数据操作和获取方式，社区里还没有一种公认的方法。这也是任何写 React 应用时最难处理的地方。

## Flux

对于 M 和 V，Facebook 提出了 Flux 的概念。之后，几乎每个月出现一新的 Flux 库，他们都有各自的特色，有的对服务器渲染支持比较好，有的运用了更多函数式编程的概念。很多 Flux 库更像是实验，这有助于 React 生态的生长，但不可否认的是，未来会有大量 Flux 库慢慢死去，而只有少数会存留下来或进行合并。。大会上 React Hot Reload 的作者 Dan Abramov 也介绍了自己新的 Flux 库 - Redux。这也是大会上最受瞩目的演讲之一。Redux 认为 Flux Store 就像函数式编程里的 reducer

`f(init_state, action) => state`

通过这种方式，我们只要存下所有 action 就可以像时光穿梭一样去到任何时间点上的状态。

Redux 应该是现在最函数式的 Flux 库。私下和 Dan Abramov 的交流中，他告诉我，他正在和其他几位 Flux 库作者接触并有意进行合并，也许 Redux 会是少数存留下的 Flux 库之一。

**相关演讲：**

[1] [Christopher Chedeau - Keynote](https://www.youtube.com/watch?v=PAA9O4E1IM4&list=PLCC436JpVnK0Phxld2dD4tM4xPMxJCiRD&index=1)

**GraphQL / Relay**

GraphQL 和 Relay 是我这次参加大会最关心的技术。在构建大型前端应用时，前端 和 后端 工程师 通过 API 的方式进行合作。API 也是双方的协议。现在主流的方式是 RESTful API，然而在实践中，我们发现 RESTful 在一些真实生产环境的需求下不是很适用。往往我们需要构建自定义 endpoint，违背了 Restful 的设计理念。GraphQL 是我认为目前最完美的解决方法。这次大会也没有让人失望，推出了 GraphQL 的规范 并 开源了 JavaScript GraphQL 库。

然而要让 GraphQL 成为主流，Facebook 需要打造一个像 React 这样的生态系统。目前只推出了规范 和 GraphQL JavaScript 库（适应于 Node.js 应用）。要想在你自己的应用上用 GraphQL 还必须要有后端语言提供 GraphQL 库的支持。比如 Strikingly 需要 GraphQL Ruby 库。这不仅仅需要前端工程师。我认为这将会比 React 生态系统更难建立。Facebook 需要整个社区的参与才能达到。

[Image: https://quip.com/-/blob/ZbWAAAAIGXR/mHxsRKw0rLWJRPutm-EcUQ]
（图片来自《Creating a GraphQL Server》[5] 演讲）

**Relay**

Relay 是 Facebook 提出的在 React 上应用 GraphQL 的方案。React 的基础单位是组件（component），构建大型应用就是组合和嵌套组件。以组件为单位的设计模式是目前社区里最认可的，这也是前端世界的趋势之一。每个组件需要的数据也应该在组件内部定义。Relay 让组件可以自定义其所需要 GraphQL 数据格式，在组件实例化的时候再去 GraphQL 服务器获取数据。Relay 也会自动构建嵌套组件的 GraphQL 查询，这样多个嵌套的组件只需要发一次请求。这次大会也公布了 Relay 将会在8月份开源。

**Immutability**

React 社区接收了很多函数式编程的想法，其中受 clojure 影响很深。immutable 数据的使用就是来自 clojure 社区。当年 Om，这个用 ClojureScript 写的 React 在速度上居然完虐原生 Javascript 版本的 React。这让整个社区都震惊了。其中一个原因就是 ClojureScript 使用了 immutable 数据。React 社区里也冒出了 immutable.js，这让 javascript 里也能用起 immutable 数据，完美弥补了javascript 做负责数据对象比较的先天性不足。immutable.js 的出现也成为了构建大型 React 应用的必备。本次大会甚至有在讨论是否把 immutable.js 直接纳入 javascript 语言中。我个人认为小型应用不会遇到 virtual DOM 渲染瓶颈，引入 immutable.js 只会让数据操作很累赘。

**相关演讲：**

[2] [Dan Abramov - Live React: Hot Reloading with Time Travel](https://www.youtube.com/watch?v=xsSnOQynTHs&list=PLCC436JpVnK0Phxld2dD4tM4xPMxJCiRD&index=7)
[3] [Lee Byron - Exploring GraphQL](https://www.youtube.com/watch?v=WQLzZf34FJ8&index=5&list=PLCC436JpVnK0Phxld2dD4tM4xPMxJCiRD)
[4] [Joseph Savona - Relay: An Application Framework For React](https://www.youtube.com/watch?v=IrgHurBjQbg&index=8&list=PLCC436JpVnK0Phxld2dD4tM4xPMxJCiRD)
[5] [Nick Schrock & Dan Schafer - Creating a GraphQL Server](https://www.youtube.com/watch?v=gY48GW87Feo&index=6&list=PLCC436JpVnK3HvUSAHpt-LRJkIK8pQG6R)


# Targets

对于 Virtual DOM 的讨论，很多人会说速度快过于真正的 DOM。这样的讨论可以让人快速入门理解 React，但是真正写过 React 应用的人会明白速度并不是 Virtual DOM 的精髓。我认为 Virtual DOM 的存在帮助我们做到了两件事。第一是申明式 UI。通过 Virtual DOM，UI 不再是一个不断被更变的 DOM，你只要申明 UI 是怎么生成的，React 会自动帮你把 UI 的改变渲染到真正的 DOM 上。这种新的思维方式让你可以不用手动操作真正的 DOM。第二是多 target。我们一直在讲 web，但 React 让我们做到 web 以外的 target。Virtual DOM 更像是 UI Virual Machine，自动帮你映射到真正的实现上。可以是 浏览器 DOM 、iOS UI、Android UI。在大会上，甚至有人做了 React 映射到 Terminal Text UI。

多 Targets 是这次讨论的主要话题之一。多 targets 的根本是 **提高开发者体验**。这是本次大会上屡次被提起的概念。我们如何在保持一样的用户体验下，提高开发者体验。

任何一家有多客户端的公司都面临同一个问题：在各种客户端语言里重新造轮子。开发者需要学习新的语言、写和维护类似的功能。提升客户端开发者体验就是减少学习成本和维护成本。这就是 React 提倡的 learn once, write everywhere。

本次大会上也有一些鼓舞人心的消息。Facebook 内部 Ads Manager iOS 版本由 7 位工程师用 React Native 花了 5 个月完成。而 Android 版本，是同一班人，3个月内完成。代码重用率达到了 87%。而且在 React Native 中，大家比较关心的动画效果和速度的问题，也在这次大会上通过 Facebook 工程师 Spencer Ahrens 演讲中的流畅演示得到了令人满意的答案。

多 targets 也可以是在单个平台更深度的结合。这次大会最让我目瞪口呆的是 Sebastian Markbåge 的演讲《DOM as a Second-class Citizen》。演讲中他畅想 React 直接输出到浏览器架构的底层。

[Image: https://quip.com/-/blob/ZbWAAAAIGXR/JCYHFuE0r7HRI4IUx2rdyw]
这是浏览器的渲染架构

[Image: https://quip.com/-/blob/ZbWAAAAIGXR/BJuronhMKilRGIDkLWkeaQ]
这是 Sebastian Markbåge 认为 React 可以做的事情。

我当时听完后凌乱了。姑且不谈该不该这么做，我觉得 React 通过 Virtual DOM 能让我们有机会做到就已经让我兴奋不已了。也说明了 Facebook 在设计 React 时已经考虑到超越 DOM。真 TM 的 NB。。。

**相关演讲：**

[6] [Spencer Ahrens - React Native: Building Fluid User Experiences](https://www.youtube.com/watch?v=xDlfrcM6YBk&list=PLCC436JpVnK0Phxld2dD4tM4xPMxJCiRD&index=4)
[7] [Mikhail Davydov - Back to Text UI](https://www.youtube.com/watch?v=ee_U2t-8L48&list=PLCC436JpVnK0Phxld2dD4tM4xPMxJCiRD&index=10)
[8] [Sebastian Markbåge - DOM as a Second-class Citizen](https://www.youtube.com/watch?v=Zemce4Y1Y-A&index=11&list=PLCC436JpVnK0Phxld2dD4tM4xPMxJCiRD)

## 其他演讲

篇幅原因，我不详细讨论 Language 和 Packager。但对有几个演讲也留下了深刻印象：

[Sebastian McKenzie - Improving Your Workflow With Code Transformation](https://www.youtube.com/watch?list=PLCC436JpVnK3HvUSAHpt-LRJkIK8pQG6R&v=OFuDvqZmUrE)

演讲者是 Babel 的作者 Sebastian McKenzie。Babel 是目前社区里最受欢迎的代码编译工具。Facebook 团队甚至已经决定转用 Babel 而不再维护之前内部使用的 jstranform。

使用 webpack 或 browserify 这类工具编译代码已经渐渐成为前端工程师工作流程的一部分。Sebastian 这次分享了编译代码所带来的好处。他也刚在 Twitter 上宣布加入 Facebook，全心做 Babel。期待未来 Babel 能够带来更多的可能性。

[Image: https://quip.com/-/blob/ZbWAAAAIGXR/phleWv0E6ekNN9n67lKIgA]
[Cheng Lou - The State of Animation in React](https://www.youtube.com/watch?v=1tavDv5hXpo&list=PLCC436JpVnK3HvUSAHpt-LRJkIK8pQG6R&index=2)

最早关注 Cheng Lou 是因为他写的 [react-tween-state](https://github.com/chenglou/react-tween-state) 动画库。一直一来大家都对动画应该在 React 里怎么表达（示）为状态感到困惑。react-tween-state 是我认为最符合 React 思维的做法。把位移存在 state 里，然后通过 javascript 动态渲染新的位置。不过大家对该做法是否能达到满意的速度一直持有保留态度。这次在他的演讲中也展现出了非常出色的效果和速度，非常值得一看。

## 总结

这次赫门在 JSConf 2015 上提出了前端的摩尔定理：前端每18月会难一倍。我觉得前端之所以变化这么快，是因为我们现在面临着前所未有的工程化挑战。今天的前端复杂度跟几年前完全不是一个等级。这也促使着社区要找到在这种复杂度下能保持开发效率和开发体验的工具和设计模式。React 社区从其他领域（游戏渲染、ClojureScript、函数式编程）偷师学艺，结合前端面临的独特问题，提出了一系列解决方案。我觉得 React 社区在各方面都推动着前端社区往前进。这对整个社区都是好事。我也希望前端各个框架，就像  Christopher Chedeau 在 keynote 上说的，停止攻击，互相学习，共同推动整个社区的发展。

It's an exciting time to be a front-end developer.

郭达峰

CTO of Strikingly.com

感谢 题叶、寸志、沈瑜杰、冯哲锐、王徐阳、徐欣 协助修订校对稿件

（这也是 Strikingly 团队做的首次技术分享，之后我们也会继续分享更多的前端技术及相关资讯，请关注我的[微博](http://www.weibo.com/dfguo)和 [GitHub](https://github.com/dfguo)）
