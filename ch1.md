

[](#table-of-contents)Table of contents 第一章目录
---------------------------------------------

[](#-understanding-astro)🚀 Understanding Astro 了解Astro
=======================================================

By [Ohans Emmanuel](https://www.ohansemmanuel.com/) 作者：Ohans Emmanuel

  

[](#chapter-1-build-your-first-astro-application)Chapter 1: Build your first Astro Application  
第1章：构建第一个Astro应用程序
-------------------------------------------------------------------------------------------------------------------

> Long is the road to learning by precepts, but short and successful by examples - Seneca the Younger.  
> 从戒律中学习的道路是漫长的，但从榜样中学习的道路是短暂的。

Get started with the basics of Astro by building a practical application: a personal site.  
通过构建一个实际应用程序开始了解Astro的基础知识：个人网站

  
  
  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch1/view-project@3x.png)](https://astro-beginner-project.vercel.app/)

  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch1/watch-instead@3x.png)](https://ohans.me/understanding-astro-udemy)

  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch1/view-project.png)](https://github.com/understanding-astro/astro-beginner-project)

  
  

[](#what-youll-learn)What you’ll learn 您将学到的内容
----------------------------------------------

*   Build a personal website with Astro.  
    使用Astro创建个人网站。
*   Set up a local development environment for Astro.  
    为Astro设置本地开发环境。
*   Familiarity with Astro components, layouts and pages.  
    熟悉Astro组件、布局和页面。
*   A working knowledge of styles and scripts in Astro.  
    在Astro中的样式和脚本的工作知识。
*   Theming Astro sites via CSS variables.  
    通过CSS变量为Astro站点创建主题。
*   Leveraging markdown pages for ease.  
    利用markdown页面轻松。
*   Deployment of a static Astro application.  
    静态Astro应用程序的部署。

[](#project-overview)Project Overview 项目概况
------------------------------------------

I remember my first commercial web development project. In retrospect, it was a disaster. One built by a passionate self-taught engineer, but a disaster still.  
我记得我的第一个商业网站开发项目。回想起来，那是一场灾难。一个由一个充满激情的自学成才的工程师建造的，但仍然是一场灾难。

Let’s make your first Astro project one we’ll remember for good.  
让我们把你的第一个天文项目变成一个我们永远记住的项目。

[](#getting-started)Getting started 开始使用
----------------------------------------

**Astro is a web framework designed for speed**. Before we get to the good stuff, let’s ensure we’re both on the same page.  
Astro是一个专为速度而设计的Web框架。在我们开始之前，让我们确保我们都在同一页上。

### [](#install-nodejs)Install Node.js 安装Node.js

Firstly, make sure you have nodejs installed.  
首先，确保你已经安装了nodejs。

If unsure, run `node --version` in your terminal. You will get back a node version if you have nodejs installed.  
如果不确定，请在终端中运行 `node --version` 。如果你安装了nodejs，你会得到一个节点版本。

[![Get NodeJS version from the CLI.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-29%20at%2011.11.18@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-29%20at%2011.11.18@2x.png)

_Get NodeJS version from the CLI.  
从CLI获取NodeJS版本。_  
  
  

Don’t have nodejs installed? Then, visit the official [download](https://nodejs.org/en/download) page and install the necessary package for your operating system. It’s as easy as installing any other computer program. Click, click, click!  
没有安装nodejs？然后，访问官方下载页面并为您的操作系统安装必要的软件包。它就像安装任何其他计算机程序一样简单。咔嗒咔嗒！

[![The NodeJS download page.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-28%20at%2010.44.30@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-28%20at%2010.44.30@2x.png)

_The NodeJS download page.  
NodeJS下载页面_  
  
  

### [](#setting-up-your-code-editor)Setting up your code editor  
设置代码编辑器

I’ll avoid any heated debate(s) on what code editor you should be writing software with. The truth is I do not care. Quite frankly.  
我将避免任何关于您应该使用什么代码编辑器来编写软件的激烈争论。事实是我不在乎。坦白说

However, I use Visual Studio Code (VSCode).  
Visual Studio Code（VSCode）

You can develop Astro applications with any code editor, but VSCode is also the officially recommended editor for Astro.  
您可以使用任何代码编辑器开发Astro应用程序，但VSCode也是官方推荐的Astro编辑器。

If you’re building with VSCode[1](#user-content-fn-1-aa56f548e078749351c130450542ff17), install the official [Astro extension](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode). This helps with syntax and semantic highlighting, diagnostic messages, IntelliSense, and more.  
如果你使用VSCode [1](#user-content-fn-1-aa56f548e078749351c130450542ff17) 编译，请安装官方的Astro扩展。这有助于语法和语义突出显示、诊断消息、智能感知等。

[![The official Astro VSCode extension.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-28%20at%2011.03.36@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-28%20at%2011.03.36@2x.png)

_The official Astro VSCode extension.  
官方Astro VSCode扩展_  
  
  

Let’s now get started setting up our first Astro project. To do this, we must install Astro, and the fastest way to do this is to use the Astro automatic CLI.  
现在让我们开始设置我们的第一个Astro项目。要做到这一点，我们必须安装Astro，最快的方法是使用Astro自动CLI。

To start the install wizard, run the following command:  
要启动安装向导，请运行以下命令：

npm create astro@latest

If on `pnpm` or `yarn`, the command looks as follows:  
如果在 `pnpm` 或 `yarn` 上，命令如下所示：

# using pnpm
pnpm create astro@latest

# using yarn
yarn create astro

[![Starting a new project with the Astro CLI wizard extension.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-28%20at%2011.15.44@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-28%20at%2011.15.44@2x.png)

_Starting a new project with the Astro CLI wizard extension.  
使用Astro CLI向导扩展启动新项目。_  
  
  

This will start the wizard, which will guide us through helpful prompts. It’s important to mention that we can run this from anywhere on our machine and later choose where exactly we want the project created.  
这将启动向导，向导将引导我们完成有用的提示。值得一提的是，我们可以在机器上的任何地方运行它，然后选择我们想要创建项目的确切位置。

When asked, “Where should we create your new project?” go ahead and pass a file path. In my case, this is `documents/dev/books/understanding-astro/astro-beginner-project`.  
当被问到“我们应该在哪里创建您的新项目？“继续并传递文件路径。在我的情况下，这是 `documents/dev/books/understanding-astro/astro-beginner-project` 。

Alternatively, we could have run the `npm create astro@latest` command in our desired directory and just entered a shorter file path, e.g., `./astro-beginner-project`.  
或者，我们可以在所需的目录中运行 `npm create astro@latest` 命令，并输入一个较短的文件路径，例如，#1。

When asked, “How would you like to start your new project?” go ahead and choose “Empty”.  
当被问到“你想如何开始你的新项目？“然后选择“空”。

[![Answering the template CLI prompt.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-28%20at%2011.20.54@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-28%20at%2011.20.54@2x.png)

_Answering the template CLI prompt.  
回答模板CLI提示符。_  
  
  

We want a fresh start to explore Astro from the ground up.  
我们希望有一个新的开始，从地面上探索天文。

Now, we will be asked whether to install dependencies or not. Select yes and hit enter to continue the installation.  
现在，我们将被询问是否安装依赖项。选择是并按回车键继续安装。

[![Installing dependencies in the CLI prompt.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-28%20at%2011.22.21@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-28%20at%2011.22.21@2x.png)

_Installing dependencies in the CLI prompt.  
在CLI提示符中安装依赖项。_  
  
  

Once the dependencies are installed, answer the “Do you plan to write TypeScript?” prompt with a yes and choose the “strictest” option.  
一旦安装了依赖项，回答“你打算写TypeScript吗？”“提示“是”并选择“最严格”选项。

We want strong type safety.  
我们需要强大的类型安全。

[![Choosing Typescript in the CLI prompt.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-28%20at%2011.24.22@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-28%20at%2011.24.22@2x.png)

_Choosing Typescript in the CLI prompt.  
在CLI提示符下选择Typescript。_  
  
  

Afterwards, answer the “Initialise a new git repository?” question with whatever works for you. I’ll go with a yes here and hit enter.  
然后，回答“初始化一个新的git仓库？“问什么适合你。我会选择通过然后按回车键。

[![Initialising git in the CLI prompt.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-28%20at%2011.25.33@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-28%20at%2011.25.33@2x.png)

_Initialising git in the CLI prompt.  
在CLI提示符下初始化git。_  
  
  

And voila! Believe it or not, our new project is created and ready to go!  
瞧！信不信由你，我们的新项目已经创建并准备就绪！

Change into the directory where you set up the project. In my case, this looks like the following:  
切换到设置项目的目录。在我的例子中，它看起来像下面这样：

cd ./documents/dev/books/understanding-astro/astro-beginner-project

And then run the application via the following:  
然后通过以下方式运行应用程序：

npm run start

This will start the live application on an available local port 🚀  
这将在可用的本地端口 🚀 上启动实时应用程序

[![The basic Astro project running on localhost:3000.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-28%20at%2011.29.57@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-28%20at%2011.29.57@2x.png)

_The basic Astro project running on localhost:3000.  
运行在localhost：3000上的基本Astro项目。_  
  
  

[](#project-structure)Project structure 项目结构
--------------------------------------------

Open the newly created project in your code editor, and you’ll notice that the `create astro` CLI wizard has included some files and folders.  
在代码编辑器中打开新创建的项目，您会注意到 `create astro` CLI向导包含了一些文件和文件夹。

Astro has an opinionated folder structure. We can see some of this in our new project. By design, every Astro project will include the following in the root directory:  
Astro有一个固执己见的文件夹结构。我们可以在我们的新项目中看到这一点。根据设计，每个Astro项目将在根目录中包含以下内容：

File / Directory 文件/目录

astro.config.mjs

The Astro configuration file. This is where we provide configuration options for our Astro project.  
Astro配置文件。这是我们为Astro项目提供配置选项的地方。

tsconfig.json

A Typescript configuration file. This specifies the root files and Typescript compiler options.  
Typescript配置文件。这将指定根文件和Typescript编译器选项。

package.json

A JSON file that holds the project metadata. This is typically found at the root of most Node.js projects.  
保存项目元数据的JSON文件。这通常位于大多数Node.js项目的根目录。

public/\* 公共/\*

This directory holds files and assets that will be copied into the Astro build directory untouched, e.g., fonts, images and files such as `robots.txt`  
此目录保存将原封不动地复制到Astro构建目录中的文件和资产，例如，字体、图像和文件，如 `robots.txt`

src/\* 简体中文

The source code of our project resides here.  
我们项目的源代码就在这里。

Let’s now look at the files in our newly generated project.  
现在让我们看看新生成的项目中的文件。

### [](#tsconfigjson)tsconfig.json

The content of our `tsconfig.json` file is the following:  
我们的 `tsconfig.json` 文件的内容如下：

{
  "extends": "astro/tsconfigs/strictest"
}

The `extends` property points to the base configuration file path to inherit from, i.e., inherit the typescript configuration from the file in `astro/tsconfigs/strictest`.  
`extends` 属性指向要继承的基本配置文件路径，即，从 `astro/tsconfigs/strictest` 中的文件继承typescript配置。

Using your editor, we may navigate to the referenced path, e.g., in `vscode` by clicking on the link while holding `CMD`. This will navigate us to `node_modules/astro/tsconfigs/strictest.json`, where we’ll find a well-annotated file:  
使用您的编辑器，我们可以导航到引用的路径，例如，在 `vscode` 中，按住 `CMD` 的同时单击链接。这将引导我们到 `node_modules/astro/tsconfigs/strictest.json` ，在那里我们将找到一个注释良好的文件：

{
  ...
  "compilerOptions": {
    // Report errors for fallthrough cases in switch statements
    "noFallthroughCasesInSwitch": true,

    // Force functions designed to override their parent class to be specified as \`override\`.
    "noImplicitOverride": true,

    // Force functions to specify that they can return \`undefined\` if a possible code path does not return a value.
    "noImplicitReturns": true,
	 ...
  }
}

This is very well annotated, so we won’t spend time on this. However, the `compilerOptions` for Typescript are set in this file. The point to make here is Astro keeps a list of typescript configurations (`base`, `strict` and `strictest`) that our project leverage when we initialise via the CLI wizard.  
这是非常好的注释，所以我们不会花时间在这上面。但是，在此文件中设置了Typescript的 `compilerOptions` 。这里要说明的一点是，Astro保留了一个类型脚本配置列表（ `base` 、 `strict` 和 `strictest` ），当我们通过CLI向导进行初始化时，我们的项目可以利用这些列表。

In this example, we’ll leave the `tsconfig.json` file as is. Typescript (and consequently the `tsconfig.json` file is optional in Astro projects. However, I strongly recommend you leverage Typescript. We’ll do so all through the book.  
在本例中，我们将保留 `tsconfig.json` 文件。Typescript（因此 `tsconfig.json` 文件在Astro项目中是可选的。但是，我强烈建议您使用Typescript。我们会在整本书中这样做。

### [](#packagejson)package.json

The `package.json` file is easy to reason about. It holds metadata about our project and includes scripts for managing our Astro project, e.g., `npm start`, `npm run build`, and `npm preview`.  
`package.json` 文件很容易推理。它保存有关我们项目的元数据，并包括用于管理我们Astro项目的脚本，例如， `npm start` ， `npm run build` ， `npm preview` 。

### [](#package-lockjson)package-lock.json

The `package-lock.json` file is an autogenerated file that holds information on the dependencies/packages for our project. We won’t be touching this file manually. Instead, it is automatically generated (and updated) by npm.  
`package-lock.json` 文件是一个自动生成的文件，它保存了我们项目的依赖项/包的信息。我们不会手动处理这个文件。相反，它由npm自动生成（和更新）。

> A project’s lock file may differ depending on the package manager, e.g., yarn or pnpm.  
> 项目的锁文件可能因包管理器而异，例如，纱线或PNPM。

### [](#astroconfigmjs)astro.config.mjs

Most frameworks define a way for us to specify our project-specific configurations. For example, Astro achieves this via the `astro.config` file.  
大多数框架都定义了一种方法，让我们指定特定于项目的配置。例如，Astro通过 `astro.config` 文件实现了这一点。

import { defineConfig } from "astro/config";

export default defineConfig({});

At the moment, it defines an empty configuration. So we’ll leave it as is. However, this is the right place to specify different build and server options, for example.  
此时，它定义了一个空的配置。所以我们就这样吧。但是，这是指定不同的构建和服务器选项的正确位置。

### [](#srcenvdts)src/env.d.ts

`d.ts` files are called type declaration files[2](#user-content-fn-2-aa56f548e078749351c130450542ff17). Yes, that’s for Typescript alone, and they exist for one purpose: to describe the shape of some existing module. The information in this file is used for type checking by Typescript.  
`d.ts` 文件被称为类型声明文件 [2](#user-content-fn-2-aa56f548e078749351c130450542ff17) 。是的，那是仅针对Typescript的，它们存在的目的只有一个：来描述一些现有模块的形状。此文件中的信息用于Typescript的类型检查。

/// <reference types="astro/client" />

The content of the file points to `astro/client`. This is essentially a reference to another declaration file at `astro/client.d.ts`  
文件的内容指向 `astro/client` 。这本质上是对另一个声明文件的引用，位于 `astro/client.d.ts`

### [](#srcpagesindexastro)src/pages/index.astro

As mentioned earlier, the `src` folder is where the source code for our project resides. But what’s the `pages` directory, and why’s there an `index.astro` file?  
如前所述， `src` 文件夹是我们项目的源代码所在的位置。但是 `pages` 目录是什么，为什么有一个 `index.astro` 文件？

First, consider the contents of the `index.astro` file:  
首先，考虑 `index.astro` 文件的内容：

\--\-
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
    <h1\>Astro</h1\>
  </body\>
</html\>

You’d notice that it looks remarkably similar to standard HTML, with some exceptions.  
您会注意到它看起来与标准HTML非常相似，但有一些例外。

Also, notice what’s written within the `<body>` tag. An `<h1>` element with the text `Astro`.  
另外，请注意 `<body>` 标记中所写的内容。带有文本 `Astro` 的 `<h1>` 元素。

If we visit the running application in the browser, we have the `<h1>` rendered.  
如果我们在浏览器中访问正在运行的应用程序，我们会呈现 `<h1>` 。

[![The rendered page heading.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-11%20at%2014.18.20@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-11%20at%2014.18.20@2x.png)

_The rendered page heading.  
呈现的页标题。_  
  
  

Now change the text to read `<h1>Hello world</h1>` and notice how the page is updated in the browser!  
现在将文本更改为 `<h1>Hello world</h1>` ，并注意页面在浏览器中是如何更新的！

[![The updated page heading.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-11%20at%2014.19.41@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-11%20at%2014.19.41@2x.png)

_The updated page heading.  
更新的页面标题。_  
  
  

This leads us nicely to discuss pages in Astro — what I consider the entry point to our application.  
这让我们很好地讨论了Astro中的页面--我认为这是我们应用程序的入口点。

[](#introduction-to-astro-pages)Introduction to Astro pages  
Astro介绍页面
-----------------------------------------------------------------------

Astro leverages a file-based routing system and achieves this by using the files in the `src/pages` directory.  
Astro利用基于文件的路由系统，并通过使用 `src/pages` 目录中的文件来实现这一点。

For example, the `src/pages/index.astro` file corresponds to the `index` page served in the browser.  
例如， `src/pages/index.astro` 文件对应于浏览器中提供的 `index` 页面。

[![The project’s index page.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-29%20at%2009.49.26@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-29%20at%2009.49.26@2x.png)

_The project’s index page.  
项目的索引页。_  
  
  

Let’s go ahead and create an `src/pages/about.astro` page with similar content to `index.astro` as shown below:  
让我们继续创建一个与 `index.astro` 内容相似的 `src/pages/about.astro` 页面，如下所示：

// 📂 src/pages/about.astro
\--\-
\--\-

<html lang\="en"\>
  <head\>
    <meta charset\="utf-8" /\>
    <link rel\="icon" type\="image/svg+xml" href\="/favicon.svg" /\>
    <meta name\="viewport" content\="width=device-width" /\>
    <meta name\="generator" content\={Astro.generator} /\>
    <title\>About us</title\>
  </head\>
  <body\>
    <h1\>About us</h1\>
  </body\>
</html\>

*   Copy and paste the exact content of `index.astro` in `about.astro`.  
    将 `index.astro` 的确切内容复制并粘贴到 `about.astro` 中。
*   Change the `<h1>` to have the text `About us`.  
    将 `<h1>` 更改为文本 `About us` 。

Now, if we navigate to `/about` in the browser, we should have the new page rendered.  
现在，如果我们在浏览器中导航到 `/about` ，我们应该已经呈现了新页面。

[![The “About us” page.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-29%20at%2009.50.13@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-29%20at%2009.50.13@2x.png)

_The “About us” page.  
关于我们页面_  
  
  

### [](#what-makes-a-valid-astro-page)What makes a valid Astro page?  
什么是有效的Astro页面？

We’ve defined Astro pages as files in the `src/pages/`directory. Unfortunately, this is only partly correct.  
我们将Astro页面定义为 `src/pages/` 目录中的文件。不幸的是，这只是部分正确。

For example, if we duplicate the `favicon.svg` file in `public/favicon.svg` into the `pages` directory, does this represent a `favicon` page?  
例如，如果我们将 `public/favicon.svg` 中的 `favicon.svg` 文件复制到 `pages` 目录中，这是否表示 `favicon` 页面？

[![Duplicating the favicon in the pages directory.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-29%20at%2009.55.21.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-29%20at%2009.55.21.png)

_Duplicating the favicon in the pages directory.  
复制pages目录中的favicon。_  
  
  

Even though `index.astro` and `about.astro` correspond to our website’s index and about pages, `/favicon` will return a `404: Not found` error.  
即使 `index.astro` 和 `about.astro` 对应于我们网站的索引和关于页面， `/favicon` 也会返回 `404: Not found` 错误。

[![The /favicon route.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-29%20at%2009.56.51@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-29%20at%2009.56.51@2x.png)

_The /favicon route. /favicon路由。_  
  
  

This is because only specific files make a valid astro page. For example, if we consider the `index` and `about` files in the `pages` directory, you perhaps notice something: they both have the `.astro` file ending!  
这是因为只有特定的文件才能构成有效的astro页面。例如，如果我们考虑 `pages` 目录中的 `index` 和 `about` 文件，您可能会注意到一些事情：#3 ##

In layperson’s terms, these are Astro files, but a more technical terminology for these is Astro components.  
在外行的术语中，这些是Astro文件，但这些文件的一个更专业的术语是Astro组件。

So, quick quiz: what is an Astro component?  
快速问答：什么是Astro组件？

That’s easy—a file with the `.astro` ending.  
这很简单-一个以 `.astro` 结尾的文件。

10 points to you! Well done.  
给你10分！干得好

* * *

[](#anatomy-of-an-astro-component)Anatomy of an Astro component  
Astro组件的解剖结构
------------------------------------------------------------------------------

We’ve established that `index.astro` and `about.astro` represent Astro components and are valid Astro pages.  
我们已经确定 `index.astro` 和 `about.astro` 代表Astro组件，并且是有效的Astro页面。

Now, let’s dig into the content of these files.  
现在，让我们深入了解这些文件的内容。

Consider the contents of the `index.astro` page:  
考虑 `index.astro` 页的内容：

// 📂 src/pages/index.astro
\--\-
\--\-

<html lang\="en"\>
  <!\-- removed for brevity \--\>

</html\>

Notice the distinction between the two parts of this file’s content.  
请注意此文件内容的两个部分之间的区别。

The section at the bottom contains the page’s markup:  
底部的部分包含页面的标记：

// 📂 src/pages/index.astro
// ...
<html lang\="en"\>
  <!\-- removed for brevity \--\>
</html\>

This part is called the **component template** section.  
此部分称为组件模板部分。

While the top section contains a rather strange divider-looking syntax:  
虽然顶部部分包含了一个相当奇怪的分隔符外观的语法：

\--\-
\--\-

This part is called the **component script** section, and the `---` is called fence.  
这部分称为组件脚本部分， `---` 称为围栏。

Together, these make up an Astro component.  
它们一起构成了Astro组件。

Let’s take the component script section for a spin.  
让我们来看看组件脚本部分。

The section’s name hints at what this section of the component does. Within the component script code fence, we may declare variables, import packages and fully take advantage of Javascript or Typescript.  
该部分的名称暗示了组件的这一部分的功能。在组件脚本代码围栏中，我们可以声明变量，导入包，并充分利用JavaScript或Typescript。

Oh yes, Typescript! 是的，Typescript！

Let’s start by creating a variable to hold our user’s profile picture, as shown below:  
让我们首先创建一个变量来保存用户的个人资料图片，如下所示：

// 📂 src/pages/index.astro
\--\-
const profilePicture \= "https://i.imgur.com/JPGFE75.jpg";
\--\-

We may then take advantage of the component template section to reference this image as shown below:  
然后，我们可以利用组件模板部分来引用此图像，如下所示：

// 📂 src/pages/index.astro
\--\-
const profilePicture \= "https://i.imgur.com/JPGFE75.jpg";
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
    <!\-- 👀 Look here  \--\>
    <img
      src\={profilePicture}
      alt\="Frau Katerina's headshot."
      width\="100px"
      height\="100px"
    /\>
  </body\>
</html\>

Note that the `profilePicture` variable is referenced using curly braces `{ }`. This is how to reference variables from the component script in the component markup.  
请注意，使用花括号 `{ }` 引用 `profilePicture` 变量。这是如何在组件标记中引用组件脚本中的变量。

Now we should have the image rendered on the home page:  
现在我们应该在主页上呈现图像：

[![Rendering the user profile photo.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-04-29%20at%2010.30.54@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-04-29%20at%2010.30.54@2x.png)

_Rendering the user profile photo.  
正在渲染用户配置文件照片。_  
  
  

It’s not much, but it’s honest work, eh?  
不多，但这是诚实的工作，嗯？

Let’s go ahead and flesh out the page to have the user’s profile markup:  
让我们继续，充实页面以获得用户的配置文件标记：

// 📂 src/pages/index.astro
// ...
  <body\>
    <!\-- Look here 👀 \--\>
    <div\>
      <img
        src\={profilePicture}
        alt\="Frau Katerina's headshot."
        width\="100px"
        height\="100px"
      /\>
      <div\>
        <h1\>Frau Katerina</h1\>
        <h2\>VP of Engineering at Goooogle</h2\>
        <p\>
          Helping developers be excellent and succeed at building scalable
          products
        </p\>
      </div\>
    </div\>
  </body\>
// ...

As you might have noticed, we’re writing `HTML` looking syntax in the component markup section!  
您可能已经注意到了，我们正在组件标记部分编写 `HTML` 外观语法！

Now we should have the user photo and their bio rendered in the browser as follows:  
现在，我们应该在浏览器中渲染用户照片和他们的个人信息，如下所示：

[![The user profile photo and bio.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-10%20at%2014.07.31@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-10%20at%2014.07.31@2x.png)

[](#component-styles)Component styles 组件样式
------------------------------------------

Styling in Astro is relatively easy to reason about. Add a `<style>` tag to a component, and Astro will automatically handle its styling.  
Astro中的造型相对容易推理。向组件添加 `<style>` 标签，Astro将自动处理其样式。

While it’s possible to select elements directly, let’s go ahead and add classes to the component markup for ease:  
虽然可以直接选择元素，但为了方便起见，让我们继续向组件标记添加类：

// 📂 src/pages/index.astro
// ...
<div class\="profile"\>
    <img
      src\={profilePicture}
      class\="profile\_\_picture"
      {/\*\* ... \*\*/}
    /\>
    <div class\="profile\_\_details"\>
      <h1\>Frau Katerina</h1\>
      {/\*\* ... \*\*/}
    </div\>
</div\>
// ...

Add a `<style>` tag, and write CSS as usual!  
添加一个 `<style>` 标签，然后像往常一样编写CSS！

// ...
<style\>
  .profile {
    display: flex;
    align\-items: flex\-start;
    flex\-wrap: wrap;
    padding: 1rem 0 3rem 0;
  }

  .profile\_\_details {
    flex: 1 0 300px;
  }

  .profile\_\_details \> h1 {
    margin\-top: 0;
  }

  .profile\_\_picture {
    border\-radius: 50%;
    margin: 0 2rem 1rem 0;
  }
</style\>

The user details should now be styled as expected.  
现在，用户详细信息的样式应该符合预期。

[![Applying styles to the index.astro page component.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-01%20at%2008.42.27@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-01%20at%2008.42.27@2x.png)

_Applying styles to the index.astro page component.  
将样式应用于index.astro页面组件。_  
  
  

If we inspect the eventual styles applied to our UI elements via the browser developer tools, we’ll notice that the style selectors look different.  
如果我们通过浏览器开发工具检查应用于UI元素的最终样式，我们会注意到样式选择器看起来不同。

For example, to style the user name, we’ve written the following CSS:  
例如，为了设置用户名的样式，我们编写了以下CSS：

.profile\_\_details \> h1 {
  margin\-top: 0;
}

However, what’s applied in the browser looks something like this:  
然而，在浏览器中应用的内容看起来像这样：

.profile\_\_details:where(.astro\-J7PV25F6) \> h1:where(.astro\-J7PV25F6) {
  margin\-top: 0;
}

Why is this? 为什么会这样呢？

The actual style declarations for the `h1` element remain unchanged. The only difference here is the selector.  
`h1` 元素的实际样式声明保持不变。这里唯一的区别是选择器。

The `h1` element now has auto-generated class names, and the selector is now scoped via the `:where` CSS selector.  
`h1` 元素现在有自动生成的类名，选择器现在通过 `:where` CSS选择器进行作用域控制。

This is done internally by Astro. This makes sure the styles we write don’t leak beyond our component; for example, if we styled every `h1` in our component as follows:  
这是由Astro内部完成的。这可以确保我们编写的样式不会泄漏到组件之外;例如，如果我们将组件中的每个 `h1` 样式化如下：

h1 {
  color: red;
}

The eventual style applied in the browser will be similar to the following:  
浏览器中应用的最终样式将类似于以下内容：

h1:where(.astro-some-unique-id) {
  color: red;
}

This will ensure all other `h1` in our project remains the same, and this style only applies to our specific component `h1`.  
这将确保我们项目中的所有其他 `h1` 保持不变，并且这种风格仅适用于我们的特定组件 `h1` 。

[](#page-layouts)Page layouts 页面布局
----------------------------------

Please look at the pages of our completed application, and realise how they all have identical forms.  
请看我们填写的申请表，并意识到它们都有相同的表格。

[![A breakdown of the application page structure.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-01%20at%2009.10.55.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-01%20at%2009.10.55.png)

_A breakdown of the application page structure.  
应用程序页面结构的细分。_  
  
  

There’s a navigation bar, a footer, and some container that holds the page’s main content.  
有一个导航栏、一个页脚和一些保存页面主要内容的容器。

Should we repeat these similar UI structures across all pages?  
我们是否应该在所有页面上重复这些类似的UI结构？

Most people will answer “No”. So, is there a way to share reusable UI structures across pages?  
大多数人会回答“不”。那么，有没有一种方法可以跨页面共享可重用的UI结构呢？

Yes, yes, yes! This is where layouts come in.  
是的是的是的这就是布局的用武之地。

Layouts are Astro components with a twist. They are used to provide reusable UI structures across pages, e.g., navigation bars and footers.  
布局是天文组件与扭曲。它们用于提供跨页面的可重用UI结构，例如，导航栏和页脚。

Conventionally, layouts are placed in the `src/layouts` directory. This is not compulsory but a widespread pattern.  
通常，布局被放置在 `src/layouts` 目录中。这不是强制性的，而是一种普遍的模式。

Let’s go ahead and create our first layout in `src/layouts/Main`. We’ll do this by moving away all the reusable UI structures currently in `index.astro` as follows:  
让我们继续在 `src/layouts/Main` 中创建第一个布局。我们将通过移除当前在 `index.astro` 中的所有可重用UI结构来做到这一点，如下所示：

// 📂 src/layouts/Main.astro
\--\-
\--\-

<html lang\="en"\>
  <head\>
    <meta charset\="utf-8" /\>
    <link rel\="icon" type\="image/svg+xml" href\="/favicon.svg" /\>
    <meta name\="viewport" content\="width=device-width" /\>
    <meta name\="generator" content\={Astro.generator} /\>
    {/\* Add a new meta description tag \*/}
    <meta name\="description" content\="Frau Katarina's website" /\>
    {/\* Title is hardcoded as Astro, for now. \*/}
    <title\>Astro</title\>
  </head\>
  <body\>
    <main\>
      {/\* We want the content of each page to go here \*/}
    </main\>
  </body\>
</html\>

*   We’ve moved the `<html>`, `<head>` and `<body>` elements to the `Main.astro` layout.  
    我们将 `<html>` 、 `<head>` 和 `<body>` 元素移到了 `Main.astro` 布局。
*   We’ve also introduced a new `<meta name=description />` tag for SEO.  
    我们还为SEO引入了一个新的 `<meta name=description />` 标签。
*   We’ve equally introduced a `<main>` element where we want the rest of our page to go in.  
    我们同样引入了一个 `<main>` 元素，我们希望页面的其余部分都可以进入其中。
*   Note that the file name of the layout is capitalised, i.e., `Main.astro`, not `main.astro`.  
    注意，布局的文件名大写，即， `Main.astro` 不是 `main.astro`

On the one hand, layouts are unique because they mostly do one thing - provide reusable structures. But, on the other hand, they aren’t unique. They are like other Astro components and can do everything a component can!  
一方面，布局是独特的，因为它们主要做一件事-提供可重用的结构。但另一方面，它们并不是独一无二的。它们就像其他Astro组件一样，可以做组件所能做的一切！

[](#rendering-components-and-slots)Rendering components and slots  
渲染组件和插槽
---------------------------------------------------------------------------

Rendering an Astro component is similar to how you’d attempt to render an HTML element, e.g., we’d render a div by writing the following:  
呈现Astro组件类似于尝试呈现HTML元素的方式，例如我们会通过编写以下内容来渲染div：

<div\>render something within the div</div\>

The same goes for Astro components.  
Astro组件也是如此。

To render the `Main.astro` component, we’d do similar:  
为了渲染 `Main.astro` 组件，我们会做类似的事情：

<Main\>render something within the Main component</Main\>

Let’s put this into practice. We may now use the `Main` layout in the `index.astro` page. To do this, we will do the following:  
让我们把这个付诸实践。我们现在可以在 `index.astro` 页面中使用 `Main` 布局。为此，我们将执行以下操作：

*   Import the `Main` layout from `"../layouts/Main.astro"`  
    从 `"../layouts/Main.astro"` 导入 `Main` 布局
*   Substitute the `<html>`, `<head>` and `<body>` elements for the `<Main>` layout in `index.astro`.  
    将 `<html>` 、 `<head>` 和 `<body>` 元素替换为 `index.astro` 中的 `<Main>` 布局。

\--\-
import Main from "../layouts/Main.astro";

const profilePicture \= "https://i.imgur.com/JPGFE75.jpg";
\--\-

<Main\>
  <div class\="profile"\>
    <img
      src\={profilePicture}
      class\="profile\_\_picture"
      alt\="Frau Katerina's headshot."
      width\="100px"
      height\="100px"
    /\>
    <div class\="profile\_\_details"\>
      <h1\>Frau Katerina</h1\>
      <h2\>VP of Engineering at Goooogle</h2\>
      <p\>
        Helping developers be excellent and succeed at building scalable
        products
      </p\>
    </div\>
  </div\>
</Main\>

If we checked our app, we’d have a blank `index` page.  
如果我们检查我们的应用程序，我们会有一个空白的 `index` 页面。

[![Blank application page.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-10%20at%2017.18.07.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-10%20at%2017.18.07.png)

_Blank application page. 空白申请页。_  
  
  

Why’s that? 为什么会这样？

Unlike HTML elements, the child elements in the `<Main>` tag aren’t automatically rendered.  
与HTML元素不同， `<Main>` 标签中的子元素不会自动呈现。

{/\*\* Child div will not be automatically rendered \*/}
<Main\>
  <div\>Hello from child</div\>
<Main\>

The `<Main>` layout component is rendered, and nothing else. The child components aren’t. Hence, the empty page.  
渲染 `<Main>` 布局组件，除此之外什么也不渲染。子组件则不是。因此，空白页面。

To render the child elements of an Astro component, we must specify where to render these using a `<slot />` element.  
要渲染Astro组件的子元素，我们必须使用 `<slot />` 元素指定渲染位置。

[![Injecting child elements into a slot.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/a.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/a.png)

_Injecting child elements into a slot.  
将子元素注入到插槽中。_  
  
  

Let’s add a `<slot>` within `Main.astro` :  
让我们在 `Main.astro` 中添加一个 `<slot>` ：

//...
<body\>
  <main\>
    {/\* We want the content of each page to go here \*/}
    <slot /\>
  </main\>
</body\>

[![Page refactored to use a reusable layout component.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-10%20at%2017.19.59.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-10%20at%2017.19.59.png)

_Page refactored to use a reusable layout component.  
页面重构以使用可重用的布局组件。_  
  
  

We should now have our page rendered with the reusable layout in place.  
我们现在应该用可重用布局呈现页面了。

[](#capitalising-component-names)Capitalising component names  
大写组件名称
----------------------------------------------------------------------

We’ve capitalised the file name of the `Main.astro` layout component but is this important?  
我们已经将 `Main.astro` 布局组件的文件名大写，但这重要吗？

Theoretically, the answer to that is no.  
理论上，答案是否定的。

We could create a file with a lower cased name, e.g., `mainLayout.astro` and import the component as follows:  
我们可以创建一个小写的文件名，例如， `mainLayout.astro` 并按如下方式导入组件：

import Main from "../layouts/mainLayout.astro";

This is perfectly correct.  
这是完全正确的。

However, where we encounter issues is if we name the imported component with a lowercase:  
但是，如果我们用小写字母命名导入的组件，就会遇到问题：

// main NOT Main
import main from "../layouts/mainLayout.astro";

In this case, we’ll encounter issues when we attempt to render the component as the name collides with the standard HTML `main` element.  
在本例中，当我们试图呈现组件时，会遇到问题，因为组件名称与标准HTML `main` 元素冲突。

For this reason, it’s common practice to capitalise both component file names and the imported variable name.  
因此，通常的做法是将组件文件名和导入的变量名大写。

[](#the-global-style-directive)The global style directive  
全局样式指令
------------------------------------------------------------------

The `Main` layout is in place but doesn’t add much to our page. Let’s start by adding some styles for the headers and also centre the page’s content:  
`Main` 布局已经到位，但并没有为我们的页面添加太多内容。让我们首先为标题添加一些样式，并将页面的内容居中：

<!-- 📂 src/layouts/Main.astro -->
<style\>
  h1 {
    font-size: 3rem;
    line-height: 1;
  }

  h1 + h2 {
    font-size: 1.1rem;
    margin-top: \-1.4rem;
    opacity: 0.9;
    font-weight: 400;
  }

  main {
    max-width: 40rem;
    margin: auto;
  }
</style\>

With this, we’ll have the `main` element centred, but the headers, `h1` and `h2` remain unstyled.  
这样，我们将以 `main` 元素为中心，但标题 `h1` 和 `h2` 保持未样式化。

[![A comparison of the changes before and after the layout component style.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-10%20at%2017.21.33.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-10%20at%2017.21.33.png)

_A comparison of the changes before and after the layout component style.  
布局构件样式前后的更改比较。_  
  
  

This is because styles applied via the `<style>` tag are locally scoped by default.  
这是因为通过 `<style>` 标记应用的样式默认情况下是本地范围的。

Can you tell me why?  
你能告诉我为什么吗？

The `main` element resides in the `Main` layout. However, the header `h1` and `h2` exist in a different `index.astro` component!  
`main` 元素位于 `Main` 布局中。然而，头 `h1` 和 `h2` 存在于不同的 `index.astro` 组件中！

For our use case, we need global styles.  
对于我们的用例，我们需要全局样式。

We need to break out of the default locally scoped styles the Astro component provides, but how do we do this?  
我们需要打破Astro组件提供的默认本地范围样式，但是我们如何做到这一点呢？

Global styles can be a nightmare — except when truly needed. For such cases, Astro provides several solutions. The first is using what’s known as a global style template directive.  
全局样式可能是一场噩梦--除非真正需要。对于这种情况，Astro提供了几种解决方案。第一种是使用所谓的全局样式模板指令。

I know that sounds like a mouthful! However, in simple terms, template directives in Astro are different kinds of HTML attributes that can be used in Astro component templates[3](#user-content-fn-3-aa56f548e078749351c130450542ff17).  
我知道这听起来很拗口！然而，简单地说，Astro中的模板指令是可以在Astro组件模板 [3](#user-content-fn-3-aa56f548e078749351c130450542ff17) 中使用的不同类型的HTML属性。

For example, to break out of the default locally scoped `<style>` behaviour, we can add a `is:global` attribute as shown below:  
例如，为了打破默认的本地作用域 `<style>` 行为，我们可以添加一个 `is:global` 属性，如下所示：

<style is:global\>
  ...;
</style\>

This will remove the local CSS scoping and make the styles available globally.  
这将删除本地CSS范围，并使样式在全局可用。

[![The page with global fonts and styles.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-01%20at%2011.06.50.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-01%20at%2011.06.50.png)

_The page with global fonts and styles.  
具有全局字体和样式的页面。_  
  
  

[](#custom-fonts-and-global-css)Custom fonts and global CSS  
自定义字体和全局CSS
-------------------------------------------------------------------------

Base layout components like `Main.astro` are a great place to have global properties such as global styles and custom fonts.  
像 `Main.astro` 这样的基本布局组件是拥有全局属性（如全局样式和自定义字体）的好地方。

We’ve added global styles via the `is:global` template directive, but alternatively, we could have all global styles imported into `Main.astro` from a `global.css` file.  
我们已经通过 `is:global` template指令添加了全局样式，但是，我们也可以将所有全局样式从 `global.css` 文件导入到 `Main.astro` 中。

In cases where a project requires importing some existing global css file, this is the more straightforward approach.  
在项目需要导入一些现有的全局css文件的情况下，这是更直接的方法。

For example, let’s refactor our project to use `global.css`. To do so, move the entire CSS content within the `<style is:global>` element into `src/styles/global.css`. Then import the styles in the `Main.astro` component frontmatter:  
例如，让我们重构我们的项目以使用 `global.css` 。为此，将 `<style is:global>` 元素中的整个CSS内容移动到 `src/styles/global.css` 中。然后导入 `Main.astro` 组件frontmatter中的样式：

// 📂 src/layouts/Main.astro
\--\-
import "../styles/global.css";
\--\-

This will load and inject style onto the page.  
这将加载样式并将其注入到页面中。

Now, let’s turn our attention to global fonts.  
现在，让我们将注意力转向全局字体。

We will use the Google [Inter](https://fonts.google.com/specimen/Inter) font for the project, but how do we do this?  
我们将在项目中使用Google Inter字体，但我们如何做到这一点呢？

Technically speaking, to add Inter to our project, we must add the `<link>`s to Inter on every page required.  
从技术上讲，要将国际米兰添加到我们的项目中，我们必须在所需的每个页面上添加国际米兰的 `<link>` 。

However, instead of repeating ourselves on every page, we can leverage the shared `Main.astro` layout component.  
然而，我们可以利用共享的 `Main.astro` 布局组件，而不是在每个页面上重复自己。

Go ahead and add the `<link>`s to the Inter font as shown below:  
继续并将 `<link>` s添加到Inter字体中，如下所示：

// 📂 src/layouts/Main.astro
<html lang\="en"\>
  <head\>
    {/\*\* 👀 Look here ... \*/}
    <link rel\="preconnect" href\="https://fonts.googleapis.com" /\>
    <link rel\="preconnect" href\="https://fonts.gstatic.com" crossorigin /\>
    <link
      href\="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap"
      rel\="stylesheet"
    /\>
  </head\>
  {/\*\* ... \*/}
</html\>

We may now update the `global.css` file to use the new font family:  
我们现在可以更新 `global.css` 文件以使用新的字体系列：

body {
  font-family: "Inter", sans-serif;
  padding: 0 0.5rem; /\* Additional body style \*/
}

And boom! We have sorted global fonts.  
砰！我们对全局字体进行了排序。

[![The page with global fonts and styles.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-10%20at%2017.41.13.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-10%20at%2017.41.13.png)

_The page with global fonts and styles.  
具有全局字体和样式的页面。_  
  
  

[](#independent-astro-components)Independent Astro components  
独立Astro组件
-------------------------------------------------------------------------

We’ve discussed two special types of Astro components: layouts and pages.  
我们已经讨论了两种特殊类型的Astro组件：布局和页面。

However, a working site is made up of more than just layouts and pages. For example, different blocks of user interfaces are typically embedded within a page. These independent and reusable blocks of user interfaces can also be represented using Astro components.  
然而，一个工作站点不仅仅是由布局和页面组成的。例如，用户界面的不同块通常嵌入在页面内。这些独立和可重用的用户界面块也可以使用Astro组件表示。

Let’s put this to practice by creating `NavigationBar` and `Footer` components to be used in the `Main.astro` layout.  
让我们通过创建要在 `Main.astro` 布局中使用的 `NavigationBar` 和 `Footer` 组件来实践这一点。

When creating components, a standard convention is to have them in the `src/components` directory. Let’s go ahead and create one.  
创建组件时，标准约定是将它们放在 `src/components` 目录中。让我们继续并创建一个。

// 📂 src/components/Footer.astro
<footer\>&copy; Frau Katerina</footer\>

<style\>
  footer {
    /\* Applies top and bottom paddings \*/
    padding: 3rem 0;
    /\* Centers the text content \*/
    text\-align: center;
    /\* Makes the font smaller \*/
    font\-size: 0.9rem;
  }
</style\>

Let’s also create a `NavigationBar` component:  
让我们创建一个 `NavigationBar` 组件：

// 📂 src/components/NavigationBar.astro
\--\-
\--\-

<nav\>
  <ul\>
    <li\>
      <a href\="/"\>Home</a\>
    </li\>

    <li\>
      {/\*\* Link points nowhere for now\*/}
      <a href\="#"\>Philosophies</a\>
    </li\>

    <li\>
      {/\*\* Link points nowhere for now\*/}
      <a href\="#"\>Beyond technology</a\>
    </li\>
  </ul\>
</nav\>

<style\>
  nav {
    display: flex;
    align\-items: flex\-start;
    padding: 2rem 0;
  }

  ul {
    display: flex;
    flex\-wrap: wrap;
    padding: 0;
    margin: 0 auto 0 0;
  }

  nav li {
    opacity: 0.8;
    list\-style: none;
    font\-size: 0.95rem;
  }

  a {
    padding: 0.5rem 1rem;
    border\-radius: 10px;
    text\-decoration: none;
  }
</style\>

Now render the `NavigationBar` and `Footer` as shown below:  
现在渲染 `NavigationBar` 和 `Footer` ，如下所示：

// 📂 src/layouts/Main.astro
\--\-
//...
import Footer from "../components/Footer.astro";
import NavigationBar from "../components/NavigationBar.astro";
\--\-

{/\*\* ... \*\*/}
<main\>
  <NavigationBar /\>

  <slot /\>

  <Footer /\>
</main>

[![Navigation bar and footer rendered.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-01%20at%2015.17.48@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-01%20at%2015.17.48@2x.png)

_Navigation bar and footer rendered.  
导航栏和页脚呈现。_  
  
  

[](#adding-interactive-scripts)Adding interactive scripts  
添加交互式脚本
-------------------------------------------------------------------

An integral part of Astro’s philosophy is shipping zero Javascript by default to the browser.  
Astro哲学的一个组成部分是默认情况下向浏览器发送零JavaScript。

This means our pages get compiled into `HTML` pages with all Javascript stripped away by default.  
这意味着我们的页面被编译成 `HTML` 页面，默认情况下所有JavaScript都被剥离。

You might ask, what about all the Javascript written in the component script section of an Astro component?  
您可能会问，在Astro组件的组件脚本部分中编写的所有JavaScript是什么？

The component script and markup will be used to generate the eventual `HTML` page(s) sent to the browser.  
组件脚本和标记将用于生成发送到浏览器的最终 `HTML` 页。

For example, go ahead and add a simple `console.log` to the frontmatter of the `index.astro` page:  
例如，继续并添加一个简单的 `console.log` 到 `index.astro` 页面的frontmatter：

// 📂 src/pages/index.astro
\--\-
console.log("Hello world!");
\--\-

Inspect the browser console and notice how the log never makes it to the browser!  
检查浏览器控制台并注意日志是如何从未到达浏览器的！

So, where’s the log?  
所以，日志在哪？

Astro runs on the server. In our case, this represents our local development server. So, the `console.log` will appear in the terminal where Astro serves our local application.  
Astro在服务器上运行。在我们的例子中，这代表我们的本地开发服务器。因此， `console.log` 将出现在Astro为本地应用程序提供服务的终端中。

[![Astro server logs.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-01%20at%2017.55.33.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-01%20at%2017.55.33.png)

_Astro server logs. 天文服务器日志。_  
  
  

When we eventually build our application for production with `npm run build`, Astro will output `HTML` files corresponding to our pages in `src/pages`.  
当我们最终使用 `npm run build` 构建应用程序用于生产时，Astro将输出与 `src/pages` 中的页面相对应的 `HTML` 文件。

In this example, the `Hello world!` message will be logged but not get into the compiled `HTML` pages.  
在本例中， `Hello world!` 消息将被记录，但不会进入编译的 `HTML` 页面。

[![Logs during building the production application.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-01%20at%2018.02.53.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-01%20at%2018.02.53.png)

_Logs during building the production application.  
生成生产应用程序期间的日志。_  
  
  

To add interactive scripts, i.e., scripts that make it into the final `HTML` page build output, add a `<script>` element in the component markup section.  
添加交互式脚本，即脚本，使其成为最终的 `HTML` 页面构建输出，在组件标记部分添加 `<script>` 元素。

For example, let’s move the `console.log` from the frontmatter to the markup via a `<script>` element:  
例如，让我们通过一个 `<script>` 元素将 `console.log` 从frontmatter移动到标记：

// 📂 src/pages/index.astro
\--\-
\--\-
// ...

<script\>
  console.log("Hello world!");
</script\>

We should have `Hello world!` logged in the browser console!  
我们应该有 `Hello world!` 登录浏览器控制台！

[![The browser “Hello world” log.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-01%20at%2018.07.13@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-01%20at%2018.07.13@2x.png)

_The browser “Hello world” log.  
浏览器“Hello world”日志。_  
  
  

[](#interactive-theme-toggle)Interactive theme toggle  
交互式主题切换
---------------------------------------------------------------

Let’s put our newly found knowledge of client-side scripts to good use.  
让我们充分利用我们新发现的客户端脚本知识。

Create a new `ThemeToggler.astro` component in the `src/components` directory.  
在 `src/components` 目录中创建新的 `ThemeToggler.astro` 组件。

Add the following markup:  
添加以下标记：

// 📂 src/components/ThemeToggler.astro
<button aria-label\="Theme toggler"\>
  <svg width\="25px" xmlns\="http://www.w3.org/2000/svg" viewBox\="0 0 24 24"\>
    <path
      class\="sun"
      fill-rule\="evenodd"
      d\="M12 17.5a5.5 5.5 0 1 0 0-11 5.5 5.5 0 0 0 0 11zm0 1.5a7 7 0 1 0 0-14 7 7 0 0 0 0 14zm12-7a.8.8 0 0 1-.8.8h-2.4a.8.8 0 0 1 0-1.6h2.4a.8.8 0 0 1 .8.8zM4 12a.8.8 0 0 1-.8.8H.8a.8.8 0 0 1 0-1.6h2.5a.8.8 0 0 1 .8.8zm16.5-8.5a.8.8 0 0 1 0 1l-1.8 1.8a.8.8 0 0 1-1-1l1.7-1.8a.8.8 0 0 1 1 0zM6.3 17.7a.8.8 0 0 1 0 1l-1.7 1.8a.8.8 0 1 1-1-1l1.7-1.8a.8.8 0 0 1 1 0zM12 0a.8.8 0 0 1 .8.8v2.5a.8.8 0 0 1-1.6 0V.8A.8.8 0 0 1 12 0zm0 20a.8.8 0 0 1 .8.8v2.4a.8.8 0 0 1-1.6 0v-2.4a.8.8 0 0 1 .8-.8zM3.5 3.5a.8.8 0 0 1 1 0l1.8 1.8a.8.8 0 1 1-1 1L3.5 4.6a.8.8 0 0 1 0-1zm14.2 14.2a.8.8 0 0 1 1 0l1.8 1.7a.8.8 0 0 1-1 1l-1.8-1.7a.8.8 0 0 1 0-1z"
    \></path\>
    <path
      class\="moon"
      fill-rule\="evenodd"
      d\="M16.5 6A10.5 10.5 0 0 1 4.7 16.4 8.5 8.5 0 1 0 16.4 4.7l.1 1.3zm-1.7-2a9 9 0 0 1 .2 2 9 9 0 0 1-11 8.8 9.4 9.4 0 0 1-.8-.3c-.4 0-.8.3-.7.7a10 10 0 0 0 .3.8 10 10 0 0 0 9.2 6 10 10 0 0 0 4-19.2 9.7 9.7 0 0 0-.9-.3c-.3-.1-.7.3-.6.7a9 9 0 0 1 .3.8z"
    \></path\>
  </svg\>
</button\>

*   For accessibility, the button has an `aria-label` of `Theme toggler`\].  
    为了便于访问，该按钮具有 `aria-label` 或 `Theme toggler` \]。
*   The `SVG` has a fixed width of `25px`, rendering two `<path>` elements.  
    `SVG` 具有固定宽度 `25px` ，呈现两个 `<path>` 元素。
*   The first `<path>` visually represents a sun icon. The second is a moon icon.  
    第一个 `<path>` 视觉上表示太阳图标。第二个是月亮图标。
*   By default, both icons (sun and moon) are rendered. Our goal is to toggle the displayed icon based on the active theme.  
    默认情况下，会渲染两个图标（太阳和月亮）。我们的目标是根据活动主题切换显示的图标。

Then import the component and render it in the `NavigationBar`:  
然后导入组件并在 `NavigationBar` 中渲染它：

// 📂 src/components/NavigationBar
\--\-
import ThemeToggler from "./ThemeToggler.astro";
\--\-

<nav\>
  <ul\>
    {/\*\* ... \*\*/}
  </ul\>
  {/\*\* 👀 Look here \*\*/}
  <ThemeToggler /\>
</nav\>

[![The sun and moon icons rendered in the toggle button.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-02%20at%2006.43.28.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-02%20at%2006.43.28.png)

_The sun and moon icons rendered in the toggle button.  
在切换按钮中渲染的太阳和月亮图标。_  
  
  

Let’s add some `<style>` to `ThemeToggler`:  
让我们添加一些 `<style>` 到 `ThemeToggler` ：

// 📂 src/components/ThemeToggler.astro
// ...
<style\>
  button {
    cursor: pointer;
    border\-radius: 10px;
    border: 0;
    padding: 5px 10px;
    transition: all 0.2s ease\-in\-out;
  }

  button:hover {
    /\* Make the button smaller (scale down) when hovered \*/
    transform: scale(0.9);
  }

  button:active {
    /\*\* Return the button to its standard size when active \*/
    transform: scale(1);
  }

  .sun {
    /\* Hide the sun icon by default. This assumes a light theme by default \*/
    fill: transparent;
  }
</style\>

Now, we should have a decent-looking theme toggler.  
现在，我们应该有一个体面的主题切换器。

[![A styled theme toggle button](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-02%20at%2006.50.49.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-02%20at%2006.50.49.png)

_A styled theme toggle button  
一个样式化的主题切换按钮_  
  
  

[](#the-global-selector)The :global() selector ：global（）选择器
-----------------------------------------------------------

Let’s take a moment to consider the strategy we’ll use for toggling the theme.  
让我们花点时间考虑一下切换主题的策略。

We’ll toggle a CSS class on the root element whenever a user clicks the toggle.  
每当用户单击切换时，我们都会在根元素上切换CSS类。

[![Adding a new “dark” class on toggle](/understanding-astro/understanding-astro-book/raw/master/images/ch1/embed.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/embed.png)

_Adding a new “dark” class on toggle  
在切换时添加一个新的“黑暗”类_  
  
  

For example, if the user was viewing the site in light mode and clicked to toggle, we’ll add a `.dark` class to the root element and, based on that, apply dark-themed styles.  
例如，如果用户在灯光模式下查看站点并单击切换，我们将向根元素添加一个 `.dark` 类，并在此基础上应用深色主题样式。

If the user is in dark mode, clicking the toggle will remove the `.dark` class. We’ll refer to this as a class strategy for toggling dark mode.  
如果用户处于黑暗模式，单击切换将删除 `.dark` 类。我们将把它称为切换黑暗模式的类策略。

Based on this strategy, we must update our local `ThemeToggler` style to display the relevant icon depending on the global `.dark` class.  
基于这个策略，我们必须更新本地 `ThemeToggler` 样式，以显示相关图标，这取决于全局 `.dark` 类。

To do this, we will leverage the `:global` selector.  
为此，我们将利用 `:global` 选择器。

Here’s how we’d achieve this:  
下面是我们如何做到这一点：

<!-- 📂 src/components/ThemeToggler.astro -->
<style\>
  /\*\*...\*\*/

  /\*\* If a parent element has a .dark class, target the .sun icon and make the path black (shows the icon) \*/
  :global(.dark) .sun {
    fill: black;
  }

  /\*\* If a parent element has a .dark class, target the .moon icon and make the path transparent (hides the icon) \*/
  :global(.dark) .moon {
    fill: transparent;
  }
</style\>

To see this at work, inspect the page via the developer tools, and add a `dark` class to the root element. The toggle icon will be appropriately changed.  
要了解这一点，请通过开发人员工具检查页面，并向根元素添加一个 `dark` 类。切换图标将被适当更改。

[![Inspecting icon change with a root dark class](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-02%20at%2007.03.08.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-02%20at%2007.03.08.png)

_Inspecting icon change with a root dark class  
检查图标变化与根黑暗类_  
  
  

In practice, limit `:global` only to appropriate use cases because mixing global and locally scoped component styles will become challenging to debug. However, this is permissible, given our use case.  
在实践中，将 `:global` 限制在适当的用例中，因为混合全局和局部范围的组件样式将对调试造成挑战。但是，考虑到我们的用例，这是允许的。

[](#event-handling)Event Handling 事件处理
--------------------------------------

We’ve handled the styles for our toggle, assuming a `.dark` root class. Now, Let’s go ahead and handle the toggle click event with a `<script>` element.  
我们已经处理了切换的样式，假设是一个 `.dark` 根类。现在，让我们继续使用 `<script>` 元素处理切换点击事件。

<!-- 📂 src/components/ThemeToggler.astro -->
<script\>
  /\*\* Represent the toggle theme class with a variable \*/
  const DARK\_THEME\_CLASS \= "dark";

  /\*\* Grab the toggle \*/
  const toggle \= document.querySelector("button");
  /\*\* Grab the document root element. In this case <html>  \*/
  const rootEl \= document.documentElement;

  if (toggle) {
    toggle.addEventListener("click", () \=> {
      /\*\* toggle the "dark" class on the root element \*/
      rootEl.classList.toggle(DARK\_THEME\_CLASS);
    });
  }
</script\>

Notice that this is standard Javascript. Nothing fancy going on here.  
请注意，这是标准JavaScript。这里没什么特别的。

*   The toggle is selected via `document.querySelector("button")`.  
    通过 `document.querySelector("button")` 选择切换。
*   To set up an event listener, we use the `.addEventListener` method on the button.  
    要设置事件侦听器，我们在按钮上使用 `.addEventListener` 方法。
*   On clicking the button, we toggle the class list on the root element: adding or removing the “dark” class.  
    点击按钮后，我们切换根元素上的类列表：添加或移除“暗”类。

With this in place, the toggle icon changes when clicked to either that of the sun or moon.  
在此位置，切换图标在单击时会更改为太阳或月亮的图标。

Excellent! 太棒了！

[](#theming-via-css-variables)Theming via CSS variables  
通过CSS变量进行主题化
----------------------------------------------------------------------

CSS variables[4](#user-content-fn-4-aa56f548e078749351c130450542ff17) are outstanding, and we’ll leverage them for theming our application.  
CSS变量 [4](#user-content-fn-4-aa56f548e078749351c130450542ff17) 非常出色，我们将利用它们为应用程序创建主题。

Firstly, let’s go ahead and define the colour variables we’ll use in the project.  
首先，让我们继续定义我们将在项目中使用的颜色变量。

// 📂 styles/global.css
html {
  \--background: white;
  \--grey\-200: #222222;
  \--grey\-400: #444444;
  \--grey\-600: #333333;
  \--grey\-900: #111111;
}

html.dark {
  \--background: black;
  \--grey\-200: #eaeaea;
  \--grey\-400: #acacac;
  \--grey\-600: #ffffff;
  \--grey\-900: #fafafa;
}

*   Set the variables on the root `HTML` element to be globally scoped.  
    将根元素 `HTML` 上的变量设置为全局范围。
*   A CSS variable is a property that begins with two dashes, `--` e.g., `--background`.  
    CSS变量是以两个破折号开头的属性， `--` 例如，#1。
*   For simplicity, we’ll stick to the minimal grey palette above.  
    为了简单起见，我们将坚持上面最小的灰色调色板。

The first visual change we’ll make is to add the following `color` and `background` style declarations to the `body` element:  
我们要做的第一个可视化更改是将以下 `color` 和 `background` 样式声明添加到 `body` 元素：

// 📂 styles/global.css
body {
  color: var(\--grey\-600);
  background: var(\--background);
}

With this seemingly simple change, we should now have the text and background colour of the `body` react to clicking the toggle.  
通过这个看似简单的更改，我们现在应该让 `body` 的文本和背景颜色对单击切换做出反应。

[![Dark mode activated](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-02%20at%2007.51.51.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-02%20at%2007.51.51.png)

_Dark mode activated 黑暗模式启动_  
  
  

Finally, update the navigation links in `NavigationBar` to reflect theme preferences:  
最后，更新 `NavigationBar` 中的导航链接以反映主题偏好：

/\* 📂 src/components/NavigationBar.astro \*/
<style\>
  /\* ... \*/
  a {
    color: var(\--grey-400);
    padding: 0.5rem 1rem;
    border-radius: 10px;
    text-decoration: none;
  }

  a:hover {
    color: var(\--grey-900);
  }
</style\>

[![Navigation links styled for dark mode](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-02%20at%2007.55.56.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-02%20at%2007.55.56.png)

_Navigation links styled for dark mode  
为暗模式设计的导航链接_  
  
  

[](#accessing-global-client-objects)Accessing global client objects  
访问全局客户端对象
-------------------------------------------------------------------------------

Question! 🙋🏼 提问！🙋🏼

Where should we access global objects such as `window.localStorage`? Within an Astro component frontmatter or an interactive `<script>`?  
我们应该在哪里访问全局对象，例如 `window.localStorage` ？在Astro组件前端还是交互式 `<script>` ？

At this point, I hope the answer to the question is clear from previous examples.  
在这一点上，我希望从前面的例子中可以清楚地看到这个问题的答案。

Since Astro runs on the server, attempting to access a `window` property within the frontmatter of a component will result in an error.  
由于Astro在服务器上运行，试图访问组件前端中的 `window` 属性将导致错误。

\---
{/\*\* ❌ this will fail with the error: window is undefined \*\*/}
 const value \= window.localStorage.getItem("value")
\---

To access `window` properties, we need the script to run on the client, I.e., in the browser. So, we must leverage one or more client-side scripts.  
要访问 `window` 属性，我们需要在客户端上运行脚本，即：在浏览器中。因此，我们必须利用一个或多个客户端脚本。

A good use case for this is remembering the user’s theme choice.  
一个很好的用例是记住用户的主题选择。

If users toggle their theme from light to dark and refresh the browser, they lose the selected theme state.  
如果用户将主题从亮切换为暗并刷新浏览器，则会丢失选定的主题状态。

How about we save this state to the browser’s local storage and restore the selected theme upon refresh?  
我们将此状态保存到浏览器的本地存储中，并在刷新时恢复选定的主题，怎么样？

Well, let’s do that!  
好吧，那就这么办吧！

Here are the first steps we’ll take:  
以下是我们要采取的第一步：

*   Grab the current state of the theme, i.e., dark or light, when the theme toggle is clicked.  
    获取主题的当前状态，即，当主题切换被单击时，颜色为暗或亮。
*   Save the theme value to the browser’s local storage in the form:  
    将主题值保存到浏览器的本地存储中，格式如下：
    
    {
      COLOUR\_MODE: "LIGHT" | "DARK";
    }
    

Here’s that translated in code:  
下面是代码翻译：

<!-- 📂 src/components/ThemeToggler.astro -->
<script\>
  const DARK\_THEME\_CLASS \= "dark";
  /\*\* Represent the local storage key by a variable \*/
  const COLOUR\_MODE \= "COLOUR\_MODE";
  /\*\* Represent the local storage values by variables \*/
  const LIGHT\_THEME \= "LIGHT";
  const DARK\_THEME \= "DARK";
  /\*\* ... \*\*/
  toggle.addEventListener("click", () \=> {
    /\*\* ... \*/
    /\*\*Get the current theme mode, i.e., light or dark \*/
    const colourMode \= rootEl.classList.contains(DARK\_THEME\_CLASS)
      ? DARK\_THEME
      : LIGHT\_THEME;

    /\*\* Save the current theme to local storage   \*/
    window.localStorage.setItem(COLOUR\_MODE, colourMode);
  });
</script\>

We have saved the theme to local storage but must now set the active theme as soon as the page is loaded and the `script` is executed.  
我们已经将主题保存到本地存储，但现在必须在页面加载并执行 `script` 后立即设置活动主题。

Here’s the annotated code required to achieve this:  
下面是实现这一点所需的注释代码：

<!-- 📂 src/components/ThemeToggler.astro -->
<script\>
  {
    /\*\*... \*\*/
  }
  const getInitialColourMode \= () \=> {
    /\*\* Get colour mode from local storage \*\*/
    const previouslySavedColourMode \= window.localStorage.getItem(COLOUR\_MODE);
    if (previouslySavedColourMode) {
      return previouslySavedColourMode;
    }
    /\*\* Does the user prefer dark mode, e.g., through an operating system or user agent setting? \*/
    if (window.matchMedia("(prefers-color-scheme: dark)").matches) {
      return DARK\_THEME;
    }
    /\*\* Default to the light theme \*/
    return LIGHT\_THEME;
  };
  /\*\*Get initial colour mode \*/
  const initialColourMode \= getInitialColourMode();
  const setInitialColourMode \= (mode: string) \=> {
    if (mode \=== LIGHT\_THEME) {
      rootEl.classList.remove(DARK\_THEME\_CLASS);
    } else {
      rootEl.classList.add(DARK\_THEME\_CLASS);
    }
  };
  /\*\* Set the initial colour mode as soon as the script is executed \*/
  setInitialColourMode(initialColourMode);
  {
    /\*\*... \*\*/
  }
</script\>

Now, give this a try. First, toggle the theme and refresh to see the theme choice preserved!  
现在，给予看。首先，切换主题并刷新以查看主题选择保留！

[](#the-magic-of-scripts)The magic of scripts  
剧本的魔力
-----------------------------------------------------

Client-side scripts added via a `<script>` may seem like your typical Javascript vanilla JS, but they’re more capable in specific ways.  
通过 `<script>` 添加的客户端脚本看起来像典型的JavaScript vanilla JS，但它们在特定的方面更有能力。

The most crucial point is that Astro processes these. This means within a `<script>`, we can import other scripts or import npm packages, and Astro will resolve and package the script for use in the browser.  
最关键的一点是Astro处理这些。这意味着在 `<script>` 中，我们可以导入其他脚本或导入npm包，Astro将解析并打包脚本以在浏览器中使用。

<script\>
  /\*\* ✅ valid package import \*\*/
  import { titleCase } from "title-case";

  const title \= titleCase("string");

  alert(title);
</script\>

/\*\* ✅ valid script reference \*\*/
<script src\="path-to-script.js" />

Another critical point is the `<script>` fully supports Typescript. For example, in our solution, we typed the parameter for the `setInitialColourMode` function:  
另一个关键点是 `<script>` 完全支持Typescript。例如，在我们的解决方案中，我们输入了 `setInitialColourMode` 函数的参数：

// mode is of type string
const setInitialColourMode \= (mode: string) \=> {
  ...
};

We don’t have to sacrifice type safety within the client `<script>` elements and can go on to write standard Typescript code. Astro will strip out the types at build time and only serve the processed Javascript to the browser.  
我们不必牺牲客户端 `<script>` 元素中的类型安全性，可以继续编写标准的Typescript代码。Astro将在构建时剥离类型，只向浏览器提供处理过的JavaScript。

Here’s a summary of what Astro does:  
以下是Astro所做的总结：

*   `NPM` packages and local files can be imported and will be bundled.  
    `NPM` 包和本地文件可以导入并捆绑。
*   Typescript is fully supported within the `<script>`.  
    Typescript在 `<script>` 中完全支持。
*   If a single `Astro` component with a `<script>` is used multiple times on a page, the `<script>` is processed and only included once.  
    如果一个带有 `<script>` 的单个 `Astro` 组件在页面上被多次使用，则 `<script>` 将被处理并且仅包含一次。
*   Astro will process and insert the script in the `<head>` of the page with a `type=module` attribute.  
    Astro将处理并在页面的 `<head>` 中插入带有 `type=module` 属性的脚本。
*   ❗️The implication of `type=module` is that the browser will defer the script, i.e., load in parallel and **execute it only after** the page’s parsed.  
    ❗️ `type=module` 的含义是浏览器将延迟脚本，即，并行加载并仅在页面解析后执行。

[](#leveraging-inline-scripts)Leveraging inline scripts  
利用内联脚本
----------------------------------------------------------------

By default, Astro processes `<script>`s. However, to opt out of Astro’s default script processing, we may pass a `is:inline` directive as shown below:  
默认情况下，Astro处理 `<script>` s。然而，要选择退出Astro的默认脚本处理，我们可以传递一个 `is:inline` 指令，如下所示：

<script is:inline\>
  // Imports will not be processed // Typescript not supported by default //
  Script will be added as is, e.g., multiple times if the component is used more
  than once on a page.
</script>

In the real world, we quickly realise that the defaults don’t always satisfy every project requirement.  
在真实的世界中，我们很快意识到默认值并不总是满足每个项目需求。

For example, consider the unstyled flash of content when we refresh our home page. For a user who chose the dark theme previously, refreshing the page shows light-themed rendered content before changing to dark after the script is parsed.  
例如，当我们刷新我们的主页时，考虑一下无样式的内容。对于之前选择了深色主题的用户，刷新页面时会显示浅色主题的渲染内容，然后在脚本解析后更改为深色。

[![Transitioning light themed content viewed on Regular 3G throttling.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-03%20at%2003.24.42.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-03%20at%2003.24.42.png)

_Transitioning light themed content viewed on Regular 3G throttling.  
在常规3G节流上观看的过渡灯光主题内容。_  
  
  

This occurs because we restore the user-chosen theme only after the page’s HTML has been parsed, i.e, the default behaviour of processed Astro scripts.  
这是因为我们只在页面的HTML被解析后，即默认的Astro脚本行为，恢复用户选择的主题。

To prevent this, we will use the `is:inline` directive, which will make the script blocking, i.e., executed immediately and stops parsing until completed.  
为了防止这种情况，我们将使用 `is:inline` 指令，这将使脚本阻塞，即：立即执行并停止解析直到完成。

Since scripts with the `is:inline` attribute aren’t processed, they’ll be added multiple times if used in reusable components that appear more than once on the page.  
由于具有 `is:inline` 属性的脚本不会被处理，因此如果在页面上出现多次的可重用组件中使用，它们将被添加多次。

So, let’s go ahead and move the theme restoration code bit into `Main.astro` — because the `Main` layout is only included once per page.  
因此，让我们继续前进，并将主题恢复代码位移动到 `Main.astro` 中-因为 `Main` 布局仅在每个页面中包含一次。

We’ll also make sure to add this within the `<head>` of the layout, as shown below:  
我们还将确保将其添加到布局的 `<head>` 中，如下所示：

<!-- 📂 src/layouts/Main.astro -->
<head\>
  <!-- ... -->
  <!-- 👀 add is:inline -->
  <script is:inline\>
    const DARK\_THEME\_CLASS \= "dark";
    const COLOUR\_MODE \= "COLOUR\_MODE";
    const LIGHT\_THEME \= "LIGHT";
    const DARK\_THEME \= "DARK";
    const rootEl \= document.documentElement;
    const getInitialColourMode \= () \=> {
      /\*\* ... \*/
    };
    const initialColourMode \= getInitialColourMode();
    // 👀 remove string type on mode
    const setInitialColourMode \= (mode) \=> {
      /\*\* ... \*/
    };
    /\*\* Set the initial colour mode as soon as the script is executed \*/
    setInitialColourMode(initialColourMode);
  </script\>
</head\>

We’re explicitly adding this to the `<head>` because Astro will not process the `is:inline` script. As such, it won’t be moved to the `head` by Astro.  
我们将它显式地添加到 `<head>` ，因为Astro不会处理 `is:inline` 脚本。因此，它不会被Astro移动到 `head` 。

Be careful with `is:inline` as it removes the default non-blocking nature of scripts. But it’s ideal for this use case.  
注意 `is:inline` ，因为它删除了脚本的默认非阻塞特性。但它非常适合这个用例。

Open your developer tools and throttle the network. Then go ahead and refresh after toggling dark mode. We should have eradicated the flash of unstyled content!  
打开你的开发者工具，控制网络。然后继续并刷新后切换黑暗模式。我们应该根除无风格内容的闪光！

[![Throttling the network via the chrome developer tools.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-11%20at%2007.30.21@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-11%20at%2007.30.21@2x.png)

_Throttling the network via the chrome developer tools.  
通过chrome开发者工具限制网络。_  
  
  

[](#global-selectors-in-scripts)Global selectors in scripts  
脚本中的全局选择器
-----------------------------------------------------------------------

Understanding how Astro processes the `<script>` in our components helps us make informed decisions.  
了解Astro如何处理组件中的 `<script>` 有助于我们做出明智的决策。

We know the `<script>` will eventually be bundled and injected into our page’s `<head>`.  
我们知道 `<script>` 最终会被捆绑并注入到我们页面的 `<head>` 中。

However, consider our selector for registering the theme toggle clicks:  
但是，考虑一下我们的选择器来注册主题切换点击：

// 📂 src/components/ThemeToggler.astro
const toggle \= document.querySelector("button");

The problem with this seemingly harmless code is that `document.querySelector` will return the first element that matches the selector — a button element.  
这个看似无害的代码的问题是 `document.querySelector` 将返回第一个匹配选择器的元素-button元素。

This will be selected if we add a random button somewhere on the page before our theme toggle button.  
如果我们在主题切换按钮之前的页面上添加了一个随机按钮，这将被选中。

// 📂 src/layouts/Main.astro
<button\> Donate to charity </button\>
<Nav /\>

//...

[![The donate to charity button.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-03%20at%2003.38.21.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-03%20at%2003.38.21.png)

_The donate to charity button.  
捐赠给慈善机构的按钮。_  
  
  

This button, which has nothing to do with theme toggling, will now be responsible for toggling the user’s theme.  
这个按钮与主题切换无关，现在将负责切换用户的主题。

Clicking “donate to charity” now toggles the theme. This is unacceptable.  
点击“捐赠给慈善机构”现在切换主题。这是不可接受的。

The lesson here is to be mindful of your DOM selectors and be specific where possible, e.g., via ids or classes:  
这里的教训是要注意DOM选择器，并尽可能具体，例如，通过ID或类：

document.querySelector("#some-unique-id");

Let’s refactor our solution to use a data attribute.  
让我们重构我们的解决方案以使用数据属性。

<!-- 📂 src/components/ThemeToggler.astro -->
<button aria-label\="Theme toggler" data-theme-toggle\>
  <!-- ... -->
</button\>

<script\>
  /\*\* 👀 Look here \*/
  const toggle \= document.querySelector("\[data-theme-toggle\]");
  // ...
</script\>

With the more specific selector, only an element with the data attribute `theme-toggle` will be selected, leaving `<button> Donate to charity </button>` out of our theme toggle business.  
使用更具体的选择器，只会选择具有数据属性 `theme-toggle` 的元素，而不会选择 `<button> Donate to charity </button>` 。

[](#markdown-pages)Markdown pages Markdown页面
--------------------------------------------

We’ve established that not all file types are valid pages in Astro. We’ve seen Astro components as pages, but allow me to introduce markdown pages!  
我们已经确定，并非所有文件类型都是Astro中的有效页面。我们已经看到了Astro组件的页面，但请允许我介绍一下markdown页面！

Markdown[5](#user-content-fn-5-aa56f548e078749351c130450542ff17) is a popular, easy-to-use markup language for creating formatted text. I’m sure my nan does not know markdown, so it’s safer to say it’s a famous text format among developers.  
Markdown [5](#user-content-fn-5-aa56f548e078749351c130450542ff17) 是一种流行的、易于使用的标记语言，用于创建格式化文本。我敢肯定我奶奶不知道markdown，所以说它是开发者中著名的文本格式更安全。

It’s no surprise Astro supports creating pages via markdown. So, let’s put this to the test.  
难怪Astro支持通过markdown创建页面。我们来测试一下。

We’ll create two new pages to replace our dead `Philosophies` and `Beyond technology` navigation links.  
我们将创建两个新页面来替换我们已经失效的 `Philosophies` 和 `Beyond technology` 导航链接。

[![The dead navigation links.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-02%20at%2010.50.19@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-02%20at%2010.50.19@2x.png)

_The dead navigation links.  
死亡的导航链接_  
  
  

Create the first page in `src/pages/philosophies.md` with the following content:  
在 `src/pages/philosophies.md` 中创建第一页，内容如下：

\- 5X \*\*Marathoner\*\*
\- Olympic gold medalist
\- Fashion \_model\_
\- Michelin-star restaurant owner
\- Adviser to the vice president

Create the second page in `src/pages/beyond-tech.md` with the following content:  
在 `src/pages/beyond-tech.md` 中创建第二个页面，内容如下：

\- Be present and \*\*enjoy the now\*\*
\- Be driven by values
\- Health is \_wealth\_
\- Be deliberate
\- Laugh out loud

These files are written in markdown syntax[6](#user-content-fn-6-aa56f548e078749351c130450542ff17).  
这些文件是用markdown语法 [6](#user-content-fn-6-aa56f548e078749351c130450542ff17) 编写的。

As with Astro component pages, markdown pages eventually get compiled to standard `HTML` pages rendered in the browser. The same file-based routing is also used. For example, to access the `philosophies` and `beyond-tech` pages, visit the `/philosophies` and `/beyond-tech`  routes, respectively.  
与Astro组件页面一样，markdown页面最终会被编译成标准的 `HTML` 页面在浏览器中呈现。也使用相同的基于文件的路由。例如，要访问 `philosophies` 和 `beyond-tech` 页面，请分别访问 `/philosophies` 和 `/beyond-tech`  路由。

[![The philosophies page.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-03%20at%2002.42.23.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-03%20at%2002.42.23.png)

_The philosophies page. 哲学页_  
  
  

[](#navigating-between-pages)Navigating between pages  
在页面之间导航
---------------------------------------------------------------

Navigating between pages in Astro requires no magic wand. Surprise!  
在Astro页面之间导航不需要魔杖。惊喜！

Astro uses the standard `<a>` element to navigate between pages. This makes sense as each page is a separate `HTML` page.  
Astro使用标准的 `<a>` 元素在页面之间导航。这是有意义的，因为每个页面都是单独的 `HTML` 页面。

Let’s update the navigation links to point to the new markdown pages as shown below:  
让我们更新导航链接，以指向新的markdown页面，如下所示：

<!-- 📂 NavigationBar.astro -->

<li\>
  <a href\="/"\>Home</a\>
</li\>

<li\>
  <a href\="/philosophies"\>Philosophies</a\>
</li\>

<li\>
  <a href\="/beyond-tech"\>Beyond technology</a\>
</li\>

Clicking any of these links should now lead us to their appropriate pages.  
单击这些链接中的任何一个现在应该会引导我们到相应的页面。

[](#markdown-layouts)Markdown layouts Markdown布局
------------------------------------------------

Let’s face it; we won’t be winning any design awards for our current markdown pages. This is because they seem off and don’t share the same layout as our existing page. Can we fix this?  
让我们面对现实吧我们不会赢得任何设计奖为我们目前的降价页面。这是因为它们看起来不太好，而且与我们现有页面的布局不一样。我们能解决这个问题吗

You’ve probably realised I ask questions and then provide answers. All right, you’ve got me. So that’s my trick to make you think about a problem — hoverer brief — before explaining the solution.  
你可能已经意识到我问问题，然后提供答案。好吧，你有我。所以这就是我的诀窍，让你在解释解决方案之前先思考一个问题--更详细的简要说明。

Believe it or not, Astro component frontmatter was inspired by markdown! The original markdown syntax supports frontmatter for providing metadata about the document. For example, we could add a `title` metadata as shown below:  
信不信由你，Astro组件前端的灵感来自markdown！原始的markdown语法支持frontmatter来提供关于文档的元数据。例如，我们可以添加一个 `title` 元数据，如下所示：

\--\-
title: Understanding Astro
\--\-

This is excellent news because Astro leverages this to provide layouts for markdown pages!  
这是一个好消息，因为Astro利用它来为markdown页面提供布局！

Instead of the _so dull I can’t take it_ page, we can utilise a layout to bring some reusable structure to all our markdown pages.  
我们可以利用布局为所有的markdown页面带来一些可重用的结构，而不是那种无聊的我不能接受的页面。

Let’s get started. 我们开始吧。

With Astro markdown pages, we can provide layouts for a markdown page by providing a layout frontmatter metadata as shown below:  
使用Astro markdown页面，我们可以通过提供布局frontmatter元数据来提供markdown页面的布局，如下所示：

\--\-
layout: path\-to\-layout
\--\-

First, let’s reuse the same `Main` layout by adding the following to both markdown pages:  
首先，让我们通过在两个markdown页面中添加以下内容来重用相同的 `Main` 布局：

// add at the top of the Markdown pages.
\--\-
layout: ../layouts/Main.astro
\--\-

The markdown pages should now reuse our existing layout with the theming, navigation and footer all set in place!  
markdown页面现在应该重新使用我们现有的布局，主题，导航和页脚都设置好了！

[![Using the Main layout in the markdown pages.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-03%20at%2004.40.15.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-03%20at%2004.40.15.png)

_Using the Main layout in the markdown pages.  
在markdown页面中使用Main布局。_  
  
  

Since `Main.astro` includes our `global.css` files, let’s go ahead and provide some default global styles for paragraphs and lists:  
由于 `Main.astro` 包含了我们的 `global.css` 文件，让我们继续为段落和列表提供一些默认的全局样式：

 {
  /\*\* 📂 src/styles/global.css \*\*/
}
p,
li {
  font-size: 1rem;
  color: var(\--gray-400);
  opacity: 0.8;
}

li {
  margin: 1rem 0;
}

[![Global list styles are now applied to the Markdown pages.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-11%20at%2007.51.10@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-11%20at%2007.51.10@2x.png)

_Global list styles are now applied to the Markdown pages.  
全局列表样式现在应用于Markdown页面。_  
  
  

We should now have these styles take effect on our markdown pages! Isn’t life better with shared layout components? 😉  
我们现在应该让这些样式生效在我们的markdown页面！共享布局组件不是更好吗？ 😉

[](#composing-layouts)Composing layouts 合成布局
--------------------------------------------

Layouts are Astro components, meaning we can compose them, i.e., render a layout in another.  
布局是Astro组件，这意味着我们可以组合它们，即，在另一个中渲染布局。

For example, let’s create a separate `Blog.astro` layout that composes our base `Main.astro` layout.  
例如，让我们创建一个单独的 `Blog.astro` 布局来组成我们的基础 `Main.astro` 布局。

// 📂 src/layouts/Blog.astro
\--\-
import Main from "./Main.astro";
\--\-

<Main\>
  <slot /\>
</Main\>

Composing the layouts in this way means we can reuse all the good stuff in `Main.astro` while extending `Blog.astro` to include only blog-specific elements.  
以这种方式组合布局意味着我们可以重用 `Main.astro` 中的所有好东西，同时扩展 `Blog.astro` 以只包含博客特定的元素。

The separation of concern significantly improves legibility and forces each layout to have a single responsibility.  
关注点的分离显著提高了易读性，并迫使每个布局具有单一的责任。

Now, at this point, the markdown pages have the same layout markup and styles from `Main.astro`. We’ve made no customisations.  
现在，在这一点上，markdown页面具有与 `Main.astro` 相同的布局标记和样式。我们没有定制。

[](#component-props)Component props 组件道具
----------------------------------------

As we build reusable components, we often find situations where we must customise certain values within a component. For example, consider the `<title>` in our `Main.astro` layout component:  
在构建可重用组件时，我们经常会发现必须在组件中自定义某些值的情况。例如，考虑我们的 `Main.astro` 布局组件中的 `<title>` ：

// 📂 src/layouts/Main.astro
<title\>Astro</title\>

A hardcoded `title` on every page where the `Main` layout is used is ridiculous.  
在使用 `Main` 布局的每一页上硬编码 `title` 是荒谬的。

To foster reusability, components can accept properties. These are commonly known as **props**.  
为了促进可重用性，组件可以接受属性。这些通常被称为道具。

Props are passed to components as attributes.  
道具作为属性传递给组件。

<Main title\="Some title" /\>

The prop values are then accessed via `Astro.props`. This is better explained with an example.  
然后通过 `Astro.props` 访问prop值。这可以用一个例子更好地解释。

Go ahead and update `Main` to accept a `title` prop as shown below:  
继续并更新 `Main` 以接受 `title` 道具，如下所示：

// 📂 src/layouts/Main.astro
\--\-
// ...
const { title } \= Astro.props;
\--\-

<html lang\="en"\>
  <head\>
    {/\*\* ... \*\*/}
    {/\*\* 👀 look here \*\*/}
    <title\>{title}</title\>
  </head\>
     {/\*\* ... \*\*/}
</html\>

To enforce Typescript checks, define the `Props` type alias or interface.  
要强制执行Typescript检查，请定义 `Props` 类型别名或接口。

// Either of these is valid
type Props \= {
  title: string,
};

interface Props {
  title: string;
}

For simplicity, I’ll stick to a type alias for the `Main` layout:  
为了简单起见，我将坚持使用 `Main` 布局的类型别名：

// 📂 src/layouts/Main.astro
\--\-
type Props \= {
  title: string
}

const { title } \= Astro.props;
\--\-
// ...

With the type declared, we’ll have Typescript error(s) in files where we’ve used `<Main>` without the required `title` prop.  
声明了类型后，我们在使用 `<Main>` 而没有需要的 `title` prop的文件中会出现Typescript错误。

[![Invalid title props error.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-03%20at%2006.01.52.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-03%20at%2006.01.52.png)

_Invalid title props error.  
标题道具无效错误。_  
  
  

Update the `index.astro` and `Blog.astro` pages to pass a `title` prop to `Main`:  
更新 `index.astro` 和 `Blog.astro` 页面，将 `title` prop传递给 `Main` ：

// 📂 src/layouts/index.astro
<Main title\="Frau Katarina"\>
{/\* ... \*/}

// 📂 src/layouts/Blog.astro
<Main title\="Frau Katarina | Blog"\>
{/\* ... \*/}

[](#leveraging-markdown-frontmatter-properties)Leveraging markdown frontmatter properties  
利用Markdown frontmatter属性
--------------------------------------------------------------------------------------------------------------------

All markdown pages in our application will have a title, subtitle and poster. Luckily, a great way to represent these is via frontmatter properties.  
我们应用程序中的所有markdown页面都将有标题、副标题和海报。幸运的是，一个很好的方式来表示这些是通过frontmatter属性。

Update the markdown pages to now include these properties, as shown below.  
更新markdown页面以包含这些属性，如下所示。

`📂 src/pages/beyond-tech.md`:

\---
layout: ../layouts/Blog.astro
poster: "/images/road-trip.jpg"
title: "Beyond Technology"
subtitle: "Humans are multi-faceted. Beyond tech, I indulge in the following:"
\---

...

`📂 src/pages/philosophies.md`:

\---
layout: ../layouts/Blog.astro
poster: "/images/philosophies.jpg"
title: "My Guiding Philosophies"
subtitle: "These are the philosophies that guide every decision and action I make."
\---

...

Note that `poster` points to image paths. These paths reference the `public` directory. So `/images/philosophies.jpg` points to an image in `public/images/philosophies.jpg`.  
请注意， `poster` 指向图像路径。这些路径引用 `public` 目录。 `/images/philosophies.jpg` 指向 `public/images/philosophies.jpg` 中的图像。

If you’re coding along, feel free to download any image from Unsplash and move them to the `public` directory.  
如果您正在编写代码，请随时从Unsplash下载任何图像并将其移动到 `public` 目录。

Adding metadata to our markdown pages doesn’t do us any good if we can use them.  
如果我们可以使用的话，向我们的markdown页面添加元数据对我们没有任何好处。

Luckily, markdown layouts have a unique superpower — they can access markdown frontmatter via `Astro.props.frontmatter`.  
幸运的是，markdown布局有一个独特的超能力-他们可以通过 `Astro.props.frontmatter` 访问markdown frontmatter。

Let’s go ahead and globally handle this in our `Blog.astro` layout component. Below’s the component script section:  
让我们继续在 `Blog.astro` 布局组件中全局处理这个问题。下面是组件脚本部分：

// 📂 src/layouts/Blog.astro
\--\-
// import the type utility for the markdown layout props
import type { MarkdownLayoutProps } from "astro";
// import the base layout: Main.astro
import Main from "./Main.astro";

// defined the Props type
type Props \= MarkdownLayoutProps<{
  // Define the expected frontmatter props here
  title: string;
  poster: string;
  subtitle: string;
}\>;

// get properties from the markdown frontmatter
const { poster, title, subtitle } \= Astro.props.frontmatter;
\--\-

*   The `MarkdownLayoutProps` utility type accepts a generic and returns the type for all the properties available to a markdown layout. So feel free to inspect the entire shape[7](#user-content-fn-7-aa56f548e078749351c130450542ff17).  
    `MarkdownLayoutProps` 实用程序类型接受泛型并返回markdown布局可用的所有属性的类型。因此，请随意检查整个形状 [7](#user-content-fn-7-aa56f548e078749351c130450542ff17) 。
*   `MarkdownLayoutProps` accepts our frontmatter property type definition as a generic, i.e., `title`, `poster` and `subtitle`. These are properties we’ve added in the frontmatter of our Markdown pages.  
    `MarkdownLayoutProps` 接受frontmatter属性类型定义为泛型，即 `title` 、 `poster` 和 `subtitle` 。这些是我们在Markdown页面的前件中添加的属性。
*   `type Props = ...` or `interface Props {}` is how we provide types for an Astro component.  
    `type Props = ...` 或 `interface Props {}` 是我们为Astro组件提供类型的方式。
*   The final line deconstructs the properties from `Astro.props.frontmatter` with full Typescript support.  
    最后一行用完全Typescript支持解构 `Astro.props.frontmatter` 的属性。

[![Typescript support in the Markdown layout.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-03%20at%2005.16.20.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-03%20at%2005.16.20.png)

_Typescript support in the Markdown layout.  
Markdown布局中的Typescript支持。_  
  
  

Equally update the layout markup to render the image, title and subtitle:  
同样地更新布局标记以呈现图像、标题和副标题：

<!-- 📂 src/layouts/Blog.astro \-->
<main\>
  <figure class\="figure"\>
    <img
      src\={poster}
      alt\=""
      width\="100%"
      height\="480px"
      class\="figure\_\_image"
    />
    <figcaption class\="figure\_\_caption"\>
      Poster image for {title.toLowerCase()}
    </figcaption\>
  </figure\>

  <h1\>{title}</h1\>
  <h2\>{subtitle}</h2\>

  <slot />
</main\>

<style\>
  h1 + h2 {
    margin-bottom: 3rem;
  }

  .figure {
    margin: 0;
  }

  .figure\_\_image {
    max-width: 100%;
    border-radius: 10px;
  }

  .figure\_\_caption {
    font-size: 0.9rem;
  }
</style\>

Most of the markup is arguably standard. However, note the `title.toLowerCase()` call for the poster image caption. This is possible because any valid JavaScript expression can be evaluated within curly braces `{ }` in the component markup.  
大多数标记都是标准的。但是，请注意海报图像标题的 `title.toLowerCase()` 调用。这是可能的，因为任何有效的JavaScript表达式都可以在组件标记中的花括号 `{ }` 中计算。

Our markdown pages will now have styled titles, subtitles and poster images! With all this handled in one place — the markdown layout.  
我们的降价页面现在将有风格的标题，字幕和海报图像！所有这些都在一个地方处理-markdown布局。

[![The fully formed Markdown page.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-03%20at%2005.19.26.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-03%20at%2005.19.26.png)

_The fully formed Markdown page.  
完整的Markdown页面。_  
  
  

[](#interactive-navigation-state)Interactive navigation state  
交互导航状态
----------------------------------------------------------------------

Now that we’re pros at handling interactive scripts in Astro let’s go ahead and make sure that we style our active navigation links differently.  
既然我们是在Astro中处理交互式脚本的专家，那么我们继续前进，确保我们的活动导航链接风格不同。

As with all things programming, there are different ways to achieve this, but we will go ahead and script this.  
与所有编程一样，有不同的方法来实现这一点，但我们将继续编写脚本。

<!-- 📂 src/components/NavigationBar.astro -->
<script\>
  const { pathname } \= window.location;
  const activeNavigationElement \= document.querySelector(
    \`nav a\[href="${pathname}"\]\`
  );

  if (activeNavigationElement) {
    activeNavigationElement.classList.add("active");
  }
</script\>

*   Get the `pathname` from the `location` object. This will be in the form `"/beyond-tech"`, `"/philosophies` or `"/"`.  
    从 `location` 对象中获取 `pathname` 。这将采用 `"/beyond-tech"` 、 `"/philosophies` 或 `"/"` 的形式。
*   Since the `pathname` corresponds to the `href` on the anchor tag element, we may select the active anchor tag via: ``document.querySelector(`nav a[href="${pathname}"]`).``  
    由于 `pathname` 对应于锚标记元素上的 `href` ，我们可以通过以下方式选择活动锚标记： ``document.querySelector(`nav a[href="${pathname}"]`).``
*   Finally, we add the `active` class to the active anchor tag.  
    最后，我们将 `active` 类添加到活动锚标记中。

Finally, add the relevant style for the active tag:  
最后，为活动标签添加相关样式：

/\* 📂 src/components/NavigationBar.astro \*/
<style\>
  /\* ... \*/
 a.active {
  background: var(\--grey-900);
  color: var(\--background);
 }
</style\>

Viola! We should now have the active anchor tag styled differently.  
维奥拉我们现在应该有不同样式的活动锚标记。

[![Active anchor tag styles.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-03%20at%2009.44.02.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-03%20at%2009.44.02.png)

_Active anchor tag styles.  
活动锚标记样式。_  
  
  

[](#component-composition)Component composition 组分组成
----------------------------------------------------

Our first look at component composition was with the `Main` and `Blog` layouts. Let’s take this further.  
我们第一次看到组件组合是使用 `Main` 和 `Blog` 布局。我们再进一步。

Our goal is to create a set of different yet identical cards. Each card acts as a link to a blog and will have a title and some background gradient.  
我们的目标是创建一组不同但相同的卡片。每张卡片作为一个博客的链接，并将有标题和一些背景渐变。

[![The eventual card layout we will build.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-04%20at%2009.44.58.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-04%20at%2009.44.58.png)

_The eventual card layout we will build.  
我们将构建的最终卡片布局。_  
  
  

To achieve this, we’ll have a `Cards.astro` component that renders multiple `Card.astro` components.  
为了实现这一点，我们将有一个 `Cards.astro` 组件来渲染多个 `Card.astro` 组件。

[![The card composition visualised.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/b.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/b.png)

_The card composition visualised.  
卡片组成可视化。_  
  
  

Let’s start by creating `Card.astro`.  
让我们开始创建 `Card.astro` 。

Define the relevant component props and relevant markup as shown below:  
定义相关组件props和相关标记，如下所示：

// 📂 src/components/Card.astro
\--\-
{/\*\* Export the Props type alias \*\*/}
export type Props \= {
  to: string;
  title: string;
  gradientFrom: string;
  gradientTo: string;
};

// Get component props from Astro.props
const { title, to } \= Astro.props;
\--\-

<a href\={to} class\="card"\>
  <div class\="card\_\_inner"\>
    <div class\="card\_\_title"\>{title}</div\>
    <!-- Render the arrow via HTML entity name: → = &rarr;\-->
    <div class\="card\_\_footer"\>&rarr;</div\>
  </div\>
</a\>

<style\>
  .card {
    /\*\* local CSS variable reused below \*/
    --radius: 10px;

    padding: 4px;
    border-radius: var(--radius);
    text-decoration: none;
    transition: all 0.2s ease-in-out;
  }

  .card:hover {
    transform: scale(0.95);
  }

  .card\_\_inner {
    background: var(--background);
    padding: 1.5rem;
    border-radius: var(--radius);
    display: flex;
    flex-direction: column;
  }

  .card\_\_title {
    font-size: 1.2rem;
    color: var(--grey-900);
    font-weight: 500;
    line-height: 1.75rem;
  }

  .card\_\_footer {
    padding-top: 2rem;
    font-size: 1.2rem;
    color: var(--grey-900);
    margin: auto 0 0 auto;
  }
</style\>

Now, go ahead and create the `Cards.astro` component as follows:  
现在，继续创建 `Cards.astro` 组件，如下所示：

// 📂 src/components/Cards.astro
\--\-
// Import the Card component
import Card from "./Card.astro";
// Import the Card Props type
import type { Props as CardProp } from "./Card.astro";

// Define the Props for this component
type Props \= {
  cards: CardProp\[\]; // accepts an array of CardProps
};

// Retrieve the cards prop
const { cards } \= Astro.props;
\--\-

<div class\="cards"\>
  <!-- Dynamically render multiple Card components and spread the required card props -->
  {cards.map((card) =\> <Card {...card} />)}
</div\>

<style\>
  .cards {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  /\* Since this is standard CSS, we can have media queries here \*/
  @media screen and (min-width: 768px) {
    .cards {
      flex-direction: row;
    }
  }
</style\>

To see the fruits of our labour, we must now import and render `Cards` in the `index.astro` page component.  
为了看到我们的劳动成果，我们现在必须在 `index.astro` 页面组件中导入并呈现 `Cards` 。

// 📂 src/pages/index.astro
\--\-
// ...
import Cards from "../components/Cards.astro";
\--\-
<Main\>
  <div class\="profile"\>
   {/\*\* ... \*\*/}
  </div\>
  {/\*\* 👀 look here \*\*/}
  <Cards
    cards\={\[
      {
        title: "Here are my guiding philosophies for life",
        gradientFrom: "#818cf8",
        gradientTo: "#d8b4fe",
        to: "/philosophies",
      },
      {
        title: "A summary of my work history",
        gradientFrom: "#fde68a",
        gradientTo: "#fca5a5",
        to: "/work-summary",
      },
      {
        title: "What I do beyond technology",
        gradientFrom: "#6ee7b7",
        gradientTo: "#9333ea",
        to: "/beyond-tech",
      },
    \]}
  /\>
</Main\>

[![The rendered cards.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-04%20at%2010.18.23.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-04%20at%2010.18.23.png)

_The rendered cards. 渲染的卡片。_  
  
  

Clicking any of the links will point to the respective blog page.  
单击任何链接将指向相应的博客页面。

Let’s not forget to add the new `work-summary.md` page:  
不要忘记添加新的 `work-summary.md` 页面：

// 📂 src/pages/work-summary.md
\--\-
layout: ../layouts/Blog.astro
poster: "/images/work-summary.jpg"
title: "Work summary"
subtitle: "A summary of my work:"
\--\-

\- VP Engineering at Google
\- VP Engineering at Facebook
\- VP Engineering at Tesla
\- VP Engineering at Amazon
\- VP Engineering at Netflix

There we go! 好了！

[](#the-template-flow-of-data)The template flow of data  
模板数据流
---------------------------------------------------------------

As we’ve discussed, the data in the frontmatter runs on the server and is not available in the browser.  
正如我们所讨论的，frontmatter中的数据在服务器上运行，在浏览器中不可用。

As we’ve built our application, we’ve frequently leveraged data in the frontmatter in the template section, as shown below:  
当我们构建应用程序时，我们经常在模板部分使用frontmatter中的数据，如下所示：

\--\-
 const data \= "Understanding Astro"
\--\-

//Use data in the template
<h1\>{data}</h1\>

This is easy to reason about for our static website. We know this will eventually be compiled into HTML.  
这对于我们的静态网站来说很容易解释。我们知道它最终会被编译成HTML。

However, consider a more robust markup that includes `<style>` and `<script>` elements. How do we reference data from the frontmatter in these markup sections?  
但是，考虑一个更健壮的标记，它包含 `<style>` 和 `<script>` 元素。我们如何在这些标记部分引用frontmatter中的数据？

\--\-
 const data \= "Understanding Astro"
\--\-

// ✅ Use data in the template
<h1\>{data}</h1\>

// styles
<style\>
 {/\*\* ❌referencing data here will fail \*/}
</style>
// scripts
<script\>
{/\*\* ❌referencing data here will fail \*/}
 console.log(data)
</script>

One answer is via the `define:vars` template directive.  
一个答案是通过 `define:vars` template指令。

`define:vars` will pass our variables from the frontmatter into the client `<script>` or `<style>`. It’s important to note that only JSON serialisable values work here.  
`define:vars` 将我们的变量从frontmatter传递到客户端 `<script>` 或 `<style>` 。需要注意的是，只有JSON可序列化值在这里起作用。

Let’s give this a shot.  
我们给予看吧。

We must reference the `gradientFrom` and `gradientTo` variables passed as props in our `<style>`.  
我们必须引用 `gradientFrom` 和 `gradientTo` 变量作为props传递给我们的 `<style>` 。

First, to make the variables available within `<style>`, we’ll go ahead and use `define:vars` as follows:  
首先，为了使变量在 `<style>` 中可用，我们将继续使用 `define:vars` ，如下所示：

// 📂 src/components/Card.astro
\--\-
const { title, to, gradientFrom, gradientTo } \= Astro.props;
// ...
\--\-

<style define:vars\={{gradientFrom, gradientTo }}\>
  {/\*\* ... \*\*/}
</style\>

`define:vars` accepts an object of variables we want available within `<style>`.  
`define:vars` 接受我们希望在 `<style>` 中可用的变量对象。

The variables are defined but not used yet!  
变量已定义但尚未使用！

Now, we can reference the variables via custom properties (aka css variables) as shown below:  
现在，我们可以通过自定义属性（又称css变量）引用变量，如下所示：

/\*\* 📂 src/components/Card.astro \*\*/
<style define:vars\={{gradientFrom, gradientTo }}\>
  /\*\* 👀 look here \*\*/
  .card {
    background-image: linear-gradient(
      to right,
      var(\--gradientFrom),
      var(\--gradientTo)
    );
  }
 /\*\* ... \*\*/
</style\>

And voila! 瞧！

Our cards are now more beautiful than ever.  
我们的卡片现在比以往任何时候都漂亮。

[![Applying dynamic gradients to the cards.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-04%20at%2010.45.36.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-04%20at%2010.45.36.png)

_Applying dynamic gradients to the cards.  
将动态渐变应用到卡片上。_  
  
  

[](#the-dark-side-of-definevars)The dark side of define:vars  
定义的黑暗面：vars
--------------------------------------------------------------------------

We’ve seen `define:vars` come in handy for using variables from the frontmatter of an Astro component. However, be careful when using `define:vars` with scripts.  
我们已经看到 `define:vars` 在使用Astro组件前端的变量时很方便。但是，在使用脚本时要小心 `define:vars` 。

Using `define:vars` with a `<script>` is similar to using the `is:inline` directive.  
将 `define:vars` 与 `<script>` 一起使用类似于使用 `is:inline` 指令。

Astro will not bundle the script and will be added multiple times if the same component is rendered more than once on a page.  
Astro不会捆绑脚本，如果同一个组件在页面上被多次渲染，则会被多次添加。

Here’s an example to make this clear.  
这里有一个例子来说明这一点。

In `Card.astro` go ahead and add a `<script>` with the `define:vars` directive as follows:  
在 `Card.astro` 中继续添加 `<script>` 和 `define:vars` 指令如下：

/\*\* 📂 src/components/Card.astro \*\*/
<script define:vars\={{ gradientFrom }}\>console.log(gradientFrom);</script\>

Inspect the elements via the developer tools. You’ll notice that the `<script>` is inlined and unprocessed, i.e., just as we’ve written it, apart from being wrapped in an immediately invoked function execution (IIFE).  
通过开发工具检查元件。您会注意到 `<script>` 是内联的且未处理的，即：就像我们写的一样，除了包装在立即调用函数执行（IIFE）中。

[![The inlined scripts.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-04%20at%2012.07.32.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-04%20at%2012.07.32.png)

_The inlined scripts. 内联脚本。_  
  
  

The script is also added three times — with a different value of `gradientFrom` for each rendered card.  
脚本也被添加三次-每个渲染的卡片都有不同的值 `gradientFrom` 。

With scripts, a better solution (except the inline behaviour is ideal for your use case) is to pass the data from the component frontmatter to the rendered element via `data-` attributes and then access these via Javascript.  
对于脚本，一个更好的解决方案（除了内联行为对于您的用例来说是理想的）是通过 `data-` 属性将数据从组件前端传递到渲染元素，然后通过JavaScript访问这些。

For example, we may rewrite the previous solution as shown below:  
例如，我们可以重写之前的解决方案，如下所示：

\---
\---

<a href\={to} class\="card" data-gradientfrom\={gradientFrom}\> ... </a\>
...
<script\>
  const card = document.querySelector(".card");

  // narrow the type of card to HTMLElement to access ".dataset"
  if (card instanceof HTMLElement) {
    // access data in dataset.gradientfrom
    console.log(card.dataset.gradientfrom);
  }
</script\>

Note that this is a contrived example and only retrieves the first card element with its associated `gradientfrom` data. Still, this demonstrates how to prevent unwanted behaviours with `define:vars` in `<script>`s.  
请注意，这是一个人为的示例，仅检索第一个card元素及其关联的 `gradientfrom` 数据。尽管如此，这演示了如何在 `<script>` s中防止 `define:vars` 出现不必要的行为。

[](#loading-multiple-local-files)Loading multiple local files  
加载多个本地文件
------------------------------------------------------------------------

Let’s go ahead and create a new `blog` directory to hold some more markdown pages. The pages and their content are shown below:  
让我们继续创建一个新的 `blog` 目录来保存更多的markdown页面。页面及其内容如下所示：

`📂 pages/blogs/rust-javascript-tooling.md` :

\---
layout: "../../layouts/Blog.astro"
poster: "/images/adventure.jpg"
title: "Why Rust is the Future of Javascript Tooling"
subtitle: "How to create fast, speedy developer experiences."
\---

\- Rust is fast
\- Yes, it is fast
\- Touted as the new C++
\- Did I mention it's pretty fast?

`📂 pages/blogs/sleep-more.md` :

\---
layout: "../../layouts/Blog.astro"
poster: "/images/sleeping-cat.jpg"
title: "Why you should sleep more"
subtitle: "Sleep is great for you. Here's why:"
\---

\- Sleep
\- Sleep more
\- Sleep a little more

`📂 pages/blogs/typescript-new-javascript.md`  :

\---
layout: "../../layouts/Blog.astro"
poster: "/images/coding.jpg"
title: "Typescript is the new Javascript"
subtitle: "Typescript is becoming a standard for web development these days:"
\---

\- Type safety
\- Type safety!
\- Even more type safety!

We aim to list these blog titles on our home page. One way to do this would be to render all link elements in `index.astro` manually:  
我们的目标是在我们的主页上列出这些博客标题。一种方法是手动渲染 `index.astro` 中的所有链接元素：

<!-- 📂 src/pages/index.astro -->
...
<main\>
  ...
  <div class\="featured-blogs"\>
    <h3 class\="featured-blogs\_\_title"\>Featured Blogs</h3\>
    <p class\="featured-blogs\_\_description"\>
      Opinion pieces that will change everything you know about web development.
    </p\>
  </div\>

  <ol class\="blogs"\>
    <li class\="blogs\_\_list"\>
      <a href\="blogs/typescript-new-javascript" class\="blog\_\_link"
        \>Typescript is the new Javascript</a
      \>
    </li\>

    <li class\="blogs\_\_list"\>
      <a href\="/blogs/rust-javascript-tooling" class\="blog\_\_link"
        \>Why Rust is the future of Javascript tooling</a
      \>
    </li\>

    <li class\="blogs\_\_list"\>
      <a href\="/blogs/sleep-more" class\="blog\_\_link"
        \>Why you should sleep more</a
      \>
    </li\>
  </ol\>
</main\>

Then update our component styles:  
然后更新我们的组件样式：

<!-- 📂 src/pages/index.astro -->
...
<style\>
  ... .featured-blogs {
    margin: 0;
    padding: 3rem 0 0 0;
  }
  .featured-blogs\_\_title {
    font-size: 2rem;
    color: var(\--gray-900);
  }

  .featured-blogs\_\_description {
    margin-top: \-1.2rem;
  }

  .blogs {
    font-size: 1rem;
    font-weight: 500;
  }

  .blogs\_\_list {
    border-bottom: 1px solid;
    border-color: var(\--gray-200);
  }

  .blog\_\_link {
    opacity: 1;
    height: 100%;
    display: block;
    padding: 1rem 0;
    color: var(\--gray-200);
    text-decoration: none;
    transition: opacity 0.2s ease-in-out;
  }

  .blog\_\_link:hover {
    opacity: 0.7;
  }
</style\>

This isn’t necessarily a wrong approach to getting this done. We will now have a list of the blogs, as expected.  
这并不一定是一个错误的方法来完成这件事。我们现在将有一个博客列表，正如预期的。

[![The rendered blog list.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-11%20at%2012.52.18@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-11%20at%2012.52.18@2x.png)

_The rendered blog list.  
渲染的博客列表。_  
  
  

A better solution is to use `Astro.glob()` to load multiple files.  
更好的解决方案是使用 `Astro.glob()` 加载多个文件。

`Astro.glob()` accepts a single `URL` glob parameter of the files we’d like to import. `glob()` will then return an array of the exports from the matching file.  
`Astro.glob()` 接受我们想要导入的文件的一个 `URL` glob参数。 `glob()` 将返回匹配文件导出的数组。

Talk is cheap, so let’s put this into action.  
空谈是廉价的，让我们把它付诸行动吧。

Instead of manually writing out the list of blog articles, we will use `Astro.glob()` to fetch all the blog posts:  
我们不需要手动写出博客文章列表，而是使用 `Astro.glob()` 获取所有博客文章：

// 📂 src/pages/index.astro
\--\-
const blogs \= await Astro.glob<{
  poster: string;
  title: string;
  subtitle: string;
}\>("../pages/blogs/\*.md");
...
\--\-
...

*   Note the argument passed to `.glob`, i.e., `../pages/blogs/*.md`. This relative glob path represents all markdown files in the `/blogs` directory.  
    注意传递给 `.glob` 的参数，即#1。这个相对glob路径表示 `/blogs` 目录中的所有markdown文件。
*   Also note the typing provided. `.glob` implements a generic, which, in this case, represents the markdown frontmatter object type.  
    还请注意提供的类型。 `.glob` 实现了一个泛型，在本例中，它表示markdown frontmatter对象类型。
    
    {
      poster: string;
      title: string;
      subtitle: string;
    }
    

Now, we may replace the manual list with a dynamically rendered list, as shown below:  
现在，我们可以用动态渲染的列表替换手动列表，如下所示：

// 📂 src/pages/index.astro
...
  <ol\>
    {
      blogs.map((blog) \=> (
        <li class\="blogs\_\_list"\>
          <a href\={blog.url} class\="blog\_\_link"\>
            {blog.frontmatter.title}
          </a\>
        </li\>
      ))
    }
  </ol\>

*   Dynamically render the blog list using the `.map` array function.  
    使用 `.map` array函数动态呈现博客列表。
*   `Astro.glob()` returns markdown properties including frontmatter and `url` where `blog.url` refers to the browser url path for the markdown file.  
    `Astro.glob()` 返回markdown属性，包括frontmatter和 `url` ，其中 `blog.url` 引用markdown文件的浏览器url路径。

And voila! Same result with a much neater implementation.  
瞧！相同的结果与一个更整洁的实现。

* * *

[](#deploying-a-static-astro-site)Deploying a static Astro site  
部署静态Astro站点
-----------------------------------------------------------------------------

We’ve come a long way! Now, let’s deploy this baby to the wild.  
我们走了很长的路！现在，让我们把这个宝贝放到野外。

Deploying a static website is relatively the same regardless of the technology used to create the site.  
部署静态网站是相对相同的，无论用于创建网站的技术。

At the end of your deployment build, we’ll have static assets to deploy to any service we choose.  
在部署构建结束时，我们将有静态资产部署到我们选择的任何服务。

[![Generating production builds.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/generate-prod-build.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/generate-prod-build.png)

_Generating production builds.  
正在生成生产构建。_  
  
  

Once this is done, we must wire up a static web server to serve this content when your users visit the deployed site.  
完成后，我们必须连接一个静态Web服务器，以便在用户访问部署的站点时提供这些内容。

NB: a static web server is a web server that serves static content. It essentially serves any files (e.g., HTML, CSS, JS) the client requests.  
注意：静态Web服务器是提供静态内容的Web服务器。它本质上服务于任何文件（例如，HTML、CSS、JS）。

This breaks down the process of deploying a static website into two:  
这将静态网站的部署过程分为两个：

(1) Create the static production assets (2) Serve the static assets via a static web server  
(1)创建静态生产资产（2）通过静态Web服务器提供静态资产

Let’s do these. 让我们做这些。

### [](#1-create-static-production-assets)1\. Create static production assets  
1.创建静态生产资产

To build our application for production, run the command:  
要构建用于生产的应用程序，请运行以下命令：

npm run build

This will internally run the `astro build` command and build our application production static assets.  
这将在内部运行 `astro build` 命令并构建我们的应用程序生产静态资产。

By default, these assets will exist in the `dist` folder.  
默认情况下，这些资源将存在于 `dist` 文件夹中。

### [](#2-serve-the-static-assets-via-a-static-web-server)2\. Serve the static assets via a static web server  
2.通过静态Web服务器提供静态资产

Choosing a web server will come down to your choice. I’ll go ahead and explain how to use Netlify. However, the steps you must take with your web server provider will look similar.  
选择Web服务器将取决于您的选择。我将继续解释如何使用Netlify。但是，您必须对您的Web服务器提供商执行的步骤看起来类似。

Go over to Netlify and create an account.  
转到Netlify并创建一个帐户。

[![The Netlify homepage.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-01-25%20at%2004.51.46@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-01-25%20at%2004.51.46@2x.png)

_The Netlify homepage. Netlify主页。_  
  
  

Once you create an account and sign in, you’ll find a manual section to deploy a site.  
创建帐户并登录后，您将找到用于部署站点的手册部分。

[![The Netlify dashboard.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-01-25%20at%2004.56.37@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-01-25%20at%2004.56.37@2x.png)

_The Netlify dashboard. Netlify仪表板。_  
  
  

Now, click `browse to upload` and upload the `dist` folder containing our static production assets.  
现在，单击 `browse to upload` 并上传包含静态生产资产的 `dist` 文件夹。

Once the upload is completed, you’ll have your site deployed with a random public URL, as shown below:  
上传完成后，您将使用随机的公共URL部署您的站点，如下所示：

[![Deployed Netlify site URL.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-01-25%20at%2004.57.57@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-01-25%20at%2004.57.57@2x.png)

_Deployed Netlify site URL.  
已部署Netlify站点URL。_  
  
  

Visit the URL to view your newly deployed website!  
访问URL以查看您新部署的网站！

[](#the-problem-with-manual-deployments)The problem with manual deployments  
手动部署的问题
-------------------------------------------------------------------------------------

Manual deployments are great for conceptually breaking down the process of deploying a static website.  
手动部署对于从概念上分解静态网站的部署过程非常有用。

However, in the real world, you may find this less optimal.  
然而，在真实的世界中，你可能会发现这不是最佳的。

The main challenge here is that every change made to your website requires you to build the application and re-upload it to your server manually.  
这里的主要挑战是，对您的网站所做的每一次更改都需要您构建应用程序并手动重新上传到您的服务器。

[![Manually redeploying after new changes.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/manual-redeployment.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/manual-redeployment.png)

_Manually redeploying after new changes.  
在新更改后手动重新部署。_  
  
  

This is a well-known problem with a standardised solution. The solution involves automating the entire process of deploying static websites by connecting your website to a git provider.  
这是标准化解决方案中众所周知的问题。该解决方案包括通过将网站连接到git提供商来自动化部署静态网站的整个过程。

[](#automating-the-deployment-of-a-static-website)Automating the deployment of a static website  
自动部署静态网站
----------------------------------------------------------------------------------------------------------

Automating the deployment of a static website looks something like this:  
自动部署静态网站看起来像这样：

**Step 1**: Write and push your code to a Git provider like GitHub. **Step 2**: Connect the GitHub project to your static web server provider, e.g., Netlify. **Step 3**: You provide your website’s `build` command and the location of the built assets to your web server provider, e.g., Netlify. **Step 4**: Your web server provider automatically runs the build command and serves your static assets. **Step 5**: Anytime you make changes to the GitHub project, your web server provider picks up the changes and reruns step 4, i.e., automatically deploying your website changes.  
步骤1：编写代码并将其推送给Git提供商，比如GitHub。步骤2：将GitHub项目连接到静态Web服务器提供商，例如：Netlify步骤3：您向您的Web服务器提供商提供网站的 `build` 命令和构建资产的位置，例如：Netlify第4步：您的Web服务器提供商自动运行build命令并提供静态资产。步骤5：每当您对GitHub项目进行更改时，您的Web服务器提供商会接收更改并重新运行步骤4，即：自动部署您的网站更改

To see this process in practice with Netlify, go over [to your dashboard](https://app.netlify.com/start) and connect a Git provider (step 1).  
要在Netlify的实践中看到这个过程，请转到您的仪表板并连接Git提供程序（步骤1）。

[![Netlify: connecting a Git provider.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-01-25%20at%2005.46.08@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-01-25%20at%2005.46.08@2x.png)

_Netlify: connecting a Git provider.  
Netlify：连接Git提供程序。_  
  
  

I’ll go ahead to select Github, authorise Netlify and select the GitHub project (step 2).  
我将继续选择Github，授权Netlify并选择GitHub项目（步骤2）。

[![Netlify: selecting the Github project.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-01-25%20at%2005.47.23@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-01-25%20at%2005.47.23@2x.png)

_Netlify: selecting the Github project.  
Netlify：选择Github项目。_  
  
  

Once that’s selected, provide the settings for your application deployment (Step 3). By default, Netlify will suggest the `build` and `publish directory`. Check these to make sure there are no errors.  
选择后，提供应用程序部署的设置（步骤3）。默认情况下，Netlify会建议使用 `build` 和 `publish directory` 。检查这些以确保没有错误。

[![Netlify: suggested build command and publish directory.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-01-25%20at%2005.49.46@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-01-25%20at%2005.49.46@2x.png)

_Netlify: suggested build command and publish directory.  
Netlify：建议的构建命令和发布目录。_  
  
  

Hit deploy, and your site will be live in seconds (step 4).  
点击部署，您的网站将在几秒钟内上线（步骤4）。

To see the redeployment after a new change, push a new change to the connected git repository.  
要查看新更改后的重新部署，请将新更改推送到连接的git存储库。

[](#how-fast-is-our-astro-website)How fast is our Astro website?  
我们的Astro网站有多快？
---------------------------------------------------------------------------------

Astro boasts of insanely fast websites compared to frameworks like React or Vue.  
与React或Vue等框架相比，Astro拥有速度惊人的网站。

Let’s put this to the test by following the steps below:  
让我们通过以下步骤来测试这一点：

*   Visit the newly deployed website on Chrome.  
    访问Chrome上新部署的网站。
*   Open the Chrome developer tools.  
    打开Chrome开发者工具。
*   Go to the Lighthouse tab.  
    转到Lighthouse选项卡。
*   Analyse the page load.  
    分析页面负载。

[![Analysing page load via lighthouse.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-11%20at%2013.42.45@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-11%20at%2013.42.45@2x.png)

_Analysing page load via lighthouse.  
通过灯塔分析页面负载。_  
  
  

Here’s my result running the test:  
下面是我运行测试的结果：

[![Lighthouse 100% scores.](/understanding-astro/understanding-astro-book/raw/master/images/ch1/CleanShot%202023-05-11%20at%2013.44.24@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch1/CleanShot%202023-05-11%20at%2013.44.24@2x.png)

_Lighthouse 100% scores. 灯塔100%得分。_  
  
  

If this were a school examination, we would have just scored A+ on performance without trying!  
如果这是学校的考试，我们不试就得了A+的表现！

This is a fast website!  
这是一个快速的网站！

Feel free to run the test on other pages!  
请随意在其他页面上运行测试！

[](#conclusion)Conclusion 结论
----------------------------

This has been a lengthy discourse on Astro! We’ve delved into building a project and learned a handful of Astro’s capabilities, from installation to project structure to the nuances of inline scripts and, eventually, project deployment.  
这是一篇关于Astro的长篇演讲！我们深入研究了如何构建一个项目，并学习了Astro的一些功能，从安装到项目结构，到内联脚本的细微差别，最终，项目部署。

Why stop here? We’ve only just scratched the surface.  
为什么停在这里？我们才刚刚触及表面。

Footnotes 页签
------------

1.  For other editors, please see the official Astro site [https://docs.astro.build/en/editor-setup/](https://docs.astro.build/en/editor-setup/) [↩](#user-content-fnref-1-aa56f548e078749351c130450542ff17)  
    有关其他编辑器，请参阅Astro官方网站https://docs.astro.build/en/editor-setup/
    
2.  What is a “.d.ts” file in Typescript? [https://medium.com/@ohansemmanuel/what-is-a-d-ts-file-in-typescript-2e2d90d58eca](https://medium.com/@ohansemmanuel/what-is-a-d-ts-file-in-typescript-2e2d90d58eca) [↩](#user-content-fnref-2-aa56f548e078749351c130450542ff17)  
    Typescript中的“.d.ts”文件是什么？https://medium.com/@ohansemmanuel/what-is-a-d-ts-file-in-typescript-2e2d90d58eca www.example
    
3.  As we’ll see later, they can also be used in .mdx files. [↩](#user-content-fnref-3-aa56f548e078749351c130450542ff17)  
    正如我们稍后将看到的，它们也可以在.mdx文件中使用。 ↩
    
4.  Don’t know CSS variables? Read my guide [https://medium.com/free-code-camp/everything-you-need-to-know-about-css-variables-c74d922ea855](https://medium.com/free-code-camp/everything-you-need-to-know-about-css-variables-c74d922ea855) [↩](#user-content-fnref-4-aa56f548e078749351c130450542ff17)  
    不知道CSS变量吗？阅读我的指南https://medium.com/free-code-camp/everything-you-need-to-know-about-css-variables-c74d922ea855 ↩
    
5.  What is Markdown? [https://en.wikipedia.org/wiki/Markdown](https://en.wikipedia.org/wiki/Markdown) [↩](#user-content-fnref-5-aa56f548e078749351c130450542ff17)  
    什么是Markdown？https://en.wikipedia.org/wiki/Markdown第0#页
    
6.  The markdown syntax cheatsheet [https://www.markdownguide.org/cheat-sheet/](https://www.markdownguide.org/cheat-sheet/) [↩](#user-content-fnref-6-aa56f548e078749351c130450542ff17)  
    Markdown语法秘籍https://www.markdownguide.org/cheat-sheet/
    
7.  Markdown layout properties: [https://docs.astro.build/en/core-concepts/layouts/#markdown-layout-props](https://docs.astro.build/en/core-concepts/layouts/#markdown-layout-props) [↩](#user-content-fnref-7-aa56f548e078749351c130450542ff17)  
    Markdown布局属性：https://docs.astro.build/en/core-concepts/layouts/#markdown-layout-props第0#页
    
