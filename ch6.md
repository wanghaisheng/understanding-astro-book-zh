
[](#-understanding-astro)🚀 Understanding Astro  
🚀 了解Astro
============================================================

By [Ohans Emmanuel](https://www.ohansemmanuel.com/) 作者：Ohans Emmanuel

  

[](#chapter-6-server-side-rendering-ssr-in-astro)Chapter 6: Server-side Rendering (SSR) in Astro  
第6章Astro中的服务器端渲染（SSR）
------------------------------------------------------------------------------------------------------------------------

This chapter will guide you on enabling SSR in an Astro project, and we will also discuss a detailed overview of the extensive features a server-side rendered Astro project offers.  
本章将指导您在Astro项目中启用SSR，我们还将详细讨论服务器端渲染Astro项目提供的广泛功能的概述。

  
  
  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch1/watch-instead@3x.png)](https://ohans.me/understanding-astro-udemy)

  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch1/view-project.png)](https://github.com/understanding-astro/ssr)

  
  

[](#what-youll-learn)What you’ll learn 您将学到的内容
----------------------------------------------

*   Understand how to enable SSR in an Astro project.  
    了解如何在Astro项目中启用SSR。
*   Leverage environment variables to store secrets.  
    利用环境变量存储秘密。
*   Provide flexible server routing via dynamic routes.  
    通过动态路由提供灵活的服务器路由。
*   Understand the request-response cycle and its relevant properties.  
    理解请求-响应周期及其相关属性。
*   Take advantage of Astro API routes to power robust applications.  
    利用Astro API路由为强大的应用程序提供支持。

[](#when-do-you-need-ssr)When do you need SSR?  
什么时候需要SSR？
-----------------------------------------------------------

In an earlier chapter, we discussed several rendering techniques for a frontend application. The reason was so we could make effective decisions for when to choose one rendering technique over the other.  
在前面的章节中，我们讨论了前端应用程序的几种渲染技术。原因是我们可以有效地决定何时选择一种渲染技术。

I'll briefly summarise why we may need SR in an Astro project. Remember that your mileage may differ - so always refer to the basics discussed in Chapter 3: Build Your Own Component Island.  
我将简要地总结为什么我们可能需要在Astro项目SR。请记住，您的里程可能会有所不同-因此请始终参考第3章中讨论的基础知识：构建自己的组件岛。

Now, the following are pointers to when we may need to enable SSR in an Astro project:  
现在，以下是我们可能需要在Astro项目中启用SSR的指针：

*   **Content that is subject to frequent changes.**: We may need SSR if a page’s content frequently changes, rather than using a statically built page which would require a rebuild for every new change.  
    经常更改的内容。：如果页面的内容频繁更改，我们可能需要SSR，而不是使用静态构建的页面，因为静态构建的页面需要为每个新的更改重新构建。
*   **Thee need for API endpoints**: SSR allows us to create API endpoints while keeping sensitive data hidden from clients. We’ll see how to do this later in the chapter.  
    API端点的需求：SSR允许我们创建API端点，同时对客户端隐藏敏感数据。我们将在本章后面看到如何做到这一点。
*   **Creating pages with restricted access**: To limit access to a page, enable server rendering for server-side handling of user privileges.  
    创建访问受限的页面：若要限制对页的访问，请启用服务器呈现以在服务器端处理用户权限。

[](#how-to-enable-ssr)How to Enable SSR  
如何启用SSR
-------------------------------------------------

Okay, here’s how it all begins. To enable SSR in an Astro project, set the `output` configuration option to `server` in the `astro.config.mjs` file.  
好吧，事情是这样开始的。要在Astro项目中启用SSR，请在 `astro.config.mjs` 文件中将 `output` 配置选项设置为 `server` 。

// 📂 astro.config.mjs

import { defineConfig } from "astro/config";

export default defineConfig({
  //This will enable SSR
  output: "server",
});

And that’s it! 就是这样！

Let’s see this in action by starting a new project with the following command:  
让我们通过使用以下命令启动一个新项目来看看这一点：

npm create astro@latest \--  \--template\=minimal \--yes \--skip\-houston ssr

This will use the `minimal` template, `--skip-houston` will skip the Houston animation, and the `--yes` option will skip all prompts and accept the defaults.  
这将使用 `minimal` 模板， `--skip-houston` 将跳过Houston动画，而 `--yes` 选项将跳过所有提示并接受默认值。

Now, change directories into `ssr` and start the project:  
现在，将目录更改为 `ssr` 并启动项目：

cd ssr && npm start

The app should run on a local server with a single `index.astro` page.  
应用程序应该在本地服务器上运行，只有一个 `index.astro` 页面。

If we build the application for production via `npm build`, we should have the single `index.astro` page pre-rendered, i.e., statically built.  
如果我们通过 `npm build` 构建应用程序用于生产，我们应该预先呈现单个 `index.astro` 页面，即，静态构建。

[![Statically rendering the index.astro page.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-22%20at%2007.13.56.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-22%20at%2007.13.56.png)

_Statically rendering the index.astro page.  
静态呈现index.astro页面。_  
  
  

To re-iterate, a pre-rendered application is essentially a static site, i.e., not server-side rendered.  
为了重新迭代，预渲染的应用程序本质上是静态站点，即，而不是服务器端呈现的。

To initiate server-side rendering, let’s change the configuration to include the `output` property as shown below:  
要启动服务器端渲染，让我们更改配置以包含 `output` 属性，如下所示：

// 📂 src/astro.config.mjs
import { defineConfig } from "astro/config";

// https://astro.build/config
export default defineConfig({
  output: "server",
});

If we rerun the production build, we will have an error in the console.  
如果我们重新运行生产构建，我们将在控制台中看到一个错误。

    [error] Cannot use `output: 'server'` without an adapter. Please install and configure the appropriate server adapter for your final deployment.
    

[](#deploying-an-ssr-project)Deploying an SSR project  
部署SSR项目
---------------------------------------------------------------

The root cause of the error above is that to build your application for server-side rendering; the Astro build command must know what server you’ll eventually be deploying to.  
上述错误的根本原因是，要为服务器端呈现构建应用程序; Astrobuild命令必须知道您最终将部署到哪个服务器。

SSR requires a server runtime, i.e., the code running within the server that renders our Astro pages. To achieve this, Astro provides adapters that match our deployment runtime.  
SSR需要服务器运行时，即，在服务器中运行的代码呈现我们的Astro页面。为了实现这一点，Astro提供了与我们的部署运行时相匹配的适配器。

An adapter allows Astro to do two things. First, determine the server runtime environment. Second, output a script that runs the SSR code on the specified runtime.  
适配器允许Astro做两件事。首先，确定服务器运行时环境。其次，输出一个脚本，该脚本在指定的运行时上运行SSR代码。

[![The Astro adapter needs..](/understanding-astro/understanding-astro-book/raw/master/images/ch6/astro_adapter_needs.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/astro_adapter_needs.png)

_The Astro adapter needs..  
Astro适配器需要。_  
  
  

At the time of writing, the available Astro adapters are Cloudfare, Deno, Netlify, NodeJS and Vercel.  
在撰写本文时，可用的Astro适配器是Cloudfare，Deno，Netlify，NodeJS和Vercel。

We may deploy our SSR project to any of these runtimes with natively supported adapters.  
我们可以使用本机支持的适配器将SSR项目部署到这些运行时中的任何一个。

To install any of these adapters, use the command:  
要安装任何这些适配器，请使用以下命令：

npx astro add \[name-of-adapter\]

`[name-of-adapter]` could be `cloudfare`, `deno`, `netlify`, `node` or `vercel`.  
`[name-of-adapter]` 可以是 `cloudfare` 、 `deno` 、 `netlify` 、 `node` 或 `vercel` 。

I recommend looking at the [official reference](https://docs.astro.build/en/guides/deploy/) for any adapters you need in your project, as it would be unreasonable to cover all of these in the book. However, we will stick to `netlify` moving on.  
我建议您查看项目中需要的任何适配器的官方参考，因为在书中涵盖所有这些适配器是不合理的。但是，我们将坚持 `netlify` 继续前进。

To add the `netlify` adapter, go ahead and enter the following command in the terminal:  
要添加 `netlify` 适配器，请继续并在终端中输入以下命令：

npx astro add netlify

This will go ahead and install the adapter and update our configuration file to the following:  
这将继续安装适配器并将我们的配置文件更新为以下内容：

import { defineConfig } from "astro/config";
// 👀 look here
import netlify from "@astrojs/netlify/functions";

// https://astro.build/config
export default defineConfig({
  output: "server",
  // 👀 look here
  adapter: netlify(),
});

Essentially, the adapter is imported in the second line of the config and added to the `adapter` property.  
实际上，适配器是在配置的第二行中导入的，并添加到 `adapter` 属性中。

Now re-run the build command:  
现在重新运行build命令：

npm run build

This will successfully build our SSR project for production by outputting `netlify` specific code snippets in the `dist` and `.netlify` directory.  
这将通过在 `dist` 和 `.netlify` 目录中输出 `netlify` 特定的代码片段来成功构建我们的SSR项目以供生产。

Now, we’re in business 🚀  
我们在做生意？？

[](#use-the-correct-adapter)Use the correct adapter  
使用正确的适配器
--------------------------------------------------------------

It goes without saying that after adding an adapter, the project should be deployed to the specified adapter, `netlify`, and not some other provider, e.g., `vercel`.  
毫无疑问，在添加适配器之后，项目应该部署到指定的适配器 `netlify` ，而不是其他提供者，例如，#1。

Use the correct adapter for your deployment runtime.  
为部署运行时使用正确的适配器。

[![Deploying a Vercel adapter to Netlify is wrong.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/adapter_deploy.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/adapter_deploy.png)

_Deploying a Vercel adapter to Netlify is wrong.  
将Vercel适配器部署到Netlify错误。_  
  
  

Our actual deployment steps will vary depending on the server runtime being deployed. For example, for Netlify, we may follow the steps described in the deploy a static site in Chapter 1. These steps will be identical for similar runtimes like Vercel.  
我们实际的部署步骤将根据所部署的服务器运行时而有所不同。例如，对于Netlify，我们可以按照第1章中部署静态站点中描述的步骤进行操作。这些步骤对于类似的运行时（如Vercel）是相同的。

For other runtimes, the official Astro [deployment guides](https://docs.astro.build/en/guides/deploy/) do an excellent job of explaining the deployment steps required.  
对于其他运行时，官方的Astro部署指南在解释所需的部署步骤方面做得很好。

[](#ssr-with-static-pages)SSR with static pages  
带有静态页面的SSR
------------------------------------------------------------

With the `output` configuration property set to `server`, every page in our Astro project will be server-side rendered. However, there’s a great chance we may want one or more pages to be statically generated at build time, i.e., some pages server-side rendered and others pre-rendered.  
将 `output` 配置属性设置为 `server` ，Astro项目中的每个页面都将在服务器端呈现。但是，我们很可能希望在构建时静态生成一个或多个页面，即，一些页面是服务器端呈现的，而其他页面是预呈现的。

[![Having a mix of server and statically rendered pages.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/hybrid_rendering.png width)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/hybrid_rendering.png width)

_Having a mix of server and statically rendered pages.  
混合了服务器和静态呈现的页面。_  
  
  

In such cases, we can opt-in to pre-rendering by adding `export const prerender = true` to any page that supports exporting variables, e.g., `.astro`, `.mdx` `, .ts` and `.js`.  
在这种情况下，我们可以通过将 `export const prerender = true` 添加到任何支持导出变量的页面来选择加入预渲染，例如， `.astro` 、 `.mdx` 、 `, .ts` 和 `.js` 。

Let’s try this out by creating a new `about.astro` page with the following content:  
让我们尝试创建一个新的 `about.astro` 页面，内容如下：

// 📂 src/pages/about.astro

\--\-
// 👀 note the prerender export
export const prerender \= true;
\--\-

<html lang\="en"\>
  <head\>
    <meta charset\="utf-8" /\>
    <link rel\="icon" type\="image/svg+xml" href\="/favicon.svg" /\>
    <meta name\="viewport" content\="width=device-width" /\>
    <meta name\="generator" content\={Astro.generator} /\>
    <title\>Astro</title\>
  </head\>
  <body\>
    <h1\>About us</h1\>
  </body\>
</html\>

With the `prerender` export, the `about` page will be statically rendered at build time, while the `index` page remains server-side rendered.  
使用 `prerender` 导出， `about` 页面将在构建时静态呈现，而 `index` 页面保持服务器端呈现。

Run `npm run build` to see this in action.  
运行 `npm run build` 以查看此操作。

[![Static and server-side generated pages in the same project.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-22%20at%2008.33.08.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-22%20at%2008.33.08.png)

_Static and server-side generated pages in the same project.  
同一项目中的静态页和服务器端生成的页。_  
  
  

[](#from-request-to-response)From Request to Response  
从请求到响应
--------------------------------------------------------------

The interaction between a client and server may be simplified in two steps:  
客户端和服务器之间的交互可以简化为两个步骤：

*   the client makes a **request**.  
    客户端发出请求。
*   the server sends a **response**.  
    服务器发送响应。

The two main entities in this simplified interaction are the client request and the server response. Luckily, with server-side rendering, we may access details of the request and response object.  
这个简化的交互中的两个主要实体是客户端请求和服务器响应。幸运的是，通过服务器端呈现，我们可以访问请求和响应对象的详细信息。

### [](#the-request-object)The Request object Request对象

The `request` object may be accessed on the `Astro` global as shown below:  
可以在 `Astro` 全局上访问 `request` 对象，如下所示：

\--\-
 const request \= Astro.request
\--\-

The object holds Information about the current request and is represented by the standard [Request](https://developer.mozilla.org/en-US/docs/Web/API/Request) interface of the fetch API.  
该对象保存有关当前请求的信息，并由fetch API的标准Request接口表示。

interface Request extends Body {
    readonly cache: RequestCache
    readonly credentials: RequestCredentials;
    readonly destination: RequestDestination;
    readonly headers: Headers;
    readonly integrity: string;
    readonly keepalive: boolean;
    readonly method: string;
    readonly mode: RequestMode;
    readonly redirect: RequestRedirect;
    readonly referrer: string;
    readonly referrerPolicy: ReferrerPolicy;
    readonly signal: AbortSignal;
    readonly url: string;
    clone(): Request;
}

For example, we may access the request headers via `Astro.request.headers` and the current request URL as a string via `Astro.request.url`.  
例如，我们可以通过 `Astro.request.headers` 访问请求头，通过 `Astro.request.url` 访问当前请求URL作为字符串。

### [](#the-response-object)The Response object Response对象

The `Response` object is the corresponding interface representing the response to a request. This is also represented by the standard [Response](https://developer.mozilla.org/en-US/docs/Web/API/Response) interface of the Fetch API.  
`Response` 对象是表示对请求的响应的对应接口。这也由Fetch API的标准Response接口表示。

As opposed to accessing the object on the `Astro` object, the `Response` object is created using the `Response()` constructor.  
与访问 `Astro` 对象上的对象相反， `Response` 对象是使用 `Response()` 构造函数创建的。

The `Response()` constructor has the following signature:  
`Response()` 构造函数具有以下签名：

new Response(body, options);

Where `body` defines the body for the response and `options` is an object containing custom settings to apply to the response, i.e., `status`, `statusText` and `headers`.  
其中 `body` 定义响应的主体， `options` 是包含应用于响应的自定义设置的对象，即， `status` 、 `statusText` 和 `headers` 。

For example, we could update our `index` page to return a new response if we were presumably in beta - represented by a simple variable.  
例如，我们可以更新我们的 `index` 页面，以返回一个新的响应，如果我们可能处于测试阶段-由一个简单的变量表示。

\--\-
const isBeta \= true;

if (isBeta) {
  return new Response("app not available - check back", {
    status: 200,
    statusText: "OK!",
  });
}
\--\-

<html lang\="en"\>
  <head\>
    <meta charset\="utf-8" /\>
    <link rel\="icon" type\="image/svg+xml" href\="/favicon.svg" /\>
    <meta name\="viewport" content\="width=device-width" /\>
    <meta name\="generator" content\={Astro.generator} /\>
    <title\>Astro</title\>
  </head\>
  <body\>
    <h1\>We're live!</h1\>
  </body\>
</html\>

Instead of returning the `HTML` page, we should now have a simple text response sent to the client.  
我们现在应该向客户端发送一个简单的文本响应，而不是返回 `HTML` 页面。

[![Returning a simple text response to the client.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-22%20at%2010.43.19.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-22%20at%2010.43.19.png)

_Returning a simple text response to the client.  
向客户端返回一个简单的文本响应。_  
  
  

There’s also a `response` object on the `Astro` global. Blimey! However, It’s important to note that this is not the same as the `Response` object constructor. So, rewriting our example to use `Astro.response` will fail.  
在 `Astro` 全局变量上还有一个 `response` 对象。哎呀！然而，重要的是要注意，这与 `Response` 对象构造函数不同。因此，重写我们的示例以使用 `Astro.response` 将失败。

\--\-
const isBeta \= true;

if (isBeta) {
  // ❌ This is wrong and will fail
  return new Astro.response("app not available - check back", {
    status: 200,
    statusText: "Excellent!",
  });
}
\--\-

[![Error: Astro.response is not a constructor.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-22%20at%2011.28.52.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-22%20at%2011.28.52.png)

_Error: Astro.response is not a constructor.  
错误：Astro.response不是构造函数。_  
  
  

This is because `Astro.response` represents the response object initialiser. It’s used to set the `options` on the server response, i.e., `status`, `statusText` and `headers`.  
这是因为 `Astro.response` 表示响应对象初始化器。用于设置服务器响应上的 `options` ，即： `status` 、 `statusText` 和 `headers` 。

For example, to set a custom header on the server response, we could do the following:  
例如，要在服务器响应上设置自定义头，我们可以执行以下操作：

// 📂 src/pages/index.astro
\--\-
Astro.response.headers.set("beta\_id", "some\_header\_value");
\--\-

<html lang\="en"\>
  <head\>
    <meta charset\="utf-8" /\>
    <link rel\="icon" type\="image/svg+xml" href\="/favicon.svg" /\>
    <meta name\="viewport" content\="width=device-width" /\>
    <meta name\="generator" content\={Astro.generator} /\>
    <title\>Astro</title\>
  </head\>
  <body\>
    <h1\>We're live!</h1\>
  </body\>
</html\>

The server will return the `HTML` page and our custom `beta_id` header.  
服务器将返回 `HTML` 页面和我们自定义的 `beta_id` 头。

[![Setting a custom header on the server response.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-22%20at%2011.31.50.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-22%20at%2011.31.50.png)

_Setting a custom header on the server response.  
在服务器响应上设置自定义标头。_  
  
  

### [](#redirect-response)Redirect response 重定向响应

It is pretty common to receive a client request and perform a redirect on the server.  
接收客户端请求并在服务器上执行重定向是很常见的。

There are two ways to achieve this in Astro.  
在Astro中有两种方法可以实现这一点。

The first is to leverage the standard `Response` object via `Response.redirect`.  
第一种是通过 `Response.redirect` 利用标准的 `Response` 对象。

Consider a case where we want to redirect a user to another page if they are not logged in, as shown below:  
考虑这样一种情况，如果用户没有登录，我们希望将其重定向到另一个页面，如下所示：

{/\*\* 📂 src/index.astro \*\*/}
\--\-
const getIsLoggedOut \= () \=> true;
const isLoggedOut \= getIsLoggedOut();

if (isLoggedOut) {
  return Response.redirect(\`${Astro.request.url}about\`, 307);
}
\--\-

In this example, we call `Response.redirect` while passing it a redirect URL and a status code, i.e.:  
在这个例子中，我们调用 `Response.redirect` ，同时向它传递一个重定向URL和一个状态码，即：

Response.redirect(URL, status);

It’s important to note that the `URL` in this case is an absolute path. Hence constructing from `Astro.request.url` that points to the absolute base path, e.g., `http://localhost:3001/`.  
值得注意的是，在这种情况下， `URL` 是一个绝对路径。因此，从指向绝对基路径的 `Astro.request.url` 构造，例如， `http://localhost:3001/` 。

When logged out, the user will be redirected to the `about` page and the optional status code `307` indicates a temporary redirect.  
注销时，用户将被重定向到 `about` 页面，可选状态代码 `307` 表示临时重定向。

As we’ve seen above, constructing the absolute URL could get unnecessarily complex. Luckily, there’s an alternative way to perform a redirect.  
正如我们在上面看到的，构造绝对URL可能会变得不必要的复杂。幸运的是，还有一种执行重定向的替代方法。

We may also leverage the `Astro.redirect` method to redirect to another page. For example, we could rewrite our solution to use `Astro.redirect` as shown below:  
我们也可以利用 `Astro.redirect` 方法重定向到另一个页面。例如，我们可以重写我们的解决方案，使用 `Astro.redirect` ，如下所示：

\--\-
const getIsLoggedOut \= () \=> true;
const isLoggedOut \= getIsLoggedOut();

if (isLoggedOut) {
  return Astro.redirect("/about", 307);
}
\--\-

We have a much simpler API here. We can redirect by just passing the relative path to redirect to. The status code is also optional here.  
我们这里有一个更简单的API。我们可以通过传递要重定向到的相对路径来重定向。在此状态代码也是可选的。

> It’s important to note that redirects should be done in page components, I.e., not inside other components, e.g., layouts or base components.  
> 重要的是要注意重定向应该在页面组件中完成，即，而不是在其他组件内部，例如，布局或基础组件。

### [](#utilities-for-manipulating-cookies)Utilities for manipulating cookies  
用于操作Cookie的实用程序

In SSR mode, we may need to read or manipulate cookies. Well, Astro’s got us covered with `Astro.cookies`. This contains utilities for reading and using cookies in SSR mode.  
在SSR模式下，我们可能需要读取或操作Cookie。好吧，阿童木给我们盖了0#号。这包含用于在SSR模式下阅读和使用cookie的实用程序。

Consider the examples of retrieving a cookie:  
考虑检索Cookie的示例：

//Get an AstroCookie object
const cookieObject \= Astro.cookies.get("coooookiee");

// Get the string value of the cookie
const cookieValue \= cookieObject.value;

// Parse the cookie value via JSON.parse. Returns an object if the cookie is a valid JSON. It throws an error otherwise.

const cookieJSON \= cookieObject.json();

// Parse the cookie value as a Number
const cookieNumber \= cookieObject.number();

// Parse the cookie as a boolean
const cookieBoolean \= cookieObject.boolean();

That’s a lot of flexibility!!  
这是一个很大的灵活性！！

We may also check if a cookie exists with the `has` method, as shown below:  
我们也可以使用 `has` 方法检查cookie是否存在，如下所示：

// check if the "cooooookies" cookie exists. returns a boolean
const hasCookie \= Astro.cookies.has("cooooookies");

It is also possible to set a cookie as shown below:  
也可以设置cookie，如下所示：

// Set a cookie
Astro.cookies.set("cooookiees", "the-cookie-value");

The signature for `Astro.cookies.set` is shown below:  
`Astro.cookies.set` 的签名如下所示：

// Astro.set(key, value, options)
key: string,
value: string | number | boolean | object,
options?: CookieOptions) \=> void

Note how different cookie value types may be set and additional cookie [options](https://www.npmjs.com/package/cookie#options-1) passed if needed, e.g., `domain`, `encode`, `expires`, `maxAge` or `httpOnly`.  
请注意如何设置不同的cookie值类型，并在需要时传递其他cookie选项，例如， `domain` 、 `encode` 、 `expires` 、 `maxAge` 或 `httpOnly` 。

### [](#the-request-ip-address)The request IP address  
请求IP地址

Understanding [IP addresses](https://en.wikipedia.org/wiki/IP_address) is beyond the scope of this book. However, we may gain access to the request’s IP address on the server via the `Astro.clientAddress` property.  
了解IP地址超出了本书的范围。但是，我们可以通过 `Astro.clientAddress` 属性访问服务器上请求的IP地址。

Below’s a simple example:  
下面是一个简单的例子：

\--\-
const ip \= Astro.clientAddress;
\--\-

<div\>Your IP address is: {ip}</div\>

* * *

[](#environment-variables)Environment variables 环境变量
----------------------------------------------------

If you’re completely new to environment variables, you might the thinking, _"Oi, what are Environment variables, and why should I care?"_  
如果你对环境变量完全陌生，你可能会想，“喂，什么是环境变量，我为什么要关心？“

Generally speaking, environment variables help us store important information like API keys or sensitive data without ever having to reveal them to clients accessing your application.  
一般来说，环境变量可以帮助我们存储重要信息，如API密钥或敏感数据，而不必向访问应用程序的客户端透露它们。

Like any secret, Environment variables can be arguably slightly tricky to handle. You need to know exactly where to find them, how to use them, and most importantly, how to keep them safe from prying eyes.  
像任何秘密一样，环境变量可以说有点棘手。你需要确切地知道在哪里可以找到它们，如何使用它们，最重要的是，如何保护它们免受窥探。

### [](#retrieving-environment-variables)Retrieving environment variables  
正在检索环境变量

In Astro, environment variables are accessed on the `import.meta.env` object.  
在Astro中，环境变量在 `import.meta.env` 对象上访问。

So, for example, if we had a `CAT_API_TOKEN` value, we would access it as follows:  
因此，例如，如果我们有一个 `CAT_API_TOKEN` 值，我们将按如下方式访问它：

\--\-
import.meta.env.CAT\_API\_TOKEN
\--\-

If you’re conversant with environment variables in node environments, you’ll notice that this differs from the classic `process.env` object. Astro leverages Vite, which uses the [import.meta](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/import.meta) Javascript feature.  
如果您熟悉节点环境中的环境变量，您会注意到这与经典的 `process.env` 对象不同。Astro利用了Vite，它使用了Meta JavaScript特性。

### [](#default-environment-variables)Default environment variables  
默认环境变量

We all have secrets.  
我们都有秘密。

I’m not quite sure of that. Let me rephrase: most people have secrets.  
我不太确定。让我换个说法：大多数人都有秘密

Similarly, every Astro project has some default secrets, aka environment variables, out of the box. Consider the defaults below:  
同样，每个Astro项目都有一些默认的秘密，即环境变量。考虑以下默认值：

// Get the mode the Astro site is running in: "development" | "production"
import.meta.env.MODE;

// Is the site running in production? returns true or false
import.meta.env.PROD;

// Is the site running in development? returns true or false
import.meta.env.DEV;

// The base URL of the Astro site
import.meta.env.BASE\_URL;

// Get the final deployed URL of the Astro site
import.meta.env.SITE;

// Get prefix for Astro-generated asset links
import.meta.env.ASSETS\_PREFIX;

For `import.meta.env.BASE_URL`, it’s important to note that this will default to `/` except explicitly stated in the project configuration. e.g.:  
对于 `import.meta.env.BASE_URL` ，需要注意的是，除非在项目配置中明确说明，否则默认为 `/` 。例如：

import { defineConfig } from "astro/config";

export default defineConfig({
  base: "/docs",
});

Astro will now use `/docs` as the root for our pages and assets in the development and production build.  
Astro现在将使用 `/docs` 作为开发和生产构建中的页面和资产的根。

Similarly, `import.meta.env.SITE` relies on the `site` property set in the astro config, e.g.:  
类似地， `import.meta.env.SITE` 依赖于astro配置中设置的 `site` 属性，例如：

import { defineConfig } from "astro/config";

export default defineConfig({
  site: "https://www.ohansemmanuel.com",
});

Astro will use this full URL to generate the site’s sitemap and canonical URLs where relevant.  
Astro将使用这个完整的URL来生成网站的站点地图和相关的规范URL。

`import.meta.env.ASSETS_PREFIX` also relies on the `build.assetsPrefix` option set in the project’s config, e.g.:  
`import.meta.env.ASSETS_PREFIX` 还依赖于项目配置中设置的 `build.assetsPrefix` 选项，例如：

import defineConfig from "astro/config";

export default defineConfig({
  build: {
    assetsPrefix: "https://cdn.example.com",
  },
});

This can be used if assets are served from a different domain than the current site, e.g., with the `https://cdn.example.com` prefix, assets will be fetched from `https://cdn.example.com/_astro/...`. This implies the files in the default astro build directory `./dist/astro` must be uploaded to the CDN directory to serve the assets.  
如果从与当前站点不同的域提供资产，则可以使用这一点，使用 `https://cdn.example.com` 前缀，将从 `https://cdn.example.com/_astro/...` 获取资源。这意味着默认astro构建目录 `./dist/astro` 中的文件必须上传到CDN目录以服务资产。

Phew! Out with the secrets!  
呼！把秘密说出来！

### [](#creating-environment-variables)Creating environment variables  
创建环境变量

It doesn’t do a lot of good if we can’t create our own secrets. Heck, it helps with the mystic.  
如果我们不能创造自己的秘密，那就没有什么好处了。见鬼，这对神秘主义有帮助。

The most common way to create environment variables is to use `.env` files.  
创建环境变量最常见的方法是使用 `.env` 文件。

For example, let’s go ahead and create a `.env` file in the root directory of our project directory with the following content:  
例如，让我们继续在项目目录的根目录中创建一个 `.env` 文件，内容如下：

// 📂 src/.env
CAT\_API\_TOKEN \= "this-is-the-cat-production-token";

We may then access the secret server-side via `import.meta.env.CAT_API_TOKEN`.  
然后，我们可以通过 `import.meta.env.CAT_API_TOKEN` 访问秘密服务器端。

I must mention that exposing certain environment variables to the client (browser) is possible. To do this, prefix the environment variable with a `PUBLIC_`, e.g.:  
我必须提到，向客户端（浏览器）公开某些环境变量是可能的。为此，请在环境变量前面加上 `PUBLIC_` ，例如：

PUBLIC\_INSENSITIVE\_TOKEN \= "this-is-public";

`PUBLIC_INSENSITIVE_TOKEN` will now be accessible both on the server and client. That’s an open secret. Anyone, and I mean anyone, can see your dirty laundry here. Only use this for insensitive environment variables.  
`PUBLIC_INSENSITIVE_TOKEN` 现在可以在服务器和客户端上访问。这是公开的秘密。任何人，我的意思是任何人，都可以看到你的脏衣服。仅对不敏感的环境变量使用此选项。

Remember that environment variables are only available in server-side code by default. Prefix environment variables with `PUBLIC_` to expose them to the client.  
请记住，默认情况下，环境变量仅在服务器端代码中可用。在环境变量的前缀加上 `PUBLIC_` ，以将它们公开给客户端。

It is also possible to run your project and provide environment variables from the CLI, as shown below:  
也可以运行项目并从CLI提供环境变量，如下所示：

CAT\_API\_TOKEN="this-is-the-cat-production-token npm run dev"

In this case, `CAT_API_TOKEN` will be available both server-side and client-side. Use with caution. We only tell people we trust secrets and never blindly trust a client, e.g., a user browser.  
在这种情况下， `CAT_API_TOKEN` 将在服务器端和客户端都可用。请谨慎使用。我们只告诉人们我们信任的秘密，从不盲目信任客户，例如，用户浏览器。

### [](#typescript-intellisense)Typescript IntelliSense Typescript智能感知

We don't get Typescript IntelliSense support if we attempt to access `CAT_API_TOKEN` in `pages/index.astro` after creating the `.env` file.  
如果在创建 `.env` 文件后尝试访问 `pages/index.astro` 中的 `CAT_API_TOKEN` ，则不会获得Typescript IntelliSense支持。

[![No Typescript IntelliSense for our custom environment variable.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-23%20at%2009.44.07.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-23%20at%2009.44.07.png)

_No Typescript IntelliSense for our custom environment variable.  
我们的自定义环境变量没有Typescript IntelliSense。_  
  
  

We’re pro developers; come on. Let’s fix this.  
我们是专业开发者;拜托，我们来解决这个问题。

We’ll find a `src/env.d.ts` file with projects started with an Astro template. Otherwise, go ahead and create one.  
我们将找到一个 `src/env.d.ts` 文件，其中包含以Astro模板启动的项目。否则，继续创建一个。

Here’s the initial content of the file if it already exists:  
下面是文件的初始内容（如果它已经存在）：

/// <reference types="astro/client" />

Let’s extend the default `ImportMeta` interface that provides type definitions for `import.meta.env` by adding the following:  
让我们扩展默认的 `ImportMeta` 接口，通过添加以下内容为 `import.meta.env` 提供类型定义：

interface ImportMetaEnv {
  readonly CAT\_API\_TOKEN: string;
  // add other custom env variables...
}

And voila! Typescript knows our secrets - for the better.  
瞧！Typescript知道我们的秘密-为了更好。

[![Typescript IntelliSense activated.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-23%20at%2009.50.10.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-23%20at%2009.50.10.png)

_Typescript IntelliSense activated.  
Typescript IntelliSense已激活。_  
  
  

[](#dynamic-routes)Dynamic routes 动态路由
--------------------------------------

Static routes are arguably easy to reason about. For example, `.astro`, `.md` and `.mdx` files in `src/pages` will automatically become pages on our website.  
静态路由可以说很容易推理。例如， `src/pages` 中的 `.astro` 、 `.md` 和 `.mdx` 文件将自动成为我们网站上的页面。

However, sometimes we require dynamic routes to prevent repetition. This typically happens when we have different routes with minimal UI changes between them.  
然而，有时我们需要动态路由来防止重复。这通常发生在我们有不同的路由，它们之间的UI变化最小的时候。

For example, if we were selling products on our website, we would have a different route for each product.  
例如，如果我们在我们的网站上销售产品，我们将为每个产品提供不同的路线。

// example routes for different products
www.example.com/product/understanding\-astro
www.example.com/product/astro\-a\-to\-z
www.example.com/product/astro\-for\-beginners
www.example.com/product/fullstack\-astro

// ❌ Providing multiple pages for each product
/pages/understanding\-astro.astro
/pages/astro\-a\-to\-z
/pages/astro\-for\-beginners
/pages/fullstack\-astro

The URL structure of the product pages could be represented by `www.example.com/product/${name}` where `name` means the product’s name.  
产品页面的URL结构可以用 `www.example.com/product/${name}` 表示，其中 `name` 表示产品名称。

Instead of creating different pages to represent each product, we may dynamically handle the product routing in one of two ways.  
我们不需要创建不同的页面来表示每个产品，而是可以通过以下两种方式之一动态地处理产品路由。

### [](#1-named-parameters)1\. Named parameters 1.命名参数

We could represent the variables in the route path with a named parameter surrounded by square brackets. For example, creating a file in the `pages` directory as follows:  
我们可以用方括号括起来的命名参数来表示路由路径中的变量。例如，在 `pages` 目录中创建文件，如下所示：

/pages/products/\[product\].astro

We may then grab the `product` path value on the page as follows:  
然后，我们可以在页面上获取 `product` path值，如下所示：

{
  /\*\* 📂 src/pages/\[product\].astro \*\*/
}
<h1\>{Astro.params.product}</h1\>;

Alternatively: 或者：

\--\-
 const {product} \= Astro.params
\--\-

<h1\>{product}</h1\>

Now if we visit the `/products/understanding-astro` page, we should have the title of the product displayed.  
现在，如果我们访问 `/products/understanding-astro` 页面，我们应该有产品的标题显示。

[![Grabbing dynamic route path values.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-24%20at%2010.25.23.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-24%20at%2010.25.23.png)

_Grabbing dynamic route path values.  
获取动态路由路径值。_  
  
  

In most cases, our variable path parameter will include a unique identifier, e.g., `/pages/products/[id].astro`.  
在大多数情况下，我们的变量路径参数将包括唯一标识符，例如，#0号。

The same routing works.  
同样的路由也是可行的。

It is also possible to leverage multiple named parameters in the route path, as shown below:  
也可以在路由路径中利用多个命名参数，如下所示：

{/\*\* /products/\[product\]\_\[id\].astro \*\*/}
<h1\>Product name: {Astro.params.product}</h1\>
<h1\>Product id: {Astro.params.id}</h1\>

This will be matched with a URL similar to `/products/understanding-astro_09u34359534530903453450`  
这将与类似于 `/products/understanding-astro_09u34359534530903453450` 的URL匹配

[![Matching multiple route named parameters.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-24%20at%2010.31.22.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-24%20at%2010.31.22.png)

_Matching multiple route named parameters.  
匹配多个路由命名参数。_  
  
  

### [](#2-rest-parameters)2\. Rest parameters 2.静止参数

Rest parameters provide ultimate flexibility in our URL routing. For example, we may use `[...path]` to match file paths of any depth. Where `path` could be represented by any string, e.g., `[...file]` or `[...somestring]`.  
Rest参数为我们的URL路由提供了极大的灵活性。例如，我们可以使用 `[...path]` 来匹配任何深度的文件路径。其中 `path` 可以由任何字符串表示，例如， `[...file]` 或 `[...somestring]` 。

Consider the following product pages:  
请考虑以下产品页面：

/products/product\-id
/products/category/product\-id/
/products/types/category/product\-id

The routes above will all be matched by the page `pages/product/[...path].astro`, and we can access the full dynamic string path within our code.  
上面的路由都将被页面 `pages/product/[...path].astro` 匹配，我们可以在代码中访问完整的动态字符串路径。

For example, create a file in `/pages/product/[...path].astro` with the following content:  
例如，在 `/pages/product/[...path].astro` 中创建一个包含以下内容的文件：

\--\-
const { path } \= Astro.params;
console.log({ path });
\--\-

<h1\>Hello there</h1\>

For the paths above, the `path` variable corresponds to `product-id`, `category/product-id` and `types/category/product-id`.  
对于上述路径， `path` 变量对应于 `product-id` 、 `category/product-id` 和 `types/category/product-id` 。

With much power comes much responsibility.  
权力越大，责任越大。

With the increased flexibility rest path parameters provide comes the responsibility of handling the paths in our code. For example, consider how we may handle the multiple product paths below:  
随着restpath参数提供的灵活性的增加，我们需要负责处理代码中的路径。例如，考虑我们如何处理以下多个产品路径：

\--\-
// Get the dynamic route path
const { path } \= Astro.params;

// Hold a list of all expected paths and corresponding data, e.g., title.
const page \= \[
  {
    path: undefined,
    title: "View all products"
  },
  {
    path: "product-id",
    title: "Some Product",
  },
  {
    path: "category/product-id",
    title: "Some Product Category Item",
  },
  {
    path: "types/category/product-id",
    title: "Some Product Type Category Item",
  },
\];

//Is this a valid path? i.e., exists in our list?
const relevantPageDetails \= page.find((v) \=> v.path \=== path);

if (!relevantPageDetails) {
  // redirect if the dynamic page isn't valid.
  return Astro.redirect("/404");
}
\--\-

// render the title of the page
<h1\>{relevantPageDetails.title}</h1\>

[![Rendering rest parameter routes.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-24%20at%2012.42.28@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-24%20at%2012.42.28@2x.png)

_Rendering rest parameter routes.  
渲染剩余参数管线。_  
  
  

It’s important to note that if the `path` is undefined, the root path will be matched, i.e., corresponds to `pages/product`.  
需要注意的是，如果 `path` 未定义，则根路径将被匹配，即：对应 `pages/product` 。

While this demonstrates using rest paths in server-side rendered pages, it is a contrived example where we’ve assumed the literal string “product-id”.  
虽然这演示了如何在服务器端呈现页面中使用REST路径，但这是一个人为的示例，我们假设文本字符串“product-id”。

In the real world, the literal string will be represented by different product id strings rather `product-id`; and we might not know what these are ahead of time!  
在真实的世界中，文字字符串将由不同的产品id字符串来表示，而不是 `product-id` ;我们可能不知道这些是什么

As we’ve done in the previous solution, keeping a massive list of all product IDs in our application becomes unmaintainable.  
正如我们在前面的解决方案中所做的那样，在应用程序中保留大量的所有产品ID列表变得无法维护。

For this use case, one way to achieve this would be to update our solution to have sufficiently complex matching logic, e.g., via regular expressions, because we don’t know the product IDs beforehand.  
对于该用例，实现这一点的一种方式将是更新我们的解决方案以具有足够复杂的匹配逻辑，例如，通过正则表达式，因为我们事先不知道产品ID。

\--\-
const { path \= "index" } \= Astro.params;

const page \= \[
  {
    match: /some-regex/,
    title: "View all products",
  },
  {
    match: /some-regex/,
    title: "Some Product",
  },
  {
    match: /some-regex/,
    title: "Some Product Category Item",
  },
  {
    match: /some-regex/,
    title: "Some Product Type Category Item",
  },
\];

const relevantPageDetails \= page.find((v) \=> path.match(v.match));

if (!relevantPageDetails) {
  return Astro.redirect("/404");
}
\--\-

<h1\>{relevantPageDetails.title}</h1\>

As a matter of personal preference, I’ve sworn a blood oath to avoid path rest parameters for multiple SSR page paths when I can’t deterministically determine the path variables beforehand.  
作为个人偏好，我发誓避免路径休息参数为多个SSR页面路径时，我不能确定性地确定路径变量预先。

Simple is sometimes better.  
简单有时更好。

In this case, I suggest separating the pages, i.e., creating multiple directories and letting the default Astro automatic routing kick in.  
在这种情况下，我建议将页面分开，即，创建多个目录，让默认的Astro自动路由启动。

For example, match the path `category/product-id` by creating a page in `category/[id]` and `types/category/[id]` to match the route `types/category/product-id`.  
例如，通过在 `category/[id]` 和 `types/category/[id]` 中创建一个页面来匹配路径 `category/product-id` 以匹配路由 `types/category/product-id` 。

They can also be composed with a common layout or shared components if they have identical user interfaces.  
如果它们具有相同的用户界面，也可以使用通用布局或共享组件来组合它们。

### [](#priority-order)Priority order 优先顺序

As we’ve discussed, URL paths can be matched in different ways, which begs the question, what happens when different file paths match the same URL path in our project?  
正如我们所讨论的，URL路径可以以不同的方式进行匹配，这就引出了一个问题：在我们的项目中，当不同的文件路径匹配相同的URL路径时，会发生什么？

Well, Astro needs to make a decision, and that’s following the priority list below:  
好吧，Astro需要做出决定，下面是优先级列表：

1.  Static routes, i.e., without path parameters, have the highest priority, e.g., `/pages/products/this-is-a-product`.  
    静态路由，即在没有路径参数的情况下，具有最高优先级，例如，#0号。
2.  Dynamic routes with named parameters have the next priority, e.g., `/pages/products/[id]`.  
    具有命名参数的动态路由具有下一优先级，例如，#0号。
3.  Dynamic routes with rest parameters have the lowest priority, e.g., `/pages/products/[...path]`.  
    具有休止参数的动态路由具有最低优先级，例如，#0号。
4.  Following the above, any ties will be resolved alphabetically.  
    按照上述步骤，任何领带将按字母顺序解决。

[![Route priority order from first to last.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/route_priority.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/route_priority.png)

_Route priority order from first to last.  
从第一个到最后一个路由优先级顺序。_  
  
  

[](#server-endpoints)Server endpoints 服务器端点
-------------------------------------------

Server endpoints are like the secret weapons in our arsenal when running server-side functions.  
当运行服务器端函数时，服务器端点就像是我们武器库中的秘密武器。

They can be used as REST API endpoints to run functions such as database access, authentications, and verifications without exposing sensitive data to the client, i.e., we can securely execute code on the server at runtime in these functions.  
它们可以用作REST API端点来运行数据库访问、身份验证和验证等功能，而不会向客户端暴露敏感数据，即我们可以在运行时在这些函数中安全地执行服务器上的代码。

Consider the current state of our project with a `page/products` directory. What if we wanted to create an API route to handle some client requests? How would we do this?  
考虑一下我们的项目的当前状态与 `page/products` 目录。如果我们想创建一个API路由来处理一些客户端请求，该怎么办？我们该怎么做？

### [](#creating-server-endpoints)Creating server endpoints  
创建服务器终结点

To create an API route in the `server` output mode, create a `.ts` or `.js` file within the `pages` directory. Optionally, you may see endpoints created with the type of data the endpoint returns in the file name, e.g., `.json.ts`  
要在 `server` 输出模式下创建API路由，请在 `pages` 目录下创建 `.ts` 或 `.js` 文件。您还可以在文件名中看到端点返回的数据类型创建的端点，例如， `.json.ts`

I prefer to keep server endpoints simple and omit additional file names. Let’s go ahead and create an `api.ts` file and handle incoming `GET` requests as shown below:  
我更喜欢保持服务器端点简单，省略其他文件名。让我们继续创建一个 `api.ts` 文件并处理传入的 `GET` 请求，如下所示：

// 📂 pages/products/api
import type { APIRoute } from "astro";

export const get: APIRoute \= (ctx) \=> {
  return {
    body: JSON.stringify({
      message: "Hello world",
    }),
  };
};

*   Note the `APIRoute` type used on the `get` function. This represents the API route function type definition.  
    注意 `get` 函数中使用的 `APIRoute` 类型。这表示API路由函数类型定义。
    
*   Every API route function receives a context object, e.g., represented by `ctx`. The [context object](https://docs.astro.build/en/reference/api-reference/#endpoint-context) contains relevant properties we’ll take a look at shortly.  
    每个API路由函数接收上下文对象，例如，由 `ctx` 表示。context对象包含相关的属性，我们将很快看到。
    
*   As shown above, an API route function can return a response with a `body`. The complete response form is shown below:  
    如上所示，API路由函数可以返回具有 `body` 的响应。完整的回复表如下所示：
    
    {
       body: string
       encoding?: 'ascii' | 'utf8' | 'utf-8' | 'utf16le' |
    		 'ucs2' | 'ucs-2' | 'base64' | 'base64url' |
    		  'latin1' | 'binary' | 'hex'
    }
    
    We may also return a standard response via the Response object as shown below:  
    我们也可以通过Response对象返回一个标准响应，如下所示：
    
    import type { APIRoute } from "astro";
    
    export const get: APIRoute \= (ctx) \=> {
      return new Response(
        JSON.stringify({
          message: "Hello world",
        }),
        {
          status: 200,
        }
      );
    };
    

### [](#request-details)Request details 请求详情

Accessing details of the request object is a breeze with API routes. For example, we may access the request object on the context object to check its headers, as shown below:  
使用API路由访问请求对象的详细信息是轻而易举的。例如，我们可以访问context对象上的request对象来检查它的头，如下所示：

import type { APIRoute } from "astro";

export const get: APIRoute \= (ctx) \=> {
  // check for an Authorization header on the request
  const auth \= ctx.request.headers.get("Authorization");

  // The user is unauthorised to get this resource
  if (!auth) {
    return new Response(JSON.stringify({ message: "Unauthorized" }), {
      status: 401,
    });
  }

  return new Response(JSON.stringify({ message: "Hello world" }), {
    status: 200,
  });
};

We could also destructure properties of the context object, e.g., the request object, as shown below:  
我们还可以解构上下文对象的属性，例如，请求对象，如下所示：

export const get: APIRoute \= ({ request }) \=> {
  // ...
};

While getting the `request` object is great, consider the complete list of properties available on the endpoint context object:  
虽然获得 `request` 对象很棒，但请考虑端点上下文对象上可用的完整属性列表：

export const get: APIRoute \= ({
  url,
  site,
  params,
  request,
  cookies,
  generator,
  redirect,
  clientAddress,
}) \=> {
  return new Response(JSON.stringify({ message: "Hello world" }), {
    status: 200,
  });
};

Some of these should be familiar from discussing the request and response objects on the `Astro` global; however, here’s a quick breakdown:  
其中的一些应该在讨论 `Astro` global上的请求和响应对象时熟悉;但是，这里有一个快速分解：

  

Property 财产

What? \- 你说什么？

url url

A standard [URL](https://developer.mozilla.org/en-US/docs/Web/API/URL) interface.  
标准URL接口。

site 现场

The site property from the astro configuration file.  
astro配置文件中的站点属性。

params 参数

An object containing values of the dynamic path segments matched by the request.  
一个对象，包含与请求匹配的动态路径段的值。

request 请求

A standard [Request](https://developer.mozilla.org/en-US/docs/Web/API/Request) interface of the Fetch API.  
Fetch API的标准请求接口。

cookies 饼干

Similar to Astro.cookies. It contains utilities for reading and manipulating cookies.  
类似Astro.cookies。它包含用于阅读和操作Cookie的实用程序。

generator 发电机

Indicates the version of Astro our project is running.  
指示我们的项目正在运行的Astro版本。

redirect 重定向

Similar to Astro.redirect.  
类似Astro.Redirect。

clientAddress 客户端地址

Specifies the IP address of the request. Similar to Astro.clientAddress  
指定请求的IP地址。类似Astro.clientAddress

The alien properties here are `generator`, `url` and `params`.  
这里的外星人财产是 `generator` 、 `url` 和 `params` 。

`generator` is easy to reason about, while `url` represents a [URL](https://developer.mozilla.org/en-US/docs/Web/API/URL) object constructed from `request.url` i.e., identical to `new URL(request.url)`. It’s worth mentioning that a similar object may be accessed on the `Astro` global via `Astro.url`. This could come in handy in static pages.  
`generator` 很容易推理，而 `url` 表示从 `request.url` 构造的URL对象，即：与 `new URL(request.url)` 相同。值得一提的是，在 `Astro` global上可以通过 `Astro.url` 访问类似的对象。这在静态页面中可能会派上用场。

What about `params`? Well, that requires a separate section when we discuss dynamic routes.  
`params` 怎么样？好吧，在我们讨论动态路由时，这需要单独一节。

### [](#dynamic-api-routes)Dynamic API routes 动态API路由

The dynamic route fabric on pages works the same magic on API endpoints.  
页面上的动态路由结构在API端点上也有同样的魔力。

For example, our API endpoint is in the `pages/products/api` file. What if we wanted client requests to be made in the format: `GET /api/products/${id}`?  
例如，我们的API端点位于 `pages/products/api` 文件中。如果我们希望客户端请求以以下格式发出：一号？

Did you notice the variable `id`?  
你注意到变量 `id` 了吗？

In this case, we may leverage dynamic routes as shown below:  
在这种情况下，我们可以利用如下所示的动态路由：

// 📂 pages/api/products/\[id\]

import type { APIRoute } from "astro";

export const get: APIRoute \= async (ctx) \=> {
  // Get the product ID
  const productId \= ctx.params.id;

  try {
    const response \= await fetch("https://fakestoreapi.com/products/1");
    const data \= await response.json();

    return new Response(
      JSON.stringify({
        ...data,
        // Add the ID in the response body
        id: productId,
      }),
      {
        status: 200,
      }
    );
  } catch (error) {
    return new Response(
      JSON.stringify({
        message: "An error occurred.",
      }),
      {
        status: 500,
      }
    );
  }
};

I might have sprung a surprise on you in the code block above! However, the main difference here is we’re reaching out to some external API (think fetching data from a database) and sending the response back to the client.  
我可能会在上面的代码块中给你一个惊喜！然而，这里的主要区别是我们接触到一些外部API（想想从数据库获取数据），并将响应发送回客户端。

Another critical point is to notice how the specific id is retrieved from `ctx.params.id`, where `ctx` represents the context object.  
另一个关键点是注意如何从 `ctx.params.id` 检索特定id，其中 `ctx` 表示上下文对象。

If we make a GET request to `api/products/astro-book-001`, we should have some data returned to the client.  
如果我们向 `api/products/astro-book-001` 发出GET请求，我们应该有一些数据返回给客户端。

[![Testing the product API on hopscotch.io](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-25%20at%2008.57.00@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-25%20at%2008.57.00@2x.png)

_Setting a custom header on the server response.  
在服务器响应上设置自定义标头。_  
  
  

Note how whatever “id” is passed in the request path is rightly retrieved, e.g., `astro-book-001`.  
注意在请求路径中传递的任何“id”如何被正确地检索，例如，#0号。

[![The product ID returned in the JSON response.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-25%20at%2008.49.31@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-25%20at%2008.49.31@2x.png)

_The product ID returned in the JSON response.  
JSON响应中返回的产品ID。_  
  
  

To re-iterate, we can get the path segments in the dynamic route pattern via `context.params` and voila! We have our use case resolved.  
为了重新迭代，我们可以通过 `context.params` 获得动态路由模式中的路径段，瞧！我们已经解决了我们的用例。

Passing query parameters to `GET` requests is not unheard of in the real world. Heck, it’s quite an everyday use case!  
将查询参数传递给 `GET` 请求在真实的世界中并非闻所未闻。Heck，这是一个相当日常的用例！

Assuming the following client request `GET api/products/astro-book-001?version=2&publishedDate=2023-06-12`, how would we handle this?  
假设下面的客户端请求 `GET api/products/astro-book-001?version=2&publishedDate=2023-06-12` ，我们将如何处理这个问题？

It’s important to note that `version` and `publishedDate` will not be present in `context.params`. However, we can grab these from the `URL` object as shown below:  
值得注意的是， `version` 和 `publishedDate` 不会出现在 `context.params` 中。但是，我们可以从 `URL` 对象中获取这些信息，如下所示：

// 📂 pages/api/products/\[id\]
export const get: APIRoute \= async (ctx) \=> {
  const productId \= ctx.params.id;

  // retrieve relevant search parameters, aka URL query parameters
  const searchParams \= ctx.url.searchParams;
  const version \= searchParams.get("version");
  const publishedDate \= searchParams.get("publishedDate");

  try {
    const response \= await fetch("https://fakestoreapi.com/products/1");
    const data \= await response.json();

    // Return a new response with the retrieved
    // "version" and "publishedDate"
    return new Response(
      JSON.stringify({
        ...data,
        version,
        publishedDate,
        id: productId,
      }),
      {
        status: 200,
      }
    );
  } catch (error) {
    return new Response(
      JSON.stringify({
        message: "An error occurred",
      }),
      {
        status: 500,
      }
    );
  }
};

The crux of the solution is the following:  
解决方案的关键在于以下几点：

// retrieve relevant search parameters, aka URL query parameters
const searchParams \= ctx.url.searchParams;
const version \= searchParams.get("version");
const publishedDate \= searchParams.get("publishedDate");

[![Retrieving query parameters in a server endpoint.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-25%20at%2009.13.04@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-25%20at%2009.13.04@2x.png)

_Retrieving query parameters in a server endpoint.  
正在服务器终结点中检索查询参数。_  
  
  

### [](#dedicated-api-directory)Dedicated api directory 专用API目录

At the time of writing, API routes must live in the `pages` directory with appropriate file endings, e.g., `.ts` or `.js`.  
在撰写本文时，API路由必须位于 `pages` 目录中，并具有适当的文件结尾，例如， `.ts` 或 `.js` 。

For example, you can have `pages/anyFileName.js` act as a server endpoint.  
例如，您可以让 `pages/anyFileName.js` 充当服务器端点。

However, I find it easier (and better) to have my server API routes in a dedicated `pages/api` directory instead of mixing these in other page routes.  
然而，我发现将我的服务器API路由放在一个专用的 `pages/api` 目录中，而不是将它们混合在其他页面路由中。

One advantage to this is potentially making it easier to redirect a subdomain to a single path for all API routes, e.g., redirect `api.my-website.com/...` to `my-website.com/api/...`.  
这样做的一个优点是潜在地使得更容易将子域重定向到用于所有API路由的单个路径，例如，重定向 `api.my-website.com/...` 到 `my-website.com/api/...` 。

On the flip side, an arguable downside is we break the collocation of other routes, e.g., standard pages such as `pages/products/...` will have their associated API route in `api/products/...`. This is a downside and a trade-off I happily make in production applications.  
另一方面，一个值得商榷的缺点是我们打破了其他路线的搭配，例如，标准页面（例如 `pages/products/...` ）将在 `api/products/...` 中具有其相关API路由。这是一个缺点，也是我在生产应用程序中乐于做出的权衡。

### [](#supporting-other-http-methods)Supporting other HTTP methods  
支持其他HTTP方法

All our examples so far have used the `get` method within our API routes. However, Astro does support all the other HTTP methods, such as `post` or `delete`.  
到目前为止，我们所有的示例都在API路由中使用了 `get` 方法。不过，Astro确实支持所有其他HTTP方法，例如 `post` 或 `delete` 。

Consider the following example that extends our `api/products/${id}` endpoint to include more methods:  
考虑以下示例，扩展了我们的 `api/products/${id}` 端点以包含更多方法：

import type { APIRoute } from "astro";

// Handle client GET requests
export const get: APIRoute \= async (ctx) \=> {
  const productId \= ctx.params.id;
  try {
    // fetch remote resource
    const response \= await fetch("https://fakestoreapi.com/products/1");
    const data \= await response.json();

    // return data, and the id param
    return new Response(
      JSON.stringify({
        ...data,
        id: productId,
      }),
      {
        status: 200,
      }
    );
  } catch (error) {
    return new Response(
      JSON.stringify({
        message: "An error occurred",
      }),
      {
        status: 500,
      }
    );
  }
};

/\*\*
 \* Handle "DELETE" requests
 \* "delete" is a reserved word in Javascript. Hence, the function name "del"
 \*/
export const del: APIRoute \= async (ctx) \=> {
  const productId \= ctx.params.id;
  try {
    const response \= await fetch("https://fakestoreapi.com/products/1", {
      method: "DELETE",
    });
    const data \= await response.json();

    return new Response(
      JSON.stringify({
        id: productId,
        message: "deleted",
        title: data.title,
      }),
      {
        status: 202,
      }
    );
  } catch (error) {
    return new Response(
      JSON.stringify({
        message: "An error occurred",
      }),
      {
        status: 500,
      }
    );
  }
};

/\*\*
 \* Handle "POST" requests
 \*/
export const post: APIRoute \= async (ctx) \=> {
  // Get the POST body data
  const data \= await ctx.request.json();

  return new Response(
    JSON.stringify({
      message: "Created",
      data,
    })
  );
};

Go ahead and give these a try!  
来吧，给予看！

[![Making a POST request to our server endpoint.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-25%20at%2008.53.33@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-25%20at%2008.53.33@2x.png)

_Making a POST request to our server endpoint.  
向服务器端点发出POST请求。_  
  
  

As a fallback to handle other HTTP methods, we can provide an `all` function to match methods that don’t have a corresponding exported function. Consider the example below:  
作为处理其他HTTP方法的后备，我们可以提供一个 `all` 函数来匹配没有相应导出函数的方法。考虑下面的示例：

...
export const all: APIRoute \= async (ctx) \=> {
  // Get the request method
  const method \= ctx.request.method;

  // Return a response
  return new Response(
    JSON.stringify({
      method,
      message: "Unsupported HTTP method",
    }),
    {
      status: 501, // unsupported
    }
  );
};

This will match unhandled methods in our implementation, such as `PATCH` requests.  
这将匹配我们实现中未处理的方法，例如 `PATCH` 请求。

[![Handling unsupported methods in a server endpoint.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-25%20at%2008.56.25@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-25%20at%2008.56.25@2x.png)

_Handling unsupported methods in a server endpoint.  
处理服务器端点中不支持的方法。_  
  
  

[](#streams-oh-streams)Streams, oh streams 溪流啊溪流
------------------------------------------------

I’ve chosen a playful title for this section as it involves a relatively lesser-known feature of Astro: server streaming.  
我为这一部分选择了一个有趣的标题，因为它涉及到Astro的一个相对不为人知的功能：服务器流。

### [](#what-is-server-streaming)What is server streaming?  
什么是服务器流？

Generally speaking, SSR refers to generating HTML on the server and sending that to a browser in response to a request.  
一般来说，SSR指的是在服务器上生成HTML并将其发送到浏览器以响应请求。

In theory, we may break this off into distinct steps:  
从理论上讲，我们可以将其分解为不同的步骤：

*   Browser requests a page  
    浏览器请求页面
*   The server renders the page (and every associated data)  
    服务器呈现页面（以及所有相关数据）
*   The server returns the **fully formed page** to the browser  
    服务器将完整格式的页面返回给浏览器
*   The browser renders the page  
    浏览器呈现页面

[![Server sending a fully formed page to the client.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/send_full_page.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/send_full_page.png)

_Server sending a fully formed page to the client.  
服务器正在向客户端发送完整格式的页。_  
  
  

What’s important here is to note that the server generates the page’s full HTML, and only then does it send the HTML to the browser.  
这里需要注意的是，服务器生成页面的完整HTML，然后才将HTML发送到浏览器。

Now, consider a different approach.  
现在，考虑一种不同的方法。

In most cases, certain parts of the HTML page are static and could be sent from the server immediately, i.e., without relying on fetching all the relevant data.  
在大多数情况下，HTML页面的某些部分是静态的，可以立即从服务器发送，即而不依赖于获取所有相关数据。

What if the server could transmit the `HTML` to the browser as it creates the page server side?  
如果服务器可以在创建页面服务器端时将 `HTML` 发送到浏览器，会怎么样？

[![The server sends partial chunks to the browser.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/server_send_chunks.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/server_send_chunks.png)

_The server sends partial chunks to the browser.  
服务器向浏览器发送部分块。_  
  
  

This is the crux of streaming: stream HTML to a browser as the server generates the HTML.  
这就是流媒体的关键：当服务器生成HTML时，将HTML流式传输到浏览器。

### [](#why-should-we-bother)Why should we bother?  
我们为什么要烦恼呢？

In theory, browsers can render partial HTML[1](#user-content-fn-1-f4f0d18a4f9735101c31b54e1d6a2fcf) and support receiving and rendering HTML data in chunks. Users can view and interact with a page as it streams rather than waiting for the full page to be sent as one big chunk.  
理论上，浏览器可以呈现部分HTML [1](#user-content-fn-1-f4f0d18a4f9735101c31b54e1d6a2fcf) ，并支持接收和呈现块形式的HTML数据。用户可以在页面流时查看并与其交互，而不是等待整个页面作为一大块发送。

Different applications will need various workarounds. However, streaming improves server overhead. The server doesn’t need as much memory to buffer entire pages. It’ll incrementally send page data to the browser releasing memory to handle more requests and consequently save overhead costs. This is a great argument to convince your boss that streaming is good for the company’s wallets (except your company plays the silly game of _burning as much cash as possible_).  
不同的应用程序需要各种变通方法。然而，流式传输改善了服务器开销。服务器不需要那么多内存来缓冲整个页面。它将递增地向浏览器发送页面数据，释放内存来处理更多的请求，从而保存开销。这是一个很好的理由，可以说服你的老板，流媒体对公司的钱包有好处（除了你的公司玩的愚蠢游戏，尽可能多地烧钱）。

### [](#streaming-is-easy-yet-difficult)Streaming is easy yet difficult  
流媒体很容易，但也很难

I’ve sung praises of streaming. It is conceptually easy to reason about. However, in practice is not unlikely to experience some difficult use cases.  
我赞美过流媒体。这在概念上很容易推理。然而，在实践中并非不太可能遇到一些困难的用例。

A great example is considering the `<title>` of a page that goes in our HTML’s `<head>`. Typically, the `<head>` is one of the first elements we stream to the browser. However, some elements within the `<head>` could very well be dynamic, e.g., we may have a `<title>` in the form `<title>{product name} fetched from the server<title>`.  
一个很好的例子是考虑一个页面的 `<title>` ，它进入了我们的HTML的 `<head>` 。通常， `<head>` 是我们流到浏览器的第一个元素之一。然而， `<head>` 中的一些元素很可能是动态的，例如：我们可能有一个 `<title>` 形式 `<title>{product name} fetched from the server<title>` 。

What’s likely to happen is we stream a stale `<title>` before we eventually get the product name from the database (assuming the database is the external source of data here).  
可能发生的是，在最终从数据库中获取产品名称之前，我们流掉了一个过时的 `<title>` （假设数据库是这里的外部数据源）。

This out-of-order streaming represents some of the most common issues we may face in practice. In this example, we may provide a generic `<title>` placeholder and continue streaming.  
这种无序流代表了我们在实践中可能面临的一些最常见的问题。在该示例中，我们可以提供通用 `<title>` 占位符并继续流式传输。

Once the data becomes available server-side, we may stream a tiny `<script>` that updates the page title to the desired value.  
一旦数据在服务器端可用，我们可以流一个微小的 `<script>` ，将页面标题更新为所需的值。

Okay, that’s enough backstory! Next, let’s dig into streaming in Astro!  
好了，背景故事到此为止！接下来，让我们深入了解Astro中的流媒体！

### [](#server-streaming-in-astro)Server streaming in Astro  
Astro中的服务器流

Now that you’re convinced (not confused) about the importance of server streaming let’s explore how streaming in Astro works.  
现在您已经确信（而不是困惑）服务器流的重要性，让我们来探讨Astro中的流是如何工作的。

Perhaps the most important thing to know is that Astro supports streaming by default. Yes, you heard that right. Browsers also natively support HTML streaming.  
也许最重要的是，Astro默认支持流媒体。是的，你没听错。浏览器本身也支持HTML流。

Essentially, within the Astro template, Astro will stream out HTML that occurs before hitting an async boundary.  
本质上，在Astro模板中，Astro将在到达异步边界之前流出HTML。

For example, consider the basic page with a `<LoadPets/>` component responsible for fetching and rendering some pet data from a database.  
例如，考虑一个带有 `<LoadPets/>` 组件的基本页面，该组件负责从数据库中获取和呈现一些宠物数据。

\--\-
import LoadPets from '../components/LoadPets.astro'
\--\-

<html\>
 <head\>
   <title\> Petsssss! </title\>
 </head\>
 <body\>
   <h1\>This is a pet site</h1\>
   <p\> Consider how pets are awesome ... </p\>
   <LoadPets /\>
 </body\>
</html\>

In this contrived example, Astro will stream out the `<head>`, `<h1>` and `<p>` sections to the browser before stopping to fetch the data in `<LoadPets />` and then stream its result to the browser when ready.  
在这个人为的例子中，Astro会将 `<head>` 、 `<h1>` 和 `<p>` 部分流到浏览器，然后停下来获取 `<LoadPets />` 中的数据，然后在准备好时将其结果流到浏览器。

Let’s explore a visual example.  
让我们来看看一个可视化的例子。

Update the `ssr` project to have a new `streaming.astro` page with the following content:  
更新 `ssr` 项目，使其具有包含以下内容的新 `streaming.astro` 页面：

\--\-
import Block from "../components/Block.astro";
\--\-

<html\>
  <head\>
    <title\>Streaming</title\>
  </head\>
  <body\>
    <Block text\="Block #1" delay\={1000} /\>
    <Block text\="Block #2" delay\={2000} /\>
    <Block text\="Block #3" delay\={3000} /\>
    <Block text\="Block #4" delay\={4000} /\>
    <Block text\="Block #5" delay\={5000} /\>
  </body\>
</html\>

The `<Block/>` component receives a `text` and a `delay` prop. `delay` represents how long to wait before rendering its template, i.e., simulating some network request call.  
`<Block/>` 组件接收 `text` 和 `delay` prop。 `delay` 表示在渲染其模板之前等待多长时间，即，模拟某网络请求呼叫。

Here’s the `<Block/>` component:  
下面是 `<Block/>` 组件：

{/\*\* 📂 src/components/Block.astro \*\*/}
\--\-
import { sleep } from "../sleep";

interface Props {
  text: string;
  delay: number;
}

const { text, delay } \= Astro.props;

await sleep(delay);
\--\-

<div\>
  {text}
</div\>

<style\>
  div {
    margin: 1rem 0;
    padding: 2rem 6rem;
    border\-radius: 10px;
    background\-color: blanchedalmond;
  }
</style\>

Where `sleep` is a utility as follows:  
其中 `sleep` 是一个实用程序，如下所示：

// 📂 src/sleep.ts
export const sleep \= (delay: number) \=>
  new Promise((r) \=> setTimeout(r, delay));

Now, go to the Chrome browser and visit the `/streaming` route to view the wonders of streaming.  
现在，转到Chrome浏览器并访问 `/streaming` 路由，以查看流媒体的奇妙之处。

[![Initial block streamed while awaiting Block #2.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-04-26%20at%2011.47.56.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-04-26%20at%2011.47.56.png)

_Initial block streamed while awaiting Block #2.  
在等待块#2时流式传输初始块。_  
  
  

Each block of content comes in one at a time!  
每个内容块一次一个！

It’s important to note that we don’t have to abstract the async bits into components. Streaming equally works with standard promises within the Astro template:  
需要注意的是，我们不必将异步位抽象为组件。流式传输同样适用于Astro模板中的标准承诺：

\--\-
import Block from "../components/Block.astro";
import { sleep } from "../sleep";

const block5Promise \= async () \=> {
  await sleep(1000);
  return "Block #5";
};
\--\-

<html\>
  <head\>
    <title\>Streaming</title\>
  </head\>
  <body\>
    <Block text\="Block #1" delay\={1000} /\>
    <Block text\="Block #2" delay\={2000} /\>
    <Block text\="Block #3" delay\={3000} /\>
    <Block text\="Block #4" delay\={4000} /\>
    <p\>{block5Promise}</p\>
  </body\>
</html\>

An important fact to note here is that Astro initiates the async fetches in parallel when sibling async components are in the component tree.  
这里需要注意的一个重要事实是，当同级异步组件在组件树中时，Astro会并行启动异步获取。

So in our example, `Block #1` through `Block #5` start fetching data in parallel and don’t block one another.  
因此，在我们的示例中， `Block #1` 到 `Block #5` 开始并行地获取数据，并且不互相阻塞。

When `Block #4` is rendered, `block5Promise` is already fetched as it takes one second compared to `Block #4`’s four seconds. Hence, the result of `block5` is streamed alongside `Block #4`.  
当 `Block #4` 被渲染时， `block5Promise` 已经被提取，因为与 `Block #4` 的4秒相比，它花费了1秒。因此， `block5` 的结果与 `Block #4` 一起流式传输。

This can be difficult to grasp via text descriptions.  
这可能很难通过文本描述来理解。

[![Describing the parallelized rendering of each block.](/understanding-astro/understanding-astro-book/raw/master/images/ch6/CleanShot%202023-05-25%20at%2013.44.47@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch6/CleanShot%202023-05-25%20at%2013.44.47@2x.png)

_Describing the parallelized rendering of each block.  
描述每个块的并行渲染。_  
  
  

Give this a look in your Chrome browser.  
在你的Chrome浏览器中给予一下。

### [](#taking-advantage-of-streaming)Taking advantage of streaming  
利用流媒体

Since Astro supports streaming by default, understanding and applying it is the first step to taking advantage of streaming.  
由于Astro默认支持流媒体，了解和应用它是利用流媒体优势的第一步。

Consider the following example:  
请考虑以下示例：

\--\-
import { sleep } from "../sleep";

const getSomeData \= async () \=> {
  await sleep(1000);
  return "some data ";
};

const getSomeOtherData \= async () \=> {
  await sleep(200);
  return "another data";
};

const data \= await getSomeData();
const otherData \= await getSomeOtherData();
\--\-

<html\>
  <head\>
    <title\>Product</title\>
  </head\>
  <body\>
    <h2\>A name</h2\>
    <p\>{data}</p\>
    <h2\>A fact</h2\>
    <p\>{otherData}</p\>
  </body\>
</html\>

In the example above, we presumably need to fetch two resources, `data` and `otherData`. However, our solution blocks streaming. We wait for `await getSomeData()` and `await getSomeOtherData()` before sending the full page to the browser.  
在上面的例子中，我们大概需要获取两个资源， `data` 和 `otherData` 。然而，我们的解决方案阻止了流。我们等待 `await getSomeData()` 和 `await getSomeOtherData()` ，然后再将完整页面发送到浏览器。

If we wanted to take advantage of server streaming, we could either render the promises directly within the markup:  
如果我们想利用服务器流，我们可以直接在标记中呈现promise：

\--\-
import { sleep } from "../sleep";

const getSomeData \= async () \=> {
  await sleep(1000);
  return "some data ";
};

const getSomeOtherData \= async () \=> {
  await sleep(200);
  return "another data";
};
\--\-

<html\>
  <head\>
    <title\>Product</title\>
  </head\>
  <body\>
    <h2\>A name</h2\>
    <p\>{getSomeData}</p\>
    <h2\>A fact</h2\>
    <p\>{getSomeOtherData}</p\>
  </body\>
</html\>

Or extract the data fetching to child components:  
或者提取数据到子组件：

\--\-
import Data from '../components/Data.astro'
import OtherData from '../components/OtherData.astro'
\--\-

<html\>
  <head\>
    <title\>Product</title\>
  </head\>
  <body\>
    <h2\>A name</h2\>
    <!\-- Handle fetch of data in <Data /\> --\>
    <Data /\>
    <h2\>A fact</h2\>
    <!\-- Handle other data fetch in <OtherData /\> --\>
    <OtherData /\>
  </body\>
</html\>

Excellent! 太棒了！

[](#conclusion)Conclusion 结论
----------------------------

Server-side rendering is powerful and opens up many opportunities in our application. However, with much power comes responsibility. So, before considering making every page in your application server-rendered, consider the PROs and CONs (e.g., as discussed in Chapter 3). Then, make the right decision for your application — that’s where true responsibility lies. And do not forget to leverage hybrid rendering where possible.  
服务器端渲染功能强大，为我们的应用程序提供了许多机会。然而，权力越大，责任就越大。因此，在考虑使应用程序中的每个页面都呈现为服务器之前，请考虑PRO和CON（例如，如第3章所述）。然后，为您的应用程序做出正确的决定-这才是真正的责任所在。并且不要忘记尽可能利用混合渲染。
