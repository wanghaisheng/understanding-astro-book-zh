

[](/understanding-astro/understanding-astro-book/edit/master/ch3.md)

[](#-understanding-astro)🚀 Understanding Astro 了解Astro
=======================================================

By [Ohans Emmanuel](https://www.ohansemmanuel.com/) 作者：Ohans Emmanuel

  

[](#chapter-3-build-your-own-component-island)Chapter 3: Build Your Own Component Island  
第3章构建自己的组件岛
------------------------------------------------------------------------------------------------------

> “What I cannot create, I do not understand” — Richard Feynman  
> “我不能创造的东西，我不理解”--理查德·费曼

Astro’s fast narrative relies on component islands, which allow using other framework components like React, Vue, or Svelte in our Astro applications. This chapter will guide us in creating our own component island from the ground up.  
Astro的快速叙述依赖于组件岛，这允许在我们的Astro应用程序中使用其他框架组件，如React，Vue或Svelte。本章将指导我们从头开始创建我们自己的组件岛。

  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch3/watch-instead@3x.png)](https://ohans.me/understanding-astro-udemy)

  
  

[![](/understanding-astro/understanding-astro-book/raw/master/view-project.png)](https://github.com/understanding-astro/build-your-own-component-island)

  
  

[](#what-youll-learn)What you’ll learn 您将学到的内容
----------------------------------------------

*   An overview of different web application rendering techniques.  
    不同Web应用程序渲染技术的概述。
*   Build your own component islands implementation from scratch.  
    从头开始构建您自己的组件岛实现。
*   Comprehend the island architecture.  
    了解岛上的建筑。

* * *

[](#a-brief-history-of-how-we-got-here)A brief history of how we got here  
我们如何走到这一步的简史
----------------------------------------------------------------------------------------

To ensure the coming technical implementation is built on a solid understanding, let’s peep into the past and explore the several application rendering techniques we may employ on a frontend application.  
为了确保即将到来的技术实现建立在坚实的理解之上，让我们看看过去，并探索我们可能在前端应用程序上使用的几种应用程序渲染技术。

It is essential to note that this isn’t an exhaustive guide to front-end application rendering. However, we’ll learn enough to understand and appreciate the component islands architecture.  
需要注意的是，这并不是一个关于前端应用程序呈现的详尽指南。然而，我们将学到足够的知识来理解和欣赏组件岛的架构。

### [](#where-it-all-begins)Where it all begins  
一切开始的地方

In simple terms, there are two main actors in serving an application to a user:  
简单地说，在向用户提供应用程序时有两个主要参与者：

1.  The user client, e.g., a web browser  
    用户客户端，例如，网页浏览器
2.  The application server 应用服务器

To display a website, a user requests a resource from an application server.  
为了显示网站，用户从应用服务器请求资源。

[![The web browser requesting article.html from an application server.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/a.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/a.png)

_The web browser requesting article.html from an application server.  
Web浏览器从应用服务器请求article.html。_  
  
  

With these two actors at play, a significant architectural decision you’ll make when building any decent frontend application is whether to render an application on the client or server[1](#user-content-fn-1-55f92bec3c7101b92f5c57e1d82ed429).  
有了这两个参与者，在构建任何像样的前端应用程序时，您将做出的一个重要的架构决策是在客户端还是服务器上呈现应用程序 [1](#user-content-fn-1-55f92bec3c7101b92f5c57e1d82ed429) 。

Let’s briefly explore both options.  
让我们简要地探讨这两种选择。

* * *

### [](#client-side-rendering-csr)Client-side rendering (CSR)  
客户端渲染（CSR）

[![Choosing client side rendering.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/1.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/1.png)

_Choosing client side rendering.  
选择客户端渲染。_  
  
  

By definition, a client-side rendered application renders pages directly in the browser using Javascript. All logic, data-fetching, templating and routing are handled on the client (the user’s browser).  
根据定义，客户端呈现的应用程序使用JavaScript直接在浏览器中呈现页面。所有逻辑、数据获取、模板和路由都在客户端（用户的浏览器）上处理。

[![An overview of a client-side rendered application.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/a-1.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/a-1.png)

_An overview of a client-side rendered application.  
客户端呈现的应用程序的概述。_  
  
  

The past years saw the rise of client-side rendering, particularly among single-page applications. You’ve likely seen this in action if you’ve worked with libraries like React or Vue.  
在过去的几年里，客户端呈现的兴起，特别是在单页面应用程序中。如果您使用过React或Vue等库，您可能已经看到了这一点。

For a practical overview, consider the webpage for a blog article with a like count and a comment section below the initial viewport.  
对于一个实用的概述，考虑一个博客文章的网页，该博客文章具有点赞计数和在初始视口下方的评论部分。

[![A blog article with a dynamic sidebar and a comment section below the article.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/a-2.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/a-2.png)

_A blog article with a dynamic sidebar and a comment section below the article.  
一个博客文章，带有动态侧边栏和文章下方的评论部分。_  
  
  

If this application was entirely client-side rendered, the simplified rendering flow would look like this:  
如果这个应用程序完全是在客户端渲染的，那么简化的渲染流程将如下所示：

1.  The user visits your website.  
    用户访问您的网站。
2.  Your static server returns a near-empty `HTML` page to the browser.  
    静态服务器会向浏览器返回一个几乎空的 `HTML` 页面。
3.  The browser fetches the linked script file in the `HTML` page.  
    浏览器在 `HTML` 页面中获取链接的脚本文件。
4.  The Javascript is loaded and parsed.  
    加载并解析JavaScript。
5.  The data for the article, number of comments and comments are fetched.  
    获取文章的数据、评论和评论的数量。
6.  A fully interactive page is shown to the user.  
    向用户显示完全交互的页面。

[![Visualising the rendering process from a user's perspective.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/a-3.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/a-3.png)

_Visualising the rendering process from a user's perspective.  
从用户的角度可视化渲染过程。_  
  
  

#### [](#the-pros-of-client-side-rendering-csr)The pros of client-side rendering (CSR)  
客户端渲染（CSR）的优点

*   The user gets back the resource from the server quickly. In our case, a near-empty `HTML` page, but on the bright side, the user receives that quickly! In technical terms, client-side rendering yields a high time to first byte (**TTFB**)[2](#user-content-fn-2-55f92bec3c7101b92f5c57e1d82ed429)  
    用户可以快速地从服务器取回资源。在我们的例子中，一个几乎空的 `HTML` 页面，但从好的方面来看，用户很快就收到了！在技术术语中，客户端渲染产生了一个高的第一字节时间（TTFB） [2](#user-content-fn-2-55f92bec3c7101b92f5c57e1d82ed429)
*   Arguably accessible to reason about. All logic, data-fetching, templating and routing are handled in one place - the client.  
    可论证的可论证的所有逻辑、数据获取、模板和路由都在一个地方处理-客户端。

#### [](#the-cons-of-client-side-rendering)The cons of client-side rendering  
客户端渲染的缺点

*   It potentially takes the user a long time to see anything tangible on our page, i.e., they’re initially met with an empty screen. Even if we change the initial `HTML` page sent to the browser to be an empty application shell, it still potentially takes time for the user to see eventual data, i.e., after the Javascript is parsed and the data fetched from the server.  
    用户可能要花很长时间才能看到我们页面上的任何有形内容，即，他们一开始看到的是一个空白的屏幕。即使我们将发送到浏览器的初始 `HTML` 页面更改为空的应用程序外壳，用户仍然可能需要时间来查看最终数据，即在解析JavaScript并从服务器获取数据之后。
    
*   As the application grows, the amount of Javascript parsed and executed before displaying data increases. This can impact mobile performance negatively.  
    随着应用程序的增长，在显示数据之前解析和执行的JavaScript数量也会增加。这可能会对移动的性能产生负面影响。
    
*   The page's time to interactivity (**TTI**)[3](#user-content-fn-3-55f92bec3c7101b92f5c57e1d82ed429) suffers, e.g., it takes long before our users can interact with the comments. All Javascript must be parsed, and all associated data must be fetched first.  
    页面的交互时间（TTI） [3](#user-content-fn-3-55f92bec3c7101b92f5c57e1d82ed429) 遭受例如我们的用户需要很长时间才能与评论互动。所有的JavaScript都必须被解析，并且所有相关的数据必须首先被提取。
    
*   Detrimental SEO if not implemented correctly.  
    有害的SEO，如果没有正确实施。
    

* * *

### [](#server-side-rendering)Server-side rendering 服务器端渲染

[![Choosing server-side rendering.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/choosing-ssr.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/choosing-ssr.png)

_Choosing server-side rendering.  
选择服务器端渲染。_  
  
  

Let’s assume we’re unhappy with client-side rendering and decide to do the opposite.  
让我们假设我们对客户端渲染不满意，并决定做相反的事情。

On the opposing end of the rendering pole lies server-side rendering.  
在渲染极的另一端是服务器端渲染。

In a server-side rendered application, a user navigates to our site, and the server generates the full `HTML` for the page and sends it back to the user.  
在服务器端呈现的应用程序中，用户导航到我们的网站，服务器为页面生成完整的 `HTML` 并将其发送回用户。

In our example, here’s what a simplified flow would look like:  
在我们的示例中，简化的流程如下所示：

1.  The user visits our website.  
    用户访问我们的网站。
2.  The data for the article, user profile and comments are fetched on the server.  
    文章、用户配置文件和评论的数据在服务器上获取。
3.  The server renders the `HTML` page with the article, the number of comments and other required assets.  
    服务器呈现具有文章、评论数量和其他所需资产的 `HTML` 页面。
4.  The server sends the client a fully formed `HTML` page.  
    服务器向客户端发送完整格式的 `HTML` 页面。

[![Visualising the rendering process from a user's perspective.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/aa.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/aa.png)

_Visualising the rendering process from a user's perspective.  
从用户的角度可视化渲染过程。_  
  
  

NB: it is assumed that the server sends a mostly static `HTML` page with minimal Javascript needed for interactivity.  
注意：假设服务器发送一个大部分静态的 `HTML` 页面，具有交互性所需的最小JavaScript。

#### [](#the-pros-of-server-side-rendering)The pros of server-side rendering  
服务器端渲染的优点

*   As soon as the user browser receives our fully formed `HTML` page, they can almost immediately interact with it, e.g., the rendered comments. There’s no need to wait for more Javascript to be loaded and parsed. In performance lingo, the time to interactivity (**TTI**) equals the first contentful paint (**FCP**).[4](#user-content-fn-4-55f92bec3c7101b92f5c57e1d82ed429)  
    一旦用户浏览器接收到我们完全形成的 `HTML` 页面，他们几乎可以立即与它交互，例如，的评论。没有必要等待更多的JavaScript被加载和解析。在性能术语中，交互时间（TTI）等于第一内容绘制（FCP）。 [4](#user-content-fn-4-55f92bec3c7101b92f5c57e1d82ed429)
*   Great SEO benefits as search engines can index your pages and crawl them just fine.  
    搜索引擎优化的好处，因为搜索引擎可以索引你的网页，并抓取它们就好了。

#### [](#the-cons-of-server-side-rendering)The cons of server-side rendering  
服务器端渲染的缺点

*   Generating pages on the server takes time. In our case, we must wait for all the relevant data to be fetched on the server. As such, the time to first byte(**TTFB**)[5](#user-content-fn-5-55f92bec3c7101b92f5c57e1d82ed429) is slow.  
    在服务器上生成页面需要时间。在我们的例子中，我们必须等待服务器上获取所有相关数据。因此，到第一字节（TTFB） [5](#user-content-fn-5-55f92bec3c7101b92f5c57e1d82ed429) 的时间慢。
*   Resource intensive: the server takes on the burden of rendering content for users and bots. As a result, associated server costs increase as rendering needs to be done on the server.  
    资源密集型：服务器承担了为用户和机器人呈现内容的负担。因此，随着渲染需要在服务器上完成，相关的服务器成本增加。
*   Full page reloads for every requested server resource.  
    为每个请求的服务器资源重新加载完整页。

* * *

### [](#server-side-rendering-with-client-side-hydration)Server-side rendering with client-side hydration  
服务器端渲染和客户端合成

We’ve explored rendering on both sides of the application rendering pole. However, what if there was a way to use server and client-side rendering? Some strategy right in the middle of the hypothetic rendering pole?  
我们已经在应用程序渲染极的两侧探索了渲染。但是，如果有一种方法可以使用服务器端和客户端渲染呢？在假设的渲染极中间的一些策略？

[![Choosing SSR with client-side hydration.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/ssr-with-client-rehydration.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/ssr-with-client-rehydration.png)

_Choosing SSR with client-side hydration.  
选择SSR与客户端水合。_  
  
  

If we were building an interactive application and working with a framework like React or Vue, a widely common approach is to render on the server and hydrate on the client.  
如果我们正在构建一个交互式应用程序，并使用像React或Vue这样的框架，一个广泛使用的方法是在服务器上渲染并在客户端上进行水合。

Hydration, in layperson’s terms, means re-rendering the entire application again on the client to attach event handlers to the DOM and support interactivity.  
用外行人的话说，水合意味着在客户机上再次重新呈现整个应用程序，以将事件处理程序附加到DOM上并支持交互性。

In theory, this is supposed to give us the wins of server-side rendering plus the interactivity we get with rich client-side rendered applications.  
从理论上讲，这应该给予我们带来服务器端渲染的好处，加上丰富的客户端渲染应用程序的交互性。

In our example, here’s what a simplified flow would look like:  
在我们的示例中，简化的流程如下所示：

1.  The user visits our website.  
    用户访问我们的网站。
2.  The data for the article, user profile and comments are fetched on the server.  
    文章、用户配置文件和评论的数据在服务器上获取。
3.  The server renders the `HTML` page with the article, the number of comments and other required assets.  
    服务器呈现具有文章、评论数量和其他所需资产的 `HTML` 页面。
4.  The server sends the client a fully formed `HTML` page alongside the Javascript client runtime.  
    服务器向客户端发送一个完整的 `HTML` 页面以及JavaScript客户端运行时。
5.  The client then “boots up” Javascript to make the page interactive.  
    然后客户端“启动”JavaScript以使页面具有交互性。

Making an otherwise static page interactive (e.g., attaching event listeners) is called hydration.  
使原本静态的页面成为交互式的（例如，附加事件监听器）被称为水合。

[![Visualising the rendering process from a user's perspective.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/ssr-csr-hydrate-flow.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/ssr-csr-hydrate-flow.png)

_Visualising the rendering process from a user's perspective.  
从用户的角度可视化渲染过程。_  
  
  

#### [](#the-pros-of-server-side-rendering-with-client-side-hydration)The pros of server-side rendering with client-side hydration  
服务器端渲染与客户端水合的优点

*   Benefits of SSR, e.g., quick FP and FMP  
    SSR的好处，例如，快速FP和FMP
*   Can power highly interactive applications.  
    可以支持高度交互的应用程序。
*   Supported rendering style in most frontend frameworks such as React and Vue.  
    大多数前端框架支持渲染风格，如React和Vue。

#### [](#the-cons-of-server-side-rendering-with-client-side-hydration)The cons of server-side rendering with client-side hydration  
服务器端渲染与客户端水合的缺点

*   Slow time to first byte — similar to standard SSR.  
    第一个字节的时间慢-类似于标准SSR。
*   It can delay time to Interactivity (TTI) by making the user interface look ready before completing client-side processing. The period where the UI looks ready but is unresponsive (not hydrated) is what’s been — quite hilariously — dubbed the uncanny valley.  
    它可以通过在完成客户端处理之前使用户界面看起来准备就绪来延迟交互时间（TTI）。UI看起来准备就绪但反应迟钝（没有水分）的时期被称为“神秘谷”。

NB: this assumes certain parts of our application, such as the likes and comments, can be interacted with, e.g., clicked to perform further action.  
NB：这假设我们的应用程序的某些部分，例如喜欢和评论，可以与之交互，例如，单击以执行进一步操作。

* * *

### [](#partial-hydration-for-the-win)Partial hydration for the win  
部分水合作用

Combining server-side rendering with client-side hydration has the potential to offer the best of both worlds. However, it is not without its demerits.  
将服务器端渲染与客户端水化相结合，有可能实现两全其美。然而，它并非没有缺点。

One way to tackle the heavy delay in time to interactivity (TTI) seems obvious. Instead of hydrating the entire application, why not hydrate only the interactive bits?  
解决交互时间（TTI）严重延迟的一种方法似乎显而易见。与其对整个应用程序进行补水，为什么不只对交互位进行补水呢？

[![Partial hydration vs full-page hydration.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/p-hydration.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/p-hydration.png)

_Partial hydration vs full-page hydration.  
部分水合vs全页水合。_  
  
  

As opposed to hydrating the entire application client side, partial hydration refers to hydrating specific parts of an application while leaving the rest static.  
与对整个应用程序客户端进行水化相反，部分水化指的是对应用程序的特定部分进行水化，同时使其余部分保持静止。

For example, in our application, we’d leave the rest of the page static while hydrating just the like button and comment section.  
例如，在我们的应用程序中，我们将保持页面的其余部分静态，而只对喜欢按钮和注释部分进行补水。

We may also take partial hydration further and implement what’s known as lazy hydration. For example, our application has a comment section below the initial viewport.  
我们还可以进一步进行部分水合，并实施所谓的惰性水合。例如，我们的应用程序在初始视口下面有一个注释部分。

In this case, we may hydrate the like button when the page is loaded and hydrate the comment section only when the user scrolls below the initial viewport.  
在这种情况下，我们可以在页面加载时使用“like”按钮，并且仅在用户滚动到初始视口下方时使用“注释”部分。

[![Hydrate the comment section at a later time.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/a-4.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/a-4.png)

_Hydrate the comment section at a later time.  
稍后再添加评论部分。_  
  
  

Talk about flexibility! 谈论灵活性！

#### [](#the-pros-of-partial-hydration)The pros of partial hydration  
部分补水的好处

*   The same benefits of server-side rendering with client-side hydration.  
    服务器端渲染与客户端水化的好处相同。
*   Faster time to interactivity as the entire application isn’t hydrated.  
    更快的交互时间，因为整个应用程序没有水合。

#### [](#the-cons-of-partial-hydration)The cons of partial hydration  
部分水合的缺点

*   If most of the parts of the application are interactive and have a high priority, the advantage of partial hydration could be arguably minimal, i.e., the entire application would take just as long to be hydrated.  
    如果应用程序的大多数部分是交互式的并且具有高优先级，则部分水合的优点可以论证为最小，即，整个应用将花费同样长的时间来水合。

### [](#where-does-the-island-architecture-come-from)Where does the island architecture come from?  
岛屿建筑从何而来？

The island architecture is built upon the foundation of partial hydration. Essentially, the islands architecture refers to having “islands of interactivity” on an otherwise static `HTML` page.  
岛屿建筑是建立在部分水化的基础上的。本质上，岛架构指的是在其他静态的 `HTML` 页面上具有“交互岛”。

[![Islands of interactivity on an otherwise static webpage.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/independent-islands.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/independent-islands.png)

_Islands of interactivity on an otherwise static webpage.  
静态网页上的互动孤岛。_  
  
  

To make sense of this, think of these islands as partially hydrated components. So our entire page isn’t hydrated, but rather these islands.  
为了理解这一点，我们可以把这些岛看作是部分水合的成分。所以我们的整个页面并没有被水合，而是这些岛屿。

* * *

[](#a-partial-hydration-islands-architecture-implementation)A partial hydration islands architecture implementation  
部分水合岛架构实现
-------------------------------------------------------------------------------------------------------------------------------

It’s game time, mate.  
游戏时间到了伙计

This section might seem challenging, but I suggest taking your time and coding along if possible. But, of course, you’ll probably be fine if you’re a more experienced engineer!  
这一部分可能看起来很有挑战性，但我建议你花点时间编写代码，如果可能的话。但是，当然，如果你是一个更有经验的工程师，你可能会很好！

We will begin building our own island architecture implementation from the ground up. In more technical terms, we will implement a framework-independent partial hydration islands architecture implementation.  
我们将从头开始构建我们自己的岛屿架构。在更多的技术术语中，我们将实现独立于框架的部分水合岛架构实现。

Phew! That’s a mouth full.  
呼！这是一个嘴满。

Let’s break that down.  
我们来分析一下。

### [](#objectives)Objectives 目的

The goal of this exercise is not to build a full-blown library or to create an exact clone of the Astro Island implementation. No!  
本练习的目标不是构建一个完整的库或创建Astro Island实现的精确克隆。不！

Our objective is to peel back the perceived layer of complexity and strip down component islands to a fundamental digestible unit.  
我们的目标是剥离感知的复杂性层和剥离组件岛到一个基本的可消化的单位。

Here are the functional requirements for our island implementation:  
以下是我们岛实施的功能要求：

1.  Framework-independent: our solution must work across multiple frameworks, e.g., `Preact`, `Vue`, `Petite-Vue` and `React`.  
    独立于框架：我们的解决方案必须跨多个框架工作，例如， `Preact` 、 `Vue` 、 `Petite-Vue` 和 `React` 。
2.  A partial hydration islands architecture implementation: we will strip away Javascript by default and only hydrate on an as-needed basis.  
    部分水化岛体系结构实现：我们将默认删除JavaScript，只在需要时添加水合物。
3.  No frontend build step: for simplicity, our implementation will disregard a frontend build step, e.g., using `babel.`  
    无前端构建步骤：为了简单起见，我们的实现将忽略前端构建步骤，例如，使用 `babel.`
4.  Support lazy hydration: this is a form of partial hydration where we can trigger hydration later and not immediately after loading the site. e.g., if an island is off-screen (not in the viewport), we will not load the Javascript for the island. We will only do so when the island is in view.  
    支持懒惰补水：这是部分水合的一种形式，其中我们可以稍后而不是在装载部位之后立即触发水合。例如，如果一个岛在屏幕外（不在视口中），我们不会加载该岛的JavaScript。我们只有在看到岛屿的时候才会这样做。

### [](#installation)Installation 安装方式

Let’s call our island module `mini-island`.  
让我们把岛模块命名为 `mini-island` 。

To install `mini-island`, a developer will import our _soon-to-be-built_ module as shown below:  
要安装 `mini-island` ，开发人员将导入我们即将构建的模块，如下所示：

<script type\="module"\>
  {/\*\* import a mini-island.js module \*\*/}
  import "/mini-island.js"
</script\>

To enjoy the benefits of partial hydration, developers will add `mini-island.js` to their page with the promise of having a small JS footprint — a small price to pay to get partially hydrated islands of interactivity.  
为了享受部分水合的好处，开发人员将在他们的页面上添加 `mini-island.js` ，并承诺拥有一个小的JS足迹-一个小的代价来获得部分水合的交互性岛屿。

### [](#api-design)API design API设计

Our first objective is to make sure our solution is framework agnostic. An excellent native solution for framework-agnostic implementations is **web components**[6](#user-content-fn-6-55f92bec3c7101b92f5c57e1d82ed429).  
我们的第一个目标是确保我们的解决方案与框架无关。一个优秀的与框架无关的实现的本地解决方案是web组件 [6](#user-content-fn-6-55f92bec3c7101b92f5c57e1d82ed429) 。

By definition, web components are a suite of technologies that allows us to create reusable custom elements.  
根据定义，Web组件是一套技术，允许我们创建可重用的自定义元素。

If you’re new to web components, instead of rendering a standard HTML element, e.g., a `div`, we will create our custom HTML element, `mini-island`.  
如果您是Web组件的新手，则不使用标准的HTML元素，例如，a `div` ，我们将创建自定义HTML元素 `mini-island` 。

`mini-island.js` will expose a custom element with the following basic usage:  
`mini-island.js` 将公开一个具有以下基本用法的自定义元素：

<mini-island\>This is an island</mini-island\>

Within `<mini-island>`, a developer will be able to leverage an island of interactivity on an otherwise static page.  
在 `<mini-island>` 中，开发人员将能够利用静态页面上的交互孤岛。

We will support three different `<mini-island>` attributes to handle partial and lazy hydration: `client:idle`, `client:visible` and `client:media={QUERY}`.  
我们将支持三个不同的 `<mini-island>` 属性来处理部分水合和惰性水合： `client:idle` 、 `client:visible` 和 `client:media={QUERY}` 。

Here’s an example of how they’d be used on `<mini-island>`:  
下面是一个如何在 `<mini-island>` 上使用它们的示例：

<mini-island client:idle /\>
<mini\-island client:visible /\>
<mini-island client:media\="(max-width: 400px)" /\>

These attributes will affect how the island is hydrated.  
这些属性将影响岛屿如何水合。

*   `client:idle`: load and hydrate javascript when the whole page is loaded[7](#user-content-fn-7-55f92bec3c7101b92f5c57e1d82ed429) and the browser is idle.[8](#user-content-fn-8-55f92bec3c7101b92f5c57e1d82ed429)  
    `client:idle` ：当整个页面加载完毕 [7](#user-content-fn-7-55f92bec3c7101b92f5c57e1d82ed429) 浏览器空闲时加载并水合JavaScript。 [8](#user-content-fn-8-55f92bec3c7101b92f5c57e1d82ed429)
*   `client:visible`: we will load and hydrate the island javascript once the island is visible, e.g., entered the user’s viewport.  
    `client:visible` ：我们将加载和水合岛JavaScript一旦岛是可见的，例如，进入了用户的视口。
*   `client:media`: we will load and hydrate the island once the query is satisfied, e.g., `client:media="(max-width: 400px)"`.  
    `client:media` ：一旦满足查询，我们将加载并水合岛，例如，#1。

There’s one final piece to our API design. How will developers define the scripts or markup to be hydrated?  
我们的API设计还有最后一个部分。开发人员将如何定义要水合的脚本或标记？

We will use the `<template>` ￼ HTML element, the content template element.  
我们将使用 `<template>` HTML元素，内容模板元素。

<!-- ❌ incorrect usage: -->
<mini-island client:idle\>
  <script\>
    console.log("this should be partially hydrated");
  </script\>
</mini-island\>

<!-- ✅ correct usage: -->
<mini-island client:idle\>
  <!-- use the <template> element -->
  <template\>
    <script\>
      console.log("this should be partially hydrated");
    </script\>
  </template\>
</mini-island\>

`<template>` is generally used for holding `HTML` that shouldn’t be rendered immediately on page load. However, the `HTML` may be instantiated via Javascript.  
`<template>` 通常用于保存不应该在页面加载时立即呈现的 `HTML` 。然而， `HTML` 可以通过JavaScript实例化。

For example, assuming a user wanted to log a warning to the console but wanted to use our island implementation, they’d do the following:  
例如，假设一个用户想要在控制台记录一个警告，但想要使用我们的孤岛实现，他们会执行以下操作：

<mini-island\>
  <h2\> Warning, something may be wrong </h2\>
  <template data-island\>
     <script type\="module"\>
		console.error("something has gone wrong")
     </script\>
  </template\>
<mini-island\>

When the above is rendered, the `<h2> Warning, something may be wrong </h2>` message will be displayed. However, child elements of the `template` will not be rendered by default, i.e., the `script` will never be executed.  
当呈现上述内容时，将显示 `<h2> Warning, something may be wrong </h2>` 消息。然而，默认情况下， `template` 的子元素将不呈现，即： `script` 永远不会被执行。

Our `mini-island` implementation will grab the content of the `template` and initialise the `<script>` when desired.  
我们的 `mini-island` 实现将抓取 `template` 的内容，并在需要时初始化 `<script>` 。

For example, if the user passes a `client:visible` attribute, we will ensure the script only runs when the island is visible.  
例如，如果用户传递了 `client:visible` 属性，我们将确保脚本仅在岛可见时运行。

<mini-island client:visible\>
  <h2\> Warning, something may be wrong </h2\>
  <template data-island\>
     <script type\="module"\>
		console.error("something has gone wrong")
     </script\>
  </template\>
<mini-island\>

It’s important to note that we expect the developer to pass a `data-island` attribute to the `template`. We will only hydrate templates with the `data-island` attribute to avoid interfering with other potential user-defined templates.  
值得注意的是，我们希望开发人员将 `data-island` 属性传递给 `template` 。我们将只使用 `data-island` 属性来合成模板，以避免干扰其他潜在的用户定义模板。

Don’t worry if these seem fuzzy right now; we will implement and test these with examples that’ll solidify your understanding.  
不要担心这些现在看起来模糊不清;我们将通过一些例子来实现和测试这些，以巩固您的理解。

### [](#getting-started)Getting started 开始使用

Ready? 准备好了吗？

Start by creating a `mini-island.js` file in whatever directory you want.  
从创建一个 `mini-island.js` 文件开始在任何你想要的目录。

In `mini-island`, create a barebones custom component as annotated below:  
在 `mini-island` 中，创建一个barebones自定义组件，如下所示：

// 📂 mini-island.js

/\*\*
 \* Define a MiniIsland class to encapsulate the behaviour of 
our custom element, <mini-island>
 \* This class extends HTMLElement where the HTMLElement 
interface represents any HTML element.
 \*/
class MiniIsland extends HTMLElement {
  /\*\*
   \* Define the name for the custom element as a static class 
property.
   \* Custom element names require a dash to be used in them 
(kebab-case).
   \* The name can't be a single word. ✅ mini-island ❌ 
miniIsland
   \*/
  static tagName \= "mini-island";
  /\*\*
   \* Define the island element attributes
   \*, e.g., <mini-island data-island>
   \*/
  static attributes \= {
    dataIsland: "data-island",
  };
}

/\*\*
 \* Our solution relies heavily on web components. Check that the
 \* browser supports web components via the 'customElements' property
 \*/

if ("customElements" in window) {
  /\*\*
   \* Register our custom element on the CustomElementRegistry object using the define method.
   \*
   \* NB: The CustomElementRegistry interface provides methods for registering custom elements and querying registered elements.
   \*
   \* NB: The arguments to the define method are the name of the custom element (mini-island)
   \* and the class (MiniIsland) that defines the behaviour of the custom element.
   \*
   \* NB: "MiniIsland.tagName" below represents the static class property, i.e., "static tagName".
   \*/
  window.customElements.define(MiniIsland.tagName, MiniIsland);
} else {
  /\*\*
   \* custom elements not supported, log an error to the console
   \*/
  console.error(
    "Island cannot be initiated because Window.customElements is unavailable."
  );
}

Let’s get some basic manual testing to nudge us in the right direction.  
让我们进行一些基本的手动测试，以推动我们朝着正确的方向前进。

Create a new `demos/initial.html` file with the following content:  
新建一个包含以下内容的 `demos/initial.html` 文件：

<!DOCTYPE html\>
<html lang\="en"\>
  <head\>
    <meta charset\="UTF-8" /\>
    <meta http-equiv\="X-UA-Compatible" content\="IE=edge" /\>
    <meta name\="viewport" content\="width=device-width, initial-scale=1.0" /\>
    <title\>Initial island demo</title\>

    <script type\="module"\>
      import "../mini-island.js";
    </script\>
  </head\>
  <body\>
    <h1\>Initial island demo</h1\>
  </body\>
</html\>

To view this via a local web server, run the following command from the project directory:  
要通过本地Web服务器查看此内容，请从项目目录运行以下命令：

 npx local-web-server

By default, this should start a local static web server on port `8000`. We may now view the initial demo page on `http://localhost:8000/demos/initial.html`  
默认情况下，这应该在端口 `8000` 上启动本地静态Web服务器。我们现在可以在 `http://localhost:8000/demos/initial.html` 上查看初始演示页面

[![The initial demo page.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/CleanShot%202023-05-14%20at%2007.29.14.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/CleanShot%202023-05-14%20at%2007.29.14.png)

_The initial demo page.  
初始演示页面。_  
  
  

Let’s confirm that our custom element `mini-island` is registered rendering the custom element with a simple paragraph child element:  
让我们确认我们的自定义元素 `mini-island` 已注册，并使用简单的段落子元素呈现自定义元素：

<!-- 📂 demos/initial.html -->
...
<body\>
  <h1\>Initial island demo</h1\>
  <mini-island\>
    <p\>Hello future island</p\>
  </mini-island\>
</body\>

This will render the custom element and the `Hello future island` paragraph as expected:  
这将按照预期呈现自定义元素和 `Hello future island` 段落：

[![Rendering the custom element with a child element.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/CleanShot%202023-05-14%20at%2007.27.26.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/CleanShot%202023-05-14%20at%2007.27.26.png)

_Rendering the custom element with a child element.  
使用子元素呈现自定义元素。_  
  
  

Now, let’s go ahead and add some Javascript within `<mini-island>` as shown below:  
现在，让我们继续在 `<mini-island>` 中添加一些JavaScript，如下所示：

<!-- 📂 demos/initial.html -->
...
<mini-island\>
  <p\>Hello future island</p\>
  <script type\="module"\>
    console.warn("THIS IS A WARNING FROM AN ISLAND");
  </script\>
</mini-island\>

If you refresh the page and check the browser console, we should see the warning logged.  
如果刷新页面并检查浏览器控制台，我们应该会看到记录的警告。

[![Console warning from the island.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/CleanShot%202023-05-14%20at%2007.32.44.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/CleanShot%202023-05-14%20at%2007.32.44.png)

_Console warning from the island.  
从岛上发出控制台警告。_  
  
  

This means the script was fired almost immediately. Not our ideal solution.  
这意味着剧本几乎立即被解雇。不是我们的理想解决方案。

While images and video account for over 70% of the bytes downloaded for the average website, byte per byte, JavaScript has a more significant negative impact on performance.  
虽然图像和视频占网站平均下载字节数的70%以上，但JavaScript对性能有更大的负面影响。

So, our goal is to ensure Javascript doesn’t run by default. We will render any relevant markup in the island (HTML and CSS) but defer the loading of Javascript.  
因此，我们的目标是确保JavaScript在默认情况下不会运行。我们将在岛上呈现任何相关的标记（HTML和CSS），但延迟JavaScript的加载。

### [](#leveraging-the-content-template-element)Leveraging the content template element  
利用内容模板元素

`<template>` is a native HTML element that’s near perfect for our use case.  
`<template>` 是一个原生HTML元素，对于我们的用例来说几乎是完美的。

The contents within a `<template>` element are parsed for correctness by the browser but not rendered.  
`<template>` 元素中的内容由浏览器进行正确性分析，但不会呈现。

For example, let’s go ahead and wrap the script from the previous example in a `<template>` element as shown below:  
例如，让我们继续将上一个示例中的脚本包装在一个 `<template>` 元素中，如下所示：

<!-- 📂 demos/initial.html -->
...
<mini-island\>
  <p\>Hello future island</p\>
  <template\>
    <script type\="module"\>
      console.warn("THIS IS A WARNING FROM AN ISLAND");
    </script\>
  </template\>
</mini-island\>

If you refresh the page, you’ll notice that the `Hello future island` paragraph is rendered, but the `script` within `<template>` isn’t, i.e., no log to the console.  
如果你刷新页面，你会发现 `Hello future island` 段落被渲染，但是 `<template>` 中的 `script` 段落没有被渲染，即：没有登录到控制台。

This is step one: isolate javascript from being loaded right away.  
这是第一步：立即将JavaScript隔离开来。

However, the eventual goal here is to ensure the developer can decide when to run the `script` within our island `template`.  
然而，这里的最终目标是确保开发人员可以决定何时在我们的岛 `template` 中运行 `script` 。

As discussed in the proposed API implementation, consider the following:  
如建议的API实现中所讨论的，请考虑以下几点：

<mini-island client:visible\>
  <p\>Hello future island</p\>
  <template\>
    <script type\="module"\>
      console.warn("THIS IS A WARNING FROM AN ISLAND");
    </script\>
  </template\>
</mini-island\>

With the `client:visible` attribute, we will only initialise the script when the island is visible (within the user viewport).  
使用 `client:visible` 属性，我们将仅在岛可见时初始化脚本（在用户视口内）。

Without taking the `client:` attributes into question, let’s go ahead and initialise any template content as soon as the `<mini-island>` element is attached to the DOM.  
在不考虑 `client:` 属性的情况下，让我们继续，并在 `<mini-island>` 元素附加到DOM之后立即初始化任何模板内容。

Consider the annotated code below:  
考虑下面的注释代码：

// 📂 mini-island.js
class MiniIsland extends HTMLElement {
  // ...

  /\*\*
   \* The connectedCallback is a part of the custom elements lifecycle callback.
   \* It is invoked anytime the custom element is attached to the DOM
   \*/
  async connectedCallback() {
    /\*\*
     \* As soon as the island is connected, we will go ahead and hydrate the island
     \*/
    await this.hydrate();
  }

  hydrate() {
    /\*\*
     \* Retrieve the relevant <template> child elements of the island
     \*/
    const relevantChildTemplates \= this.getTemplates();
  }
}

Now, we will turn our attention to `getTemplates()`.  
现在，我们将注意力转向 `getTemplates()` 。

Since `<mini-island>` is a custom element extending a standard `HTMLElement`, we can access traditional DOM querying methods such as `querySelectorAll`[9](#user-content-fn-9-55f92bec3c7101b92f5c57e1d82ed429).  
由于 `<mini-island>` 是一个自定义元素，扩展了标准的 `HTMLElement` ，我们可以访问传统的DOM查询方法，如 `querySelectorAll` [9](#user-content-fn-9-55f92bec3c7101b92f5c57e1d82ed429) 。

So, let’s use `querySelectorAll` to retrieve a list of all child template elements with a `data-island` attribute.  
所以，让我们使用 `querySelectorAll` 检索所有具有 `data-island` 属性的子模板元素的列表。

// 📂 mini-island.js
// ...

getTemplates() {
  /\*\*
   \* querySelectorAll() returns a list of the document's elements that match the specified group of selectors.
   \* The selector, in this case, is of the form "template\[data-island\]."
   \*, i.e., this.querySelectorAll("template\[data-island\]")
  \*/
  return this.querySelectorAll(
    \`template\[${MiniIsland.attributes.dataIsland}\]\`
  );
}

Note that the `data-island` attribute is retrieved in the code above via `MiniIsland.attributes.dataIsland`.  
请注意， `data-island` 属性是通过 `MiniIsland.attributes.dataIsland` 在上面的代码中检索的。

Also, do you remember why we’re using the `data-island` attribute?  
另外，你还记得为什么我们要使用 `data-island` 属性吗？

This is because we want to give developers the flexibility to use standard `<template>` elements within our island. So, our island will only concern itself with `<template data-island>` elements.  
这是因为我们希望给予开发人员灵活地在我们的岛中使用标准 `<template>` 元素。所以，我们的岛只关心 `<template data-island>` 元素。

Now that we’ve retrieved the template node via `getTemplates()`, we will grab its content and hydrate it.  
现在我们已经通过 `getTemplates()` 检索了模板节点，我们将获取其内容并对其进行水合处理。

Let’s update the `hydrate` method as shown below:  
让我们更新 `hydrate` 方法，如下所示：

// 📂 mini-island.js
// ...
hydrate() {
    /\*\*
     \* Retrieve the relevant <template> child elements of the island
     \*/
    const relevantChildTemplates \= this.getTemplates();
    /\*\*
     \* Grab the DOM subtree within the template and replace the template with live content
     \*/
    this.replaceTemplates(relevantChildTemplates);
}

The `replaceTemplates` method is as shown below:  
`replaceTemplates` 方法如下所示：

// 📂 mini-island.js
// ...
 replaceTemplates(templates) {
    /\*\*
     \* Iterate over all nodes in the template list.
     \* templates refer to a NodeList of templates
     \* node refers to a single <template>
     \*/
    for (const node of templates) {
      /\*\*
       \* replace the <template> with its HTML content
       \* e.g., <template><p>Hello</p></template> becomes <p>Hello</p>
       \*/
      node.replaceWith(node.content);
    }
  }

Do you see what we’re doing here?  
你看到我们在做什么了吗？

We’re grabbing the template DOM subtree, accessing its content and removing the `<template>` element.  
我们抓取模板DOM子树，访问它的内容并删除 `<template>` 元素。

<!-- 👀 before -->
<mini-island\>
  <template\>
    <p\>Hello</p\>
  </template\>
  <mini-island\>
    <!-- ✅ after -->
    <mini-island\>
      <p\>Hello</p\>
      <mini-island\></mini-island\></mini-island\></mini-island
\></mini-island\>

This will attach the content to the DOM and kick off rendering and script loading.  
这将把内容附加到DOM并启动渲染和脚本加载。

With the templates now replaced, let’s go ahead and change the initial demo file to hold a more tangible example, as shown below:  
现在替换了模板，让我们继续修改初始演示文件以保存一个更具体的示例，如下所示：

<!\-- 📂 demos/initial.html \--\>
<mini-island\>
  <p\>Hello future island</p\>
  <template data-island\>
    <script type\="module"\>
      console.warn("THIS IS A WARNING FROM AN ISLAND");
    </script\>
  </template\>
</mini-island\>

Note that the `<template>` element has the `data-island` attribute. This is how we signal to the island to hydrate the template content.  
请注意， `<template>` 元素具有 `data-island` 属性。这就是我们如何向岛屿发出信号，让它们水合模板内容物。

Now, refresh your browser and notice how the `console.warn` is triggered.  
现在，刷新您的浏览器并注意 `console.warn` 是如何触发的。

[![Hydrated island script.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/CleanShot%202023-05-15%20at%2007.10.42.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/CleanShot%202023-05-15%20at%2007.10.42.png)

_Hydrated island script. 水化物岛文字。_  
  
  

If you also inspect the elements, you’ll notice that the `<template>` has been replaced with its live child content.  
如果您还检查这些元素，您会注意到 `<template>` 已被其活动子内容替换。

[![Replaced island <template> element.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/CleanShot%202023-05-15%20at%2007.11.54.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/CleanShot%202023-05-15%20at%2007.11.54.png)

_Replaced island template element.  
已替换岛模板元素。_  
  
  

We’re officially hydrating our island!  
我们正式给我们的岛补水了！

### [](#handling-lazy-hydration-via-client-attributes)Handling lazy hydration via “client:” attributes  
通过“client：”属性处理延迟水合

Our current solution isn’t going to win us any awards. As soon as the island is attached to the DOM, we hydrate the island. Let’s make it better by introducing lazy hydration.  
我们目前的解决方案不会为我们赢得任何奖项。一旦岛屿连接到DOM上，我们就给岛屿补水。让我们通过引入懒惰水合作用来改善它。

Lazy hydration is a form of partial hydration where we hydration later — not immediately after page load.  
懒惰水合是一种部分水合形式，我们稍后水合-而不是在页面加载后立即水合。

Lazy hydration is powerful because we can determine what’s essential or priority for our site, i.e., we can choose to delay the execution of unimportant Javascript.  
懒惰的水合作用是强大的，因为我们可以确定什么是我们的网站的必要或优先事项，即，我们可以选择延迟不重要的JavaScript的执行。

Update the `initial.html` document to consider our first use case. Here’s the updated code:  
更新 `initial.html` 文档以考虑我们的第一个用例。下面是更新后的代码：

<!-- 📂 demos/initial.html -->
<!DOCTYPE html\>
<html lang\="en"\>
  <head\>
    <meta charset\="UTF-8" />
    <meta http-equiv\="X-UA-Compatible" content\="IE=edge" />
    <meta name\="viewport" content\="width=device-width, initial-scale=1.0" />
    <title\>Initial island demo</title\>

    <script type\="module"\>
      import "../mini-island.js";
    </script\>
  </head\>
  <body\>
    <h1\>Initial island demo</h1\>
    <!-- 👀 look here  -->
    <p style\="padding-bottom: 100vh"\>Scroll down</p\>
    <!-- 👀 look here  -->
    <mini-island client:visible\>
      <p\>Hello island</p\>

      <template data-island\>
        <script type\="module"\>
          console.warn("THIS IS A WARNING FROM AN ISLAND");
        </script\>
      </template\>
    </mini-island\>
  </body\>
</html\>

[![The client:visible demo.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/CleanShot%202023-05-15%20at%2007.18.38.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/CleanShot%202023-05-15%20at%2007.18.38.png)

_The client:visible demo.  
客户端：visible demo。_  
  
  

We now have a paragraph that reads `scroll down`, which has a large enough bottom padding to push the island off the viewport.  
我们现在有一个段落，它有一个足够大的底部填充，可以将岛从视口中推出去。

With the `client:visible` attribute on the `<mini-island>`, we should not hydrate the island except when it’s visible, i.e., the user scrolls to view the island.  
使用 `<mini-island>` 上的 `client:visible` 属性，我们不应该对岛进行水合，除非它是可见的，即用户滚动以查看岛。

However, test this in your browser.  
不过，请在浏览器中测试。

[![The island is hydrated before being in view](/understanding-astro/understanding-astro-book/raw/master/images/ch3/CleanShot%202023-05-15%20at%2007.20.43.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/CleanShot%202023-05-15%20at%2007.20.43.png)

_The island is hydrated before being in view.  
这个岛在进入视野之前已经被水化了。_  
  
  

The script is hydrated before we scroll (as soon as the page loads), and the `THIS IS A WARNING FROM AN ISLAND` message is logged.  
脚本在我们滚动（页面加载后）之前被水合，并记录 `THIS IS A WARNING FROM AN ISLAND` 消息。

Let’s prevent this from happening.  
让我们阻止这一切发生。

To achieve this, take a second look at the island hydrate method:  
要实现这一点，请再看看岛水合物方法：

  hydrate() {
    const relevantChildTemplates \= this.getTemplates();
    this.replaceTemplates(relevantChildTemplates);
  }

Conceptually, we aim to wait for specific loading conditions to be met before we replace the island templates. In this case, we want to wait until the island is visible.  
从概念上讲，我们的目标是等待特定的加载条件得到满足，然后再更换岛模板。在这种情况下，我们希望等到岛屿可见。

In pseudo-code: 在伪代码中：

  hydrate() {
     // Get island conditions, e.g., client:visible, client:idle
    // If these exist, wait for the conditions to be met before the next steps
    const relevantChildTemplates \= this.getTemplates();
    this.replaceTemplates(relevantChildTemplates);
  }

To manage our island loading conditions, let’s introduce a new `Conditions` class as shown below:  
为了管理我们的岛加载条件，让我们引入一个新的 `Conditions` 类，如下所示：

// 📂 mini-island.js

// ...
class Conditions {}

// same existing code ...
if ("customElements" in window) {
  window.customElements.define(MiniIsland.tagName, MiniIsland);
} else {
  console.error(
    "Island cannot be initiated because Window.customElements is unavailable."
  );
}

Within `Conditions`, we will introduce a static property that’s a key-value representation of the `client:` attribute and async methods.  
在 `Conditions` 中，我们将引入一个静态属性，它是 `client:` 属性和异步方法的键值表示。

[![An object with key-value corresponding to attribute and promise condition.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/attr-promise.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/attr-promise.png)

_An object with key-value corresponding to attribute and promise condition.  
一个对象，键值对应于属性和promise条件。_  
  
  

Our conditions will be fulfilled at a later unknown time. So, we will represent these with async functions. These async functions will return promises that are resolved when the associated condition is met.  
我们的条件将在稍后未知的时间实现。因此，我们将用async函数来表示它们。这些async函数将返回promise，当满足相关条件时，promise将被解析。

Here’s the representation of this in code:  
下面是代码中的表示：

// // 📂 mini-island.js
// ...
class Conditions {
  /\*\*
   \* A map of loading conditions and their respective async methods
   \*/
  static map \= {
    idle: Conditions.waitForIdle,
    visible: Conditions.waitForVisible,
    media: Conditions.waitForMedia,
  };

  static waitForIdle() {
    return new Promise((resolve) \=> resolve());
  }

  static waitForVisible() {
    return new Promise((resolve) \=> resolve());
  }

  static waitForMedia() {
    return new Promise((resolve) \=> resolve());
  }
}

At the moment, the promises resolve immediately. However, let’s go ahead and flesh out our use case for `client:visible`.  
目前，承诺立即兑现。然而，让我们继续充实我们的用例 `client:visible` 。

First, we will expose a `getConditions` method on the `Conditions` class. The method will check if a certain DOM node (in our case, our `mini-island`) has an attribute in the form of `client:${condition}`.  
首先，我们将在 `Conditions` 类上公开一个 `getConditions` 方法。该方法将检查某个DOM节点（在我们的例子中，我们的 `mini-island` ）是否具有 `client:${condition}` 形式的属性。

Below’s the annotated implementation:  
下面是带注释的实现：

// 📂 mini-island.js

class Conditions {
  // ...
  static getConditions(node) {
    /\*\*
     \* The result variable will hold the
     \* key:value representing condition:attribute.
     \* e.g., For <mini-island client:visible>
     \* result should be { visible: "" }
     \* and for <mini-island client:media="(max-width: 400px)" />
     \* result should be { media: "(max-width: 400px)" }
     \*/
    let result \= {};

    /\*\*
     \* Loop over all keys of the static map,
     \*, i.e., \["idle", "visible", "media"\]
     \*/
    for (const condition of Object.keys(Conditions.map)) {
      /\*\*
       \* Check if the node has the attribute
       \* of the form "client:${key}".
       \*/
      if (node.hasAttribute(\`client:${condition}\`)) {
        /\*\*
         \* If the node has the attribute...
         \* save the condition (key) - attribute (value)
         \* to the result object
         \*/
        result\[condition\] \= node.getAttribute(\`client:${condition}\`);
      }
    }
    /\*\* return the result \*/
    return result;
  }
}

Next, we will expose a `hasConditions` method responsible for checking if an island has one or more conditions:  
接下来，我们将公开一个 `hasConditions` 方法，负责检查一个岛是否有一个或多个条件：

// 📂 mini-island.js
// ...
class Conditions {
  // ...
  static hasConditions(node) {
    /\*\*
     \* Using the "getConditions" static class method, retrieve
     \* a conditions attributes map
     \*/
    const conditionAttributesMap \= Conditions.getConditions(node);

    /\*\*
     \* Check the length of the result keys to determine if there are
     \* any loading conditions on the node
     \*/
    return Object.keys(conditionAttributesMap).length \> 0;
  }
}

With `hasConditions` and `getConditions` ready, let’s go ahead and use these within the `MiniIsland` hydrate method.  
`hasConditions` 和 `getConditions` 准备好了，让我们继续在 `MiniIsland` 水合物方法中使用它们。

First, here’s the current state of the `hydrate` method.  
首先，这里是 `hydrate` 方法的当前状态。

// 📂 mini-island.js

class MiniIsland extends HTMLElement {
  // ...
  hydrate() {
    const relevantChildTemplates \= this.getTemplates();
    this.replaceTemplates(relevantChildTemplates);
  }
  // ...
}

Now, update the method with the following. I have provided annotations to make it easier to understand.  
现在，使用以下内容更新该方法。我提供了注释，使其更容易理解。

// 📂 mini-island.js

class MiniIsland extends HTMLElement {
  // ...
  async hydrate() {
    /\*\*
     \* conditions will hold an array of potential
     \* promises to be resolved before hydration
     \*/
    const conditions \= \[\];

    /\*\*
     \* Get the condition - attribute value map
     \* NB: the argument passed to
     \* \`Conditions.getConditions\` is the island node
     \*/
    let conditionAttributesMap \= Conditions.getConditions(this);

    /\*\*
     \* Loop over the conditionAttributesMap variable
     \*/
    for (const condition in conditionAttributesMap) {
      /\*\*
       \* Grab the condition async function from the static map
       \* Remember that the function that returns a promise when invoked
       \*/
      const conditionFn \= Conditions.map\[condition\];

      /\*\*
       \* Check if the condition function exists
       \*/
      if (conditionFn) {
        /\*\*
         \* Invoke the condition function with two arguments:
         \* (1) The value of the condition attribute set on the node
         \* For example:
         \* for <mini-island client:visible /> this is an empty string ""
         \* for <mini-island client:media="(max-width: 400px)" />
         \* This is the string "(max-width: 400px)"
         \*
         \* (2) The node, i.e., the island DOM node
         \*/
        const conditionPromise \= conditionFn(
          conditionAttributesMap\[condition\],
          this
        );

        /\*\*
         \* append the promise to the conditions array
         \*/

        conditions.push(conditionPromise);
      }

      /\*\*
       \* Await all promise conditions to be
       \* resolved before replacing the template nodes
       \*/
      await Promise.all(conditions);
      /\*\*
       \* Retrieve the relevant <template> child elements of the island
       \*/
      const relevantChildTemplates \= this.getTemplates();
      /\*\*
       \* Grab the DOM subtree in the template
       \* and replace the template with live content
       \*/
      this.replaceTemplates(relevantChildTemplates);
    }
  }
}

At the moment, remember that our condition promises in `Conditions` resolve immediately.  
此时此刻，请记住，我们的条件承诺在 `Conditions` 立即解决。

Before we test our solution, we must satisfy the condition for the `client:visible` attribute.  
在测试解决方案之前，我们必须满足 `client:visible` 属性的条件。

How do we ensure that the island is visible?  
我们如何确保岛屿是可见的？

The best solution here is to use the `IntersectionObserver` API[10](#user-content-fn-10-55f92bec3c7101b92f5c57e1d82ed429). Let’s take advantage of that as shown below:  
这里最好的解决方案是使用 `IntersectionObserver` API [10](#user-content-fn-10-55f92bec3c7101b92f5c57e1d82ed429) 。让我们利用这一点，如下所示：

// 📂 mini-island.js

class Conditions {
  // ...
  /\*\*
   \*
   \* @param noop - the value of the condition attribute.
   \* This is named "noop" as it is not relevant in this condition, i.e.,
   \* as per our API, client:visible always has a falsy attribute value, e.g.,
   \* ✅ <mini-island client:visible />
   \* ❌ <mini-island client:visible={some-value} />
   \* @param el - the node element.
   \* This represents our island DOM node passed during hydration
   \* @returns - a Promise that resolves when "el" is visible
   \* NB: relies on the Intersection Observer API
   \*/
  static waitForVisible(noop, el) {
    /\*\*
     \* If the Intersection Observer API is not available,
     \* go ahead and exit immediately.
     \*/
    if (!("IntersectionObserver" in window)) {
      return;
    }

    /\*\*
     \* Otherwise, set up a new Promise that is resolved when the
     \* node parameter (our island DOM node) is visible
     \*/
    return new Promise((resolve) \=> {
      let observer \= new IntersectionObserver((entries) \=> {
        let \[entry\] \= entries;

        /\*\*
         \* is it visible?
         \*/
        if (entry.isIntersecting) {
          /\*\*
           \* remove observer
           \*/
          observer.unobserve(entry.target);
          /\*\*
           \* resolve promise
           \*/
          resolve();
        }
      });

      /\*\*
       \* set up the observer on the "el" argument
       \*/
      observer.observe(el);
    });
  }
}

This is excellent work!  
干得好！

Return to the demo `initial.html` application running in your browser, refresh, and notice how the island behaves.  
返回到浏览器中运行的演示 `initial.html` 应用程序，刷新并注意小岛的行为。

The island is no longer hydrated until we scroll down and the island is visible 🎉  
岛屿不再含水，直到我们向下滚动，岛屿是可见的 🎉

Well done, mate! Give yourself a round of applause and a cuppa tea. We’ve smashed it! Take a pause if you need one, and let’s get on the next set of requirements when you’re ready.  
干得好伙计给予自己一点掌声和一杯茶。我们把它砸了！如果您需要暂停一下，准备好后，让我们开始下一组需求。

### [](#supporting-the-clientidle-and-clientmedia-conditions)Supporting the client:idle and client:media conditions  
支持client：idle和client：media条件

We have a pretty robust solution within the `hydrate` method. So, to support more loading conditions, we have to flesh out the other condition promises.  
我们在 `hydrate` 方法中有一个非常强大的解决方案。因此，为了支持更多的加载条件，我们必须充实其他条件承诺。

#### [](#waitforidle)waitForIdle 等待空闲

Take a pause and consider how we should do this. For example, what heuristic do we rely on the determine when the browser is “idle”?  
暂停一下，考虑一下我们应该如何做到这一点。例如，我们依靠什么启发式来确定浏览器何时“空闲”？

It begs the question, what’s “idle” in this case?  
这就引出了一个问题，在这种情况下，什么是“闲置”？

Well, for our implementation, the definition of idle is when the browser is not actively loading any resources, and no latency-critical events, such as animation and input responses, are in progress.  
对于我们的实现，空闲的定义是浏览器没有主动加载任何资源，并且没有延迟关键事件（如动画和输入响应）正在进行中。

To achieve this, we will rely on two properties (i) The `document.readyState` event [11](#user-content-fn-11-55f92bec3c7101b92f5c57e1d82ed429)  
为了实现这一点，我们将依赖于两个属性（i） `document.readyState` 事件 [11](#user-content-fn-11-55f92bec3c7101b92f5c57e1d82ed429)

If the value of this event is `complete`, the document and all sub-resources have finished loading. This includes all dependent resources such as stylesheets, scripts, iframes, and images.  
如果此事件的值为 `complete` ，则文档和所有子资源都已完成加载。这包括所有依赖的资源，如样式表、脚本、iframe和图像。

Listening to this event ensures we hydrate the island when all other essential assets have been downloaded.  
收听此事件确保我们在所有其他重要资产都已下载时为岛补水。

(ii) The `window.requestIdleCallback()` method [12](#user-content-fn-12-55f92bec3c7101b92f5c57e1d82ed429)  
(ii) `window.requestIdleCallback()` 方法 [12](#user-content-fn-12-55f92bec3c7101b92f5c57e1d82ed429)

By definition, the `window.requestIdleCallback()` method will queue a function to be called when a browser is idle. This ensures the function is only executed when the browser handles no latency-critical event.  
根据定义，当浏览器空闲时， `window.requestIdleCallback()` 方法将调用一个函数排队。这可确保仅在浏览器未处理延迟关键事件时执行该函数。

Let’s put these together and create a promise that resolves when the `document.readyState` event is `complete`, and no latency-critical events are being handled.  
让我们把这些组合在一起，创建一个promise，当 `document.readyState` 事件是 `complete` 时，并且没有处理延迟关键事件。

Here’s the implementation below:  
下面是实现：

// 📂 mini-island.js
// ...
class Conditions {
  // ...
  static waitForIdle() {
    const onLoad \= new Promise((resolve) \=> {
      /\*\*
       \* The document.readyState property
       \* describes the loading state of the document.
       \*/
      if (document.readyState !== "complete") {
        /\*\*
         \* Set up an event listener for the "load" event.
         \* The load event is fired when the whole page
         \* has loaded, including all dependent resources
         \* such as stylesheets, scripts, iframes, and
         \* images.
         \*/
        window.addEventListener(
          "load",
          () \=> {
            /\*\*
             \* resolve this promise once the "load" event is fired.
             \*/
            resolve();
          },
          /\*\*
           \* Remove the listener after the first
           \* invocation of the "load" event.
           \*/
          { once: true }
        );
      } else {
        resolve();
      }
    });

    /\*\*
     \* The window.requestIdleCallback() method queues a
     \* function to be called during a browser's idle periods.
     \* This enables developers to perform background
     \* and low-priority work on the main event loop
     \*/

    const onIdle \= new Promise((resolve) \=> {
      /\*\*
       \* Check for "requestIdleCallback" support
       \*/
      if ("requestIdleCallback" in window) {
        requestIdleCallback(() \=> {
          /\*\*
           \* pass the promise resolve function
           \* as the operation to be queued
           \*/
          resolve();
        });
      } else {
        /\*\*
         \* resolve the promise immediately
         \* if requestIdleCallback isn't supported
         \*/
        resolve();
      }
    });

    /\*\*
     \* waitForIdle will wait for both
     \* promises to be resolved, i.e., onIdle and onLoad
     \*/
    return Promise.all(\[onIdle, onLoad\]);
  }
}

Now, go to the `initial.html` demo file and update the file as shown below:  
现在，转到 `initial.html` demo文件并更新文件，如下所示：

<!-- 📂 demos/initial.html -->
<!DOCTYPE html\>
<html lang\="en"\>
  <!-- ... -->
  <!-- content unchanged -->
  <body\>
    <h1\>Initial island demo</h1\>
    <img
      src\="https://raw.githubusercontent.com/ohansemmanuel/larder/main/large\_image.jpeg"
      alt\="34MB large satellite image from Effigis."
    />

    <mini-island client:idle\>
      <p\>Hello island</p\>

      <template data-island\>
        <script type\="module"\>
          console.warn("THIS IS A WARNING FROM AN ISLAND");
        </script\>
      </template\>
    </mini-island\>
  </body\>
</html\>

Note that we’ve introduced a large `34MB` image from [Effigis](https://effigis.com/en/solutions/satellite-images/satellite-image-samples/) and passed a `client:idle` attribute to `<mini-island>`.  
请注意，我们从Efigis引入了一个大的 `34MB` 映像，并将 `client:idle` 属性传递给 `<mini-island>` 。

> Consider downloading the large image and referencing it locally instead of hitting the GitHub servers repeatedly.  
> 考虑下载大映像并在本地引用它，而不是反复访问GitHub服务器。

The large image will keep the browser busy for some time. Before testing this in the browser, I suggest disabling the browser cache via developer tools.  
大图像将使浏览器忙碌一段时间。在浏览器中测试之前，我建议通过开发者工具禁用浏览器缓存。

[![The disable cache property in Firefox.](/understanding-astro/understanding-astro-book/raw/master/images/ch3/CleanShot%202023-05-15%20at%2011.43.31.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch3/CleanShot%202023-05-15%20at%2011.43.31.png)

_The disable cache property in Firefox.  
Firefox中的disable cache属性。_  
  
  

Open the page in the browser and notice how the script is not invoked until the browser has finished loading the large image and is in an idle state.  
在浏览器中打开页面，注意在浏览器完成加载大图像并处于空闲状态之前，脚本是如何被调用的。

This is great! 太棒了！

Instead of potentially allowing non-priority Javascript code to compete for the browser resources, we’ve shelved that to be initialised later during the browser’s idle period.  
我们没有允许非优先级JavaScript代码竞争浏览器资源，而是搁置了在浏览器空闲期间进行初始化。

#### [](#waitformedia)waitForMedia waitForMedia

The media condition is fascinating. The island is only hydrated when a CSS media query is met. This is useful for mobile toggles or other elements only visible on specific screen sizes.  
媒体条件很迷人。只有当满足CSS媒体查询时，岛才水合。这对于移动的切换或仅在特定屏幕尺寸上可见的其他元素很有用。

We will leverage the `window.matchMedia()` to determine if the document matches the media query string.  
我们将利用 `window.matchMedia()` 来确定文档是否匹配媒体查询字符串。

Here’s the annotated implementation:  
下面是带注释的实现：

// 📂 mini-island.js
// ...
class Conditions {
  /\*\*
   \*
   \* @param {\*} query - the query string
   \* passed to the client:media attribute
   \* @returns Promise that resolves when
   \* the document matches the passed CSS media query
   \*/
  static waitForMedia(query) {
    /\*\*
     \* window.matchMedia(query) returns A MediaQueryList object.
     \* This object stores information on a media query
     \* applied to a document and one of the properties
     \* on this object is "matches" - a boolean for
     \* whether the document matches the media query or not.
     \* Create a new simple object of similar form, i.e.,
     \* with a "matches" property
     \*/
    let queryList \= {
      matches: true,
    };

    if (query && "matchMedia" in window) {
      /\*\* 
       Override our stub with the actual query list
     \*/
      queryList \= window.matchMedia(query);
    }

    /\*\*
     \* If matchMedia isn't supported or the
     \* query is truthy, return immediately
     \* e.g., truthy if matchMedia isn't in the window object
     \*/
    if (queryList.matches) {
      return;
    }

    return new Promise((resolve) \=> {
      /\*\*
       \* Set a new listener on the queryList object
       \* and resolve the promise when there's a match
       \*/
      queryList.addListener((e) \=> {
        if (e.matches) {
          resolve();
        }
      });
    });
  }
}

With this in place, we may update the `initial.html` demo file to the following:  
有了这一点，我们可以将 `initial.html` 演示文件更新为以下内容：

<!DOCTYPE html\>
<html lang\="en"\>
  <!-- content remains the same -->
  <body\>
    <h1\>Initial island demo</h1\>

    <mini-island client:media\="(max-width: 400px)"\>
      <p\>Hello island</p\>

      <template data-island\>
        <script type\="module"\>
          console.warn("THIS IS A WARNING FROM AN ISLAND");
        </script\>
      </template\>
    </mini-island\>
  </body\>
</html\>

Now refresh the page in your browser and notice how the script is never initialised until you resize your browser window to match the css query, i.e., a maximum width of `400px`.  
现在在浏览器中刷新页面，注意脚本是如何直到您调整浏览器窗口的大小以匹配css查询，即最大宽度为 `400px` 。

### [](#supporting-frameworks-vue-petite-vue-and-preact)Supporting frameworks: Vue, Petite-vue and Preact  
支持框架：Vue、Petite-Vue和Preact

Our `<mini-island>` implementation is simple yet effective. However, you may not appreciate it until you’ve seen it used with other frameworks. Coincidentally, this is also a part of our objectives, i.e., to develop a framework-agnostic solution.  
我们的 `<mini-island>` 实现简单而有效。然而，在看到它与其他框架一起使用之前，您可能不会欣赏它。巧合的是，这也是我们目标的一部分，即，来开发一个框架不可知的解决方案。

The following sections show framework examples utilising `<mini-island>`. To do this, we will build out the same framework user interface in the form of a simple counter.  
下面的部分展示了使用 `<mini-island>` 的框架示例。为此，我们将以简单计数器的形式构建相同的框架用户界面。

#### [](#vue)Vue 维

Vue is a Javascript framework for building user interfaces. Vue’s mental model builds on top of standard HTML, CSS and Javascript, making it easy to understand for most people.  
Vue是用于构建用户界面的JavaScript框架。Vue的心智模型建立在标准HTML、CSS和JavaScript之上，使得大多数人都很容易理解。

As expected of a modern UI framework, Vue is declarative and reactive.  
正如现代UI框架所期望的那样，Vue是声明式和响应式的。

Let’s go ahead and build a counter application leveraging Vue and `<mini-island>` as shown below:  
让我们继续构建一个利用Vue和 `<mini-island>` 的计数器应用程序，如下所示：

<!-- 📂 demos/vue.html -->

<!DOCTYPE html\>
<html lang\="en"\>
  <head\>
    <meta charset\="UTF-8" />
    <meta http-equiv\="X-UA-Compatible" content\="IE=edge" />
    <meta name\="viewport" content\="width=device-width, initial-scale=1.0" />
    <title\>Vue mini-island demo</title\>

    <script type\="module"\>
      import "../mini-island.js";
    </script\>
  </head\>
  <body\>
    <h1\>Vue</h1\>
    <mark\>This is a vue counter </mark\>

    <p\>
      By default, this button does not load any Javascript and isn't hydrated.
    </p\>

    <p\>
      Resize your browser to match the media query:
      <code\>(max-width: 400px)</code\> to hydrate the island
    </p\>

    <mini-island client:media\="(max-width: 400px)"\>
      <div id\="vue-app"\>
        <button @click\="count++"\>
          <span\>⬆️</span\>

          <div\>
            <strong\>Vue</strong\>
            <div\>
              <span v-html\="count"\>0</span\>
              <span\>\-</span\>
              <span\>clicks</span\>
            </div\>
          </div\>
        </button\>
      </div\>

      <template data-island\>
        <script type\="module"\>
          import { createApp } from "https://unpkg.com/vue@3.2.36/dist/vue.esm-browser.prod.js";

          createApp({
            data: () \=> ({ count: 0 }),
          }).mount("#vue-app");
        </script\>
      </template\>
    </mini-island\>
  </body\>
</html\>

It’s okay if you do not understand the Vue code snippets. What’s important is the following:  
如果你不理解Vue代码片段也没关系。重要的是以下几点：

*   The HTML markup is rendered as soon as the HTML page is loaded and parsed.  
    HTML标记在加载和解析HTML页面后立即呈现。
    
*   This includes the static counter markup within `mini-island`, i.e.,  
    这包括 `mini-island` 内的静态计数器标记，即
    
    <div id\="vue-app"\>
      <button @click\="count++"\>
        <span\>⬆️</span\>
    
        <div\>
          <strong\>Vue</strong\>
          <div\>
            <span v-html\="count"\>0</span\>
            <span\>\-</span\>
            <span\>clicks</span\>
          </div\>
        </div\>
      </button\>
    </div\>
    
*   However, the counter is not hydrated at this point. So, clicking the counter will not increase the count. This is because Vue hasn’t been loaded, and the counter button is not yet hydrated.  
    然而，计数器在这一点上没有水合。因此，单击计数器不会增加计数。这是因为Vue尚未加载，计数器按钮尚未水合。
    
*   Consider the loading condition set on the island, i.e., `client:media="(max-width: 400px)"`.  
    考虑岛上设置的加载条件，即，#0号。
    
*   Now, resize your browser (use the developer tools) to a width less than `400px` to hydrate the island.  
    现在，调整浏览器的大小（使用开发工具），使其宽度小于 `400px` ，以使岛屿水合。
    
*   This will import Vue and hydrate the counter. Here’s the code responsible for within the island `template`:  
    这将导入Vue并水合计数器。这里是负责岛内 `template` 的代码：
    
    <template data-island\>
      <script type\="module"\>
        import { createApp } from "https://unpkg.com/vue@3.2.36/dist/vue.esm-browser.prod.js";
    
        createApp({
          data: () \=> ({ count: 0 }),
        }).mount("#vue-app");
      </script\>
    </template\>
    
*   The counter should now be hydrated; we may now click to our heart’s content.  
    柜台现在应该是水化的;我们现在可以尽情点击了
    

#### [](#petite-vue)Petite-vue 小视图

From the official Vue [documentation](https://vuejs.org/guide/extras/ways-of-using-vue.html#standalone-script), Vue also provides an alternative distribution called petite-vue that is optimised for progressively enhancing existing HTML.  
从官方Vue文档中，Vue还提供了一个名为petite-vue的替代发行版，该发行版针对逐步增强现有HTML进行了优化。

This is perfect for our use case.  
这非常适合我们的用例。

Let’s go ahead and create a similar demo using `petite-vue` as shown below:  
让我们继续使用 `petite-vue` 创建一个类似的演示，如下所示：

<!-- 📂 demos/petite-vue.html -->

<!DOCTYPE html\>
<html lang\="en"\>
  <head\>
    <meta charset\="UTF-8" />
    <meta http-equiv\="X-UA-Compatible" content\="IE=edge" />
    <meta name\="viewport" content\="width=device-width, initial-scale=1.0" />
    <title\>Vue mini-island demo</title\>

    <script type\="module"\>
      import "../mini-island.js";
    </script\>
  </head\>
  <body\>
    <h1\>Petite-vue</h1\>
    <mark\>This is a petite-vue counter </mark\>

    <p\>
      By default, this button does not load any Javascript and isn't hydrated.
    </p\>

    <p\>
      Resize your browser to match the media query:
      <code\>(max-width: 400px)</code\> to hydrate the island
    </p\>

    <mini-island client:media\="(max-width: 400px)"\>
      <div id\="vue-app" v-scope\="{ count: 0 }"\>
        <button @click\="count++"\>
          <span\>⬆️</span\>

          <div\>
            <strong\>Petite-vue</strong\>
            <div\>
              <span v-html\="count"\>0</span\>
              <span\>\-</span\>
              <span\>clicks</span\>
            </div\>
          </div\>
        </button\>
      </div\>

      <template data-island\>
        <script type\="module"\>
          import { createApp } from "https://unpkg.com/petite-vue@0.4.1/dist/petite-vue.es.js";

          createApp().mount("#vue-app");
        </script\>
      </template\>
    </mini-island\>
  </body\>
</html\>

Apart from a few changes, the code above is identical to the standard Vue API. Here’s how this works:  
除了一些改动外，上面的代码与标准Vue API完全相同。这是如何工作的：

*   The HTML markup is rendered as soon as the HTML page is loaded and parsed.  
    HTML标记在加载和解析HTML页面后立即呈现。
    
*   This includes the static counter markup within `mini-island`, i.e.,  
    这包括 `mini-island` 内的静态计数器标记，即
    
    <div id\="vue-app" v-scope\="{ count: 0 }"\>
      <button @click\="count++"\>
        <span\>⬆️</span\>
    
        <div\>
          <strong\>Vue</strong\>
          <div\>
            <span v-html\="count"\>0</span\>
            <span\>\-</span\>
            <span\>clicks</span\>
          </div\>
        </div\>
      </button\>
    </div\>
    
*   NB: the significant difference in the code above is the introduction of the `v-scope` attribute to hold our count data variable.  
    注意：上面代码的显著区别是引入了 `v-scope` 属性来保存count数据变量。
    
*   The counter, however, is not hydrated at this point. So, clicking the counter will not increase the count. This is because petite-vue hasn’t been loaded, and the counter button is not yet hydrated.  
    然而，计数器此时未水合。因此，单击计数器不会增加计数。这是因为petite-vue还没有加载，计数器按钮还没有水合。
    
*   Consider the loading condition set on the island, i.e., `client:media="(max-width: 400px)"`  
    考虑岛上设置的加载条件，即， `client:media="(max-width: 400px)"`
    
*   Now, resize your browser (take advantage of the developer tools) to a width less than `400px` to hydrate the island.  
    现在，调整浏览器的大小（利用开发人员工具），使其宽度小于 `400px` ，以使岛屿变得更加湿润。
    
*   This will import Petite-vue and hydrate the counter. Here’s the code responsible for within the island `template`:  
    这将导入Petite-vue并水合计数器。这里是负责岛内 `template` 的代码：
    
    <template data-island\>
      <script type\="module"\>
        import { createApp } from "https://unpkg.com/petite-vue@0.4.1/dist/petite-vue.es.js";
    
        createApp().mount("#vue-app");
      </script\>
    </template\>
    
*   The counter should now be hydrated; we may now click to our heart’s content.  
    柜台现在应该是水化的;我们现在可以尽情点击了
    

#### [](#preact)Preact Preact

Preact is a fast 3kB alternative to React with the same modern API, and it can be used in the browser without any transpiration steps.  
Preact是React的快速3 kB替代品，具有相同的现代API，它可以在浏览器中使用，而无需任何蒸腾步骤。

Let’s go ahead and create a similar demo using Preact, as shown below:  
让我们继续使用Preact创建一个类似的演示，如下所示：

<!-- 📂 demos/preact.html -->

<!DOCTYPE html\>
<html lang\="en"\>
  <head\>
    <meta charset\="UTF-8" />
    <meta http-equiv\="X-UA-Compatible" content\="IE=edge" />
    <meta name\="viewport" content\="width=device-width, initial-scale=1.0" />
    <title\>Preact mini-island demo</title\>

    <script type\="module"\>
      import "../mini-island.js";
    </script\>
  </head\>

  <body\>
    <h1\>Preact</h1\>
    <p\>This is a preact counter</p\>

    <p\>By default, this button is not rendered or hydrated</p\>

    <mini-island client:idle\>
      <div id\="preact-app"\>
        <mark
          \>The counter island will be rendered and hydrated just above this mark
          when the browser is idle</mark
        \>
      </div\>

      <template data-island\>
        <script type\="module"\>
          import { h, Component, render } from "https://esm.sh/preact";
          import { useState } from "https://esm.sh/preact/hooks";
          import htm from "https://esm.sh/htm";

          // Initialize htm with Preact
          const html \= htm.bind(h);

          function App(props) {
            const \[count, setCount\] \= useState(0);

            const increment \= () \=>
              setCount((currentCount) \=> currentCount + 1);

            return html\`<div\>
              <button onClick\=${() \=> increment()}\>
                <span\>⬆️ </span\>
                <div\>
                  <strong\>Preact</strong\>
                  <div\>
                    <span\>${count}</span\>
                    <span\>\-</span\>
                    <span\>clicks</span\>
                  </div\>
                </div\>
              </button\>
            </div\>\`;
          }

          render(html\`<${App} />\`, document.getElementById("preact-app"));
        </script\>
      </template\>
    </mini-island\>

    <ul\>
      <li\>The document must be completely loaded</li\>
      <li\>The large image below must complete loading</li\>
    </ul\>

    <img
      src\="https://raw.githubusercontent.com/ohansemmanuel/larder/main/large\_image.jpeg"
      alt\="34MB large satellite image from Effigis."
    />
  </body\>
</html\>

The code above behaves differently from the previous framework examples.  
上面的代码与前面的框架示例不同。

Here’s how this works:  
这是如何工作的：

*   The HTML markup is rendered after loading and parsing the HTML.  
    HTML标记在加载和解析HTML之后呈现。
*   The counter, however, is not rendered or hydrated. This is because `mini-island` has a `client: idle` loading condition.  
    然而，计数器未被渲染或水合。这是因为 `mini-island` 具有 `client: idle` 加载条件。
*   The counter will be rendered and hydrated when the browser is idle. For this to be the case, the large image in the document must complete loading.  
    当浏览器空闲时，计数器将被渲染和水合。为此，文档中的大图像必须完成加载。
*   Once this is loaded (including other associated document resources), Preact renders and hydrates the counter when the browser is idle.  
    一旦加载了这个文件（包括其他相关的文档资源），Preact会在浏览器空闲时渲染和水合计数器。
*   The counter should now be hydrated; we may now click to our heart’s content.  
    柜台现在应该是水化的;我们现在可以尽情点击了

### [](#conclusion)Conclusion 结论

When it comes to performance and deciding what rendering solution works for your application, no single solution fits all applications. Depending on the application, we always have to make tradeoffs. However, the island architecture provides very performant client applications without sacrificing rich interactivity.  
在性能和决定哪种渲染解决方案适用于您的应用程序时，没有一种解决方案适合所有应用程序。根据应用程序的不同，我们总是需要做出权衡。然而，岛式架构提供了非常高性能的客户端应用程序，而不会牺牲丰富的交互性。

The main goal of this chapter was to peel back the perceived layer of complexity and strip down component islands to a fundamental digestible unit with `<mini-island>`.  
本章的主要目标是剥离感知的复杂性层，并将组件岛剥离为一个基本的可消化的单位，用 `<mini-island>` 。

Now, we will take this knowledge into exploring component islands in Astro, and (almost) nothing will surprise you. That’s the definition of proper understanding!  
现在，我们将利用这些知识探索Astro中的组件岛屿，（几乎）没有什么会让你感到惊讶。这就是正确理解的定义！

Footnotes 页签
------------

1.  There are other rendering techniques in between rendering on the client or server. [↩](#user-content-fnref-1-55f92bec3c7101b92f5c57e1d82ed429)  
    在客户端或服务器上的渲染之间存在其他渲染技术。 ↩
    
2.  Time to first byte refers to the time between navigation to the site and when the first bytes of are received. [↩](#user-content-fnref-2-55f92bec3c7101b92f5c57e1d82ed429)  
    到达第一个字节的时间是指导航到站点和接收到的第一个字节之间的时间。↩
    
3.  The TTI measure the duration it takes for a webpage to achieve complete interactivity. [↩](#user-content-fnref-3-55f92bec3c7101b92f5c57e1d82ed429)  
    TTI测量网页实现完全交互所需的持续时间。 ↩
    
4.  When a browser displays the initial content from the DOM, it is known as the First Contentful Paint (FCP). This is the first indication to the user that the page is loading. [↩](#user-content-fnref-4-55f92bec3c7101b92f5c57e1d82ed429)  
    当浏览器显示DOM中的初始内容时，它被称为第一内容绘制（FCP）。这是向用户表明页面正在加载的第一个指示。 ↩
    
5.  Time to first byte (TTFB): the time from when the user navigates the page to when the first bit of content comes in. [↩](#user-content-fnref-5-55f92bec3c7101b92f5c57e1d82ed429)  
    到第一个字节的时间（TTFB）：从用户导航页面到第一位内容进入的时间。 ↩
    
6.  Web components on MDN: [https://developer.mozilla.org/en-US/docs/Web/API/Web\_components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components) [↩](#user-content-fnref-6-55f92bec3c7101b92f5c57e1d82ed429)  
    MDN上的Web组件：https://developer.mozilla.org/en-US/docs/Web/API/Web\_components第0#页
    
7.  The whole page is loaded when dependent resources such as stylesheets, scripts, iframes, and images have been fetched. [↩](#user-content-fnref-7-55f92bec3c7101b92f5c57e1d82ed429)  
    当获取依赖资源（如样式表、脚本、iframe和图像）时，整个页面将被加载。 ↩
    
8.  Leverage window.requestIdleCallback for idle state: [https://developer.mozilla.org/en-US/docs/Web/API/Window/requestIdleCallback](https://developer.mozilla.org/en-US/docs/Web/API/Window/requestIdleCallback) [↩](#user-content-fnref-8-55f92bec3c7101b92f5c57e1d82ed429)  
    利用window.requestIdleCallback获取空闲状态：https://developer.mozilla.org/en-US/docs/Web/API/Window/requestIdleCallback第0#页
    
9.  querySelectorAll on MDN: [https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll) [↩](#user-content-fnref-9-55f92bec3c7101b92f5c57e1d82ed429)  
    MDN上的querySelectorAll：https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll第0#页
    
10.  The IntersectionObserver API on MDN [https://developer.mozilla.org/en-US/docs/Web/API/Intersection\_Observer\_API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API) [↩](#user-content-fnref-10-55f92bec3c7101b92f5c57e1d82ed429)  
    MDN上的IntersectionObserver API https://developer.mozilla.org/en-US/docs/Web/API/Intersection\_Observer\_API ↩
    
11.  [https://developer.mozilla.org/en-US/docs/Web/API/Document/readyState](https://developer.mozilla.org/en-US/docs/Web/API/Document/readyState "readyState") [↩](#user-content-fnref-11-55f92bec3c7101b92f5c57e1d82ed429)
    
12.  [https://developer.mozilla.org/en-US/docs/Web/API/Window/requestIdleCallback](https://developer.mozilla.org/en-US/docs/Web/API/Window/requestIdleCallback "requestIdleCallback") [↩](#user-content-fnref-12-55f92bec3c7101b92f5c57e1d82ed429)
