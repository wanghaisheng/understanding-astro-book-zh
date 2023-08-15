
[](#-understanding-astro)🚀 Understanding Astro  
🚀 了解Astro
============================================================

By [Ohans Emmanuel](https://www.ohansemmanuel.com/) 作者：Ohans Emmanuel

  

[](#chapter-5-oh-my-react)Chapter 5: Oh my React!  
第五章：我的反应！
-------------------------------------------------------------

Everything you need to know to develop rich content websites with real-world best practices. This is a practical section best served with you coding along.  
您需要知道的一切，以开发具有真实世界最佳实践的丰富内容网站。这是一个实用的部分，最好与您沿着编写代码。

  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch5/watch-instead@3x.png)](https://ohans.me/understanding-astro-udemy)

  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch5/view-project.png)](https://github.com/understanding-astro/react.dev-astro)

* * *

[](#what-youll-learn)What you’ll learn 您将学到的内容
----------------------------------------------

*   Styling Astro projects with Tailwind.  
    与Tailwind一起设计Astro项目。
*   Several syntax highlighting solutions for Astro.  
    Astro的几种语法高亮解决方案。
*   Leveraging content collections for scalable and type-safe development.  
    利用内容集合进行可伸缩和类型安全的开发。
*   Understand dynamic routing in Astro.  
    了解Astro中的动态路由。

* * *

[](#set-up-the-starter-project)Set up the starter project  
设置启动器项目
-------------------------------------------------------------------

We’ve spent ample time learning the ins and outs of building static websites with Astro. So, in this chapter, we will not start from scratch.  
我们已经花了大量的时间来学习如何使用Astro构建静态网站。因此，在本章中，我们不会从头开始。

Instead, we’ll begin with a basic static project we’ll build upon throughout the chapter.  
相反，我们将从一个基本的静态项目开始，我们将在整个章节中建立。

[![Building from a starter project.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/project-shell.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/project-shell.png)

_Building from a starter project.  
从启动项目生成。_  
  
  

In this chapter, we will adopt a solution-oriented approach similar to that of detectives. We aim to solve various `TODOs` scattered throughout the starter project.  
在这一章中，我们将采用一种类似于侦探的以解决方案为导向的方法。我们的目标是解决分散在整个启动项目中的各种 `TODOs` 。

[![Solving small isolated problems.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/todos.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/todos.png)

_Solving small isolated problems.  
解决孤立的小问题。_  
  
  

The reason for this is to ignore already learned concepts and focus on learning new concepts or consolidating older concepts via practice — solving isolated problems.  
这样做的原因是忽略已经学过的概念，而专注于学习新概念或通过实践解决孤立的问题来巩固旧概念。

To get started, go ahead and clone the project:  
要开始，请继续克隆项目：

git clone https://github.com/understanding-astro/react.dev-astro.git

Then change directories:  
然后更改目录：

cd react.dev-astro

Finally, checkout to the `clean-slate` branch I’ve prepared so we can systematically build upon the base application.  
最后，签出到我准备好的 `clean-slate` 分支，这样我们就可以系统地构建基本应用程序。

git checkout clean-slate

[](#installing-dependencies)Installing dependencies 正在安装依赖项
-----------------------------------------------------------

Go ahead and install the project’s dependencies via the following:  
继续并通过以下方式安装项目的依赖项：

npm install

Then install the Astro `react` integration:  
然后安装Astro `react` 集成：

npx astro add react

When prompted, type “y” to accept each prompt. “y” means “yes”!  
出现提示时，键入“y”以接受每个提示。“y”表示“是”！

The complete installation will add all relevant react dependencies and updates the `astro.config.mjs` project configuration file.  
完整的安装将添加所有相关的react依赖项并更新 `astro.config.mjs` 项目配置文件。

[![Installing the React integration and dependencies.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-23%20at%2008.11.48.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-23%20at%2008.11.48.png)

_Installing the React integration and dependencies.  
安装React集成和依赖项。_  
  
  

Finally, go ahead and install the `mdx` integration. I’ll describe the what and why later in the chapter. For now, go ahead and install the integration by running the following:  
最后，继续安装 `mdx` 集成。我将在本章的后面描述是什么和为什么。现在，通过运行以下命令继续安装集成：

npx astro add mdx

This will install the `@astrojs/mdx` integration and also update the `astro.config.mjs` project configuration file.  
这将安装 `@astrojs/mdx` 集成并更新 `astro.config.mjs` 项目配置文件。

[![Installing the MDX integration.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-23%20at%2008.13.42.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-23%20at%2008.13.42.png)

_Installing the MDX integration.  
安装MDX集成。_  
  
  

Now run the application:  
现在运行应用程序：

npm start

This will run the application in an available local port e.g., the default `localhost:3000`.  
这将在可用的本地端口中运行应用程序，默认值 `localhost:3000` 。

Visit the local server and you’ll find the base unstyled application running in the browser as shown below:  
访问本地服务器，您会发现在浏览器中运行的基本无样式应用程序，如下所示：

[![The unstyled homepage.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-23%20at%2008.16.14.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-23%20at%2008.16.14.png)

_The unstyled homepage. 无样式的主页。_  
  
  

I’ve got to say that’s one ugly-looking page.  
我不得不说这是一个丑陋的页面。

We’ll fix that next.  
我们下一个会解决的。

[](#styling-astro-projects-with-tailwind)Styling Astro projects with Tailwind  
使用Tailwind设计Astro项目
---------------------------------------------------------------------------------------------------

Love or hate it, CSS is how we make beautiful web applications.  
不管你喜不喜欢，CSS是我们制作漂亮的Web应用程序的方式。

In Chapter One, we wrote the styles for the personal website by hand i.e., by writing out every CSS declaration, however, in this chapter, we will use a CSS framework called Tailwind.  
在第一章中，我们手工编写了个人网站的样式，即，通过写出每一个CSS声明，然而，在本章中，我们将使用一个叫做Tailwind的CSS框架。

So, what’s Tailwind? 顺风是什么

An overly simple definition would be, Tailwind is the modern [bootstrap](https://getbootstrap.com/). Never used Bootstrap? Then think of Tailwind as a utility-first CSS framework that provides class names like `flex`, `text-lg`, `items-center` and many more that you can apply to your markup for styles.  
一个过于简单的定义是，顺风是现代的引导。从未使用过Bootstrap？然后将Tailwind视为一个实用程序优先的CSS框架，它提供了诸如 `flex` ， `text-lg` ， `items-center` 等类名，您可以将其应用于样式标记。

Tailwind will enable us to build modern-looking websites — fast.  
Tailwind将使我们能够快速构建现代外观的网站。

### [](#installing-tailwind)Installing Tailwind 安装尾风

Keep the project running in your terminal and open another terminal tab. Run the following install command:  
保持项目在终端中运行，并打开另一个终端选项卡。运行以下安装命令：

npx astro add tailwind

This will install the Astro tailwind integration in the project and update the project configuration.  
这将在项目中安装Astro tailwind集成并更新项目配置。

[![Installing the Astro Tailwind integration.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-24%20at%2008.16.12.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-24%20at%2008.16.12.png)

_Installing the Astro Tailwind integration.  
安装Astro Tailwind集成。_  
  
  

Once the installation is complete, the existing application styles will now take effect. Visit the application on your local port to see the styled application.  
安装完成后，现有的应用程序样式现在将生效。访问本地端口上的应用程序以查看样式化的应用程序。

[![The styled application.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-24%20at%2008.17.17.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-24%20at%2008.17.17.png)

_The styled application. 样式化的应用程序。_  
  
  

What a difference styling makes!  
风格的不同！

Take your time and browse the different pages of the styled application.  
慢慢浏览样式化应用程序的不同页面。

### [](#how-does-tailwind-work)How does Tailwind work?  
Tailwind是如何工作的？

Using Tailwind in Astro is straightforward. Install the Tailwind integration and provide a `class` attribute with Tailwind utility classes in your component markup.  
在Astro中使用Tailwind很简单。安装Tailwind集成并在组件标记中提供带有Tailwind实用程序类的 `class` 属性。

For example, consider the styled text “The library for web and native user interfaces” on the project homepage:  
例如，考虑项目主页上的样式文本“The library for web and native user interfaces”：

[![The homepage subtitle.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-03%20at%2006.50.11@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-03%20at%2006.50.11@2x.png)

_The homepage subtitle. 主页字幕。_  
  
  

Now, consider the code responsible for the styles:  
现在，考虑负责样式的代码：

// pages/index.astro
// ...
<p class\="max-w-lg py-1 text-center font-display text-4xl leading-snug text-secondary dark:text-primary-dark md:max-w-full"\>
  The library for web and native user interfaces
</p\>

In the example above, the classes applied are as shown below:  
在上面的例子中，应用的类如下所示：

"max-w-lg py-1 text-center font-display text-4xl leading-snug text-secondary
dark:text-primary-dark md:max-w-full"

While this is not a Tailwind book, it’s only fair to give a general explanation of what’s going on here.  
虽然这不是一本顺风的书，但对这里发生的事情给予一般性的解释是公平的。

Firstly, most Tailwind utility classes are well-named and you can infer what they do. Others might not.  
首先，大多数Tailwind工具类都有很好的名称，您可以推断出它们的作用。其他人可能不会。

If you’re coding along in VSCode, I recommend installing the official Tailwind integration:  
如果你在VSCode中编码，我建议你安装官方的Tailwind集成：

[![Installing the official VSCode Tailwind plugin.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-03%20at%2006.55.50@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-03%20at%2006.55.50@2x.png)

_Installing the official VSCode Tailwind plugin.  
安装官方VSCode Tailwind插件。_  
  
  

If you’re not using VSCode, consider finding your [editor setup](https://tailwindcss.com/docs/editor-setup) in the official Tailwind docs.  
如果您没有使用VSCode，请考虑在官方Tailwind文档中查找编辑器设置。

Installing the integration brings a lot of benefits. The important benefit I’d love to highlight here is you can hover over any of the Tailwind utility classes to see the exact CSS property value the class corresponds to.  
安装集成带来了很多好处。我想在这里强调的重要好处是，您可以将鼠标悬停在任何Tailwind实用程序类上，以查看该类对应的确切CSS属性值。

For example, hovering over the `max-w-lg` displays the css property value for the utility class as shown below:  
例如，将鼠标悬停在 `max-w-lg` 上会显示实用程序类的css属性值，如下所示：

.max-w-lg {
  max-width: 32rem /\* 512px \*/;
}

[![Hovering over Tailwind classes.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-03%20at%2006.58.37@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-03%20at%2006.58.37@2x.png)

_Hovering over Tailwind classes.  
盘旋在顺风班上空。_  
  
  

This is very helpful because you can now inspect whatever classes are added to any markup in the project!  
这是非常有帮助的，因为现在您可以检查项目中添加到任何标记中的任何类！

### [](#tailwind-configuration)Tailwind configuration 顺风布局

Upon installing Tailwind, it ships with its default theme.  
安装Tailwind后，它将附带默认主题。

It’s not a bad theme, however, when you build projects, you likely want control over the project theme.  
这不是一个坏的主题，但是，当您构建项目时，您可能希望控制项目主题。

In our example, we want a theme that models the official React documentation theme.  
在我们的示例中，我们需要一个模拟官方React文档主题的主题。

To customise Tailwind, we can provide a `tailwind.config.js` file where we can define our project’s fonts, colour palette, type scale, border radius values, breakpoints and much more.  
要自定义Tailwind，我们可以提供一个 `tailwind.config.js` 文件，在其中我们可以定义项目的字体，调色板，类型比例，边界半径值，断点等等。

Look at the `tailwind.config.cjs` file in the project’s root. This is where the project’s tailwind configuration magic happens.  
查看项目根目录中的 `tailwind.config.cjs` 文件。这就是项目顺风配置魔法发生的地方。

For more details on customising Tailwind, please consult the [official documentation](https://tailwindcss.com/docs/theme).  
有关定制Tailwind的更多详细信息，请参阅官方文档。

[](#typescript-import-alias)Typescript import alias Typescript导入别名
------------------------------------------------------------------

Let’s be honest, no one likes those ugly relative imports, eh?  
老实说，没有人喜欢那些丑陋的进口货，嗯？

import MyComponent from '../../components/MyComponent.astro

Ugh!! 啊！

C’mon, we can do better.  
来吧，我们可以做得更好。

This is where import aliases come in. The easiest way to get this set up in an Astro project is to define the aliases in the `tsconfig.json` file.  
这就是导入别名的用武之地。在Astro项目中进行此设置的最简单方法是在 `tsconfig.json` 文件中定义别名。

For example, we may do the following:  
例如，我们可以执行以下操作：

// 📂 tsconfig.json

{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@components/\*": \["src/components/\*"\],
    }
  }
}

We’re essentially mapping any directories in the `src/components` import path to `@components`.  
我们实际上是将 `src/components` 导入路径中的所有目录映射到 `@components` 。

Now, wait for it.  
现在，等着瞧。

The result of this is we can take our previous ugly import path and turn it into a work of art as shown below:  
这样做的结果是，我们可以采用之前丑陋的导入路径，并将其转化为艺术品，如下所示：

// Before
import MyComponent from '../../components/MyComponent.astro
// After
import MyComponent from '@components/MyComponent.astro'

Beautiful and clean, isn’t it?  
又漂亮又干净，不是吗？

The reason I mention this is the starter project has been set up to use import aliases. So, don’t get confused.  
我提到这一点的原因是启动器项目已经设置为使用导入别名。所以，别搞糊涂了。

Go ahead and look in the `tsconfig.json` file where you’ll find the following import aliases:  
继续查看 `tsconfig.json` 文件，您将在其中找到以下导入别名：

"paths": {
   "@components/\*": \["src/components/\*"\],
   "@layouts/\*": \["src/layouts/\*"\],
   "@utils/\*": \["src/utils/\*"\]
}

You’re welcome 😉 不客气 😉

[](#islands--colocating-page-components)Islands & colocating page components  
孤岛和共定位页面组件
-----------------------------------------------------------------------------------------

We’ve learned that appropriate file types in the `src/pages` directory get transformed into HTML pages.  
我们已经了解到 `src/pages` 目录中的适当文件类型会被转换为HTML页面。

However, what if we need to have some files collocated in the `src/pages` directory without being transformed into accompanying `HTML` pages?  
但是，如果我们需要将一些文件放在 `src/pages` 目录中，而不被转换为附带的 `HTML` 页面，该怎么办？

[![Colocating files in the pages directory.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/exclude_page_intro.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/exclude_page_intro.png)

_Colocating files in the pages directory.  
在pages目录中共置文件。_  
  
  

This can be helpful for collocating tests, utilities and components along the associating pages.  
这对于在关联页面中搭配测试、实用程序和组件很有帮助。

Well, there’s a solution for that.  
有个解决办法

To exclude a valid page file type in the `src/pages` directory from being compiled into an associating HTML page, prefix the file name with an underscore `_`.  
要排除 `src/pages` 目录中的有效页面文件类型，使其无法编译到关联的HTML页面中，请在文件名前面加上下划线 `_` 。

[![Prefix file name with a underscore to not transform into HTML pages.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/prefix_exclude_page.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/prefix_exclude_page.png)

_Prefix file name with a underscore to not transform into HTML pages.  
在文件名前面加上下划线，以避免转换为HTML页面。_  
  
  

For example, take a look at the `pages/_components/Home` directory in the project.  
例如，查看项目中的 `pages/_components/Home` 目录。

This directory contains a handful of components that aren’t meant to be reusable across the project. They only exist to be used on the project’s homepage.  
这个目录包含了一些不打算在整个项目中重用的组件。它们只存在于项目的主页上。

To exclude these from being separate browser pages, note how the `_components` directory is named.  
要将这些页面从单独的浏览器页面中排除，请注意 `_components` 目录是如何命名的。

As an example, if you visited `/_components/Home/Code` in the browser, this will return a `404`. Even though the `Code` components exist, it is not a page.  
例如，如果您在浏览器中访问了 `/_components/Home/Code` ，则会返回 `404` 。虽然 `Code` 组件存在，但它不是一个页面。

Now, let’s bring our knowledge of collocated components and Astro islands together to solve our first TODO in the project.  
现在，让我们将我们对配置组件和Astro岛的知识结合起来，来解决项目中的第一个TODO问题。

Take a look at the `index.astro` and consider the `TODO` to render the `Video` React component as shown below:  
看一下 `index.astro` 并考虑 `TODO` 来渲染 `Video` React组件，如下所示：

// 📂 src/pages/index.astro
❗️ <Code class\="text-white"\>TODO:</Code> (Astro Island): Render the ...

[![TODO: Render the Video React component island.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-05%20at%2008.40.18@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-05%20at%2008.40.18@2x.png)

_TODO: Render the Video React component island.  
TODO：渲染Video React组件岛。_  
  
  

Now consider the annotated solution below:  
现在考虑下面带注释的解决方案：

// 📂 src/pages/index.astro
\=\==
// Import the Video component from "\_components ..."
import { Video } from "./\_components/home/Video";
// ...
\--\-
<ExampleResultPanel slot\="right-content"\>
  {/\*\* Render the Video component. NB: this is a React component \*\*/}
   <Video
     client:visible {/\*\* 👈 Add the client directive \*\*/}
     video\={{ title: "My video", description: "Video description" }}
    /\>
</ExampleResultPanel\>

*   Render the `Video` React component  
    渲染 `Video` React组件
*   Pass a `client:visible` attribute to hydrate the island as soon as the component is visible  
    传递一个 `client:visible` 属性，以便在组件可见时立即对岛进行水合
*   Finally pass the required `video` object props to the `Video` component: `{title: "my video", description: "Video description"}`.  
    最后将所需的 `video` 对象props传递给 `Video` 组件： `{title: "my video", description: "Video description"}` 。

[![The rendered video island.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-05%20at%2008.39.19@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-05%20at%2008.39.19@2x.png)

_The rendered video island.  
渲染的视频岛。_  
  
  

Similarly, let’s resolve the second TODO. This time around we’ll render multiple `Video` components.  
同样，让我们解决第二个TODO。这次我们将渲染多个 `Video` 组件。

// 📂 src/pages/index.astro
❗️ <Code class\="text-white"\>TODO:</Code> (Astro Island): Render two ...

[![TODO: Render two React component islands.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-05%20at%2008.43.18@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-05%20at%2008.43.18@2x.png)

_TODO: Render two React component islands.  
TODO：渲染两个React组件岛。_  
  
  

Consider the solution below:  
考虑下面的解决方案：

<ExampleResultPanel slot\="right-content"\>
  <div class\="flex w-full flex-col gap-4"\>
    {/\*\* ... \*\*/}
    {/\*\* Render both islands \*\*/}
    <Video
      client:visible
      video\={{ title: "My video", description: "Video description" }}
    /\>
    <Video
      client:visible
      video\={{ title: "My video", description: "Video description" }}
    /\>
  </div\>
</ExampleResultPanel\>

[![The rendered Astro islands.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-05%20at%2008.45.15@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-05%20at%2008.45.15@2x.png)

_The rendered Astro islands.  
阿童木群岛_  
  
  

[](#syntax-highlighting)Syntax highlighting 语法突出显示
--------------------------------------------------

I never understood the intricacies of syntax highlighting until I started researching this section of the book. It’s a bliss how much’s abstracted in libraries.  
直到我开始研究这本书的这一部分，我才理解了语法突出显示的错综复杂。图书馆里有那么多抽象的东西真是太布利斯了。

Anyway, I’ll skip the nuances and provide what I believe to be the most important bits.  
无论如何，我将跳过细微差别，并提供我认为最重要的部分。

So, how do we tackle syntax highlighting in an Astro application?  
那么，我们如何在Astro应用程序中处理语法突出显示呢？

By default, Astro uses [Shiki](https://github.com/shikijs/shiki) - a syntax highlighting library under the hood, and broadly speaking, there are two ways to go about syntax highlighting your code blocks in an Astro component[1](#user-content-fn-1-7480127aa737d860f674069ffe7b7221).  
默认情况下，Astro使用Shiki -一个隐藏在引擎盖下的语法高亮库，一般来说，有两种方法可以在Astro组件 [1](#user-content-fn-1-7480127aa737d860f674069ffe7b7221) 中对代码块进行语法高亮。

Let’s have a look at these.  
让我们看看这些。

### [](#the-default-code-component)The default Code component  
默认的代码组件

Astro ships with a `<Code />` component that provides syntax highlights at build time.  
Astro附带了一个 `<Code />` 组件，在构建时提供语法突出显示。

[![The Code component renders to HTML and inline styles without any Javascript.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/code_component.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/code_component.png)

_The Code component renders to HTML and inline styles without any Javascript.  
Code组件渲染为HTML和内联样式，而不使用任何JavaScript。_  
  
  

By implication, there’s no runtime overhead to this method of syntax highlighting as no computations are done at runtime and the eventual result is a bunch of elements with inline styles.  
这意味着，这种语法高亮显示的方法没有运行时开销，因为在运行时不进行计算，最终结果是一堆具有内联样式的元素。

This is powered by Shiki.  
这是由Shiki提供的。

[![Sample syntax highlighted DOM output.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-25%20at%2008.35.52.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-25%20at%2008.35.52.png)

_Sample syntax highlighted DOM output.  
示例语法突出显示的DOM输出。_  
  
  

Let’s go back to our starter project and resolve another TODO.  
让我们回到我们的启动项目并解决另一个TODO。

📂 src/pages/index.astro

// ...
❗️ <Code class\="text-white"\>TODO:</Code> Replace with Syntax highlighted code

[![TODO: Add syntax highlighted code block.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-05%20at%2016.06.25@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-05%20at%2016.06.25@2x.png)

_TODO: Add syntax highlighted code block.  
TODO：添加语法突出显示的代码块。_  
  
  

The goal here is to provide syntax-highlighted code within the component markup.  
这里的目标是在组件标记中提供语法突出显示的代码。

To solve this, we’ll leverage the `Code` component from Astro as shown in the annotated code block below:  
为了解决这个问题，我们将利用Astro的 `Code` 组件，如下面注释的代码块所示：

// 📂 src/pages/index.astro
\--\-
// import Code from "astro/components"
import { Code as AstroCode } from "astro/components";
//... other imports
\--\-

// ...Render the component and pass the code and lang string props
<div slot\="left-content"\>
  <AstroCode
            code\={\`function Video({ video }) {
  return (
    <div>
      <Thumbnail video={video} />
      <a href={video.url}>
        <h3>{video.title}</h3>
        <p>{video.description}</p>
      </a>
      <LikeButton video={video} />
    </div>
  );
}\`}
    lang\="jsx" {/\*\* 👈 code language for syntax highlighting \*\*/}
   /\>
</div\>

[![The syntax highlighted code block.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-25%20at%2013.04.02@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-25%20at%2013.04.02@2x.png)

_The syntax highlighted code block.  
语法突出显示了代码块。_  
  
  

Since the code snippets are just good old HTML DOM nodes, we can apply some styles on the parent `div` to style them further as shown below:  
由于代码片段只是很好的旧HTML DOM节点，我们可以在父节点 `div` 上应用一些样式来进一步样式化它们，如下所示：

// 📂 src/pages/index.astro
<div
   slot\="left-content"
   class\="\[&\_pre\]:!bg-transparent \[&\_pre\]:!text-sm \[&\_pre\]:!leading-6"\>
	<AstroCode ... /\>
</div\>

This will reduce the size of the font, reduce the type leading and make the code background transparent. Note that the square braces are how we write arbitrary [custom styles](https://tailwindcss.com/docs/adding-custom-styles#using-arbitrary-values) in Tailwind.  
这将减小字体的大小，减少类型前导并使代码背景透明。请注意，方括号是我们在Tailwind中编写任意自定义样式的方式。

See the results below:  
请参见下面的结果：

[![Better styled syntax highlighted code block.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-25%20at%2013.03.25@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-25%20at%2013.03.25@2x.png)

_Better styled syntax highlighted code block.  
更好的样式化语法突出显示代码块。_  
  
  

Much better, eh? 好多了，嗯？

We can go ahead and do the same for the other `TODO` :  
我们可以继续对其他 `TODO` 做同样的事情：

// 📂 src/pages/index.astro
❗️ <Code class\="text-white"\>TODO:</Code> Replace with Syntax highlighted code

Consider the identical solution below:  
考虑以下相同的解决方案：

<div
   slot\="left-content"
   {/\*\* Similar style as before. Leverages Tailwind \*\*/}
   class\="\[&\_pre\]:!bg-transparent \[&\_pre\]:!text-sm \[&\_pre\]:!leading-6"
        \>
          <AstroCode
            code\={\`function VideoList({ videos, emptyHeading }) {
  const count = videos.length;
  let heading = emptyHeading;
  if (count > 0) {
    const noun = count > 1 ? 'Videos' : 'Video';
    heading = count + ' ' + noun;
  }
  return (
    <section>
      <h2>{heading}</h2>
      {videos.map(video =>
        <Video key={video.id} video={video} />
      )}
    </section>
  );
}\`}
   lang\="jsx"
 /\>

[![The syntax highlighted code block.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-25%20at%2013.05.02@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-25%20at%2013.05.02@2x.png)

_The syntax highlighted code block.  
语法突出显示了代码块。_  
  
  

The default `Code` component also supports all the official Shiki [themes](https://github.com/shikijs/shiki/blob/main/docs/themes.md#all-themes). For example, we can change the component theme to `poimandres` as shown below:  
默认的 `Code` 组件也支持所有官方的Shiki主题。例如，我们可以将组件主题更改为 `poimandres` ，如下所示：

<AstroCode
  // ...
  lang\="jsx"
  theme\="poimandres"
/\>

[![The poimandres theme.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-25%20at%2013.15.33@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-25%20at%2013.15.33@2x.png)

_The poimandres theme. Poimandres主题。_  
  
  

Let’s consider the PROs and CONs of using the default `Code` component provided by Astro.  
让我们考虑一下使用Astro提供的默认 `Code` 组件的优点和缺点。

#### [](#pros)Pros 优点

*   Easy to use 易于使用
*   Great results for low effort  
    低投入的巨大成果
*   Lots of available themes by default  
    默认情况下有很多可用的主题

#### [](#cons)Cons 缺点

*   More work is required to customise your themes e.g., Our [www.react.dev](http://www.react.dev) clone requires its custom theme  
    需要更多的工作来定制您的主题，例如，我们的www.react.dev克隆需要其自定义主题
*   No default support for dark and light theme  
    没有默认支持黑暗和光明主题

### [](#bring-your-theme)Bring your theme 带上你的主题

Using your specific syntax themes is probably not the top on everyone’s list.  
使用特定的语法主题可能不是每个人的首选。

However, Shiki supports the same syntax for VSCode themes. For example, we could load some custom open-source VSCode theme (or build on top of it) for our code blocks.  
但是，Shiki支持VSCode主题的相同语法。例如，我们可以为我们的代码块加载一些自定义的开源VSCode主题（或在其之上构建）。

Let’s take a look at [Nightowl](https://github.com/sdras/night-owl-vscode-theme) : a VS Code dark theme for contrast for nighttime coding.  
让我们来看看Nightowl：一个VS Code黑暗主题，用于夜间编码的对比。

Go ahead and copy the code [snippet theme](https://raw.githubusercontent.com/sdras/night-owl-vscode-theme/main/themes/Night%20Owl-color-theme.json) to a `src/snippet-theme.json` file.  
继续并将代码片段主题复制到 `src/snippet-theme.json` 文件中。

Next, we’ll write a simple component to load our custom theme as shown below:  
接下来，我们将编写一个简单的组件来加载自定义主题，如下所示：

// 📂 src/components/Shiki.astro

\--\-
import type { Lang } from "shiki";

// Similar to Astro's Code component, this is built on shiki
import shiki, { getHighlighter } from "shiki";

// Similar to Astro's Code component, receive lang and code as props
type Props \= {
  lang: Lang;
  code: string;
};

const { code \= "", lang \= "jsx" } \= Astro.props;

// 👀 Load the custom theme
const theme \= await shiki.loadTheme("../../snippet-theme.json");

const highlighter \= await getHighlighter({
  theme,
  langs: \[lang\],
});
\--\-

{/\*\*
  A fragment is an available Astro component. Use Fragment to prevent unnecessary markup.
The set:html directive is used to inject an HTML string into an element e.g., similar to el.innerHTML.
\*\*/}
<Fragment
  set:html\={highlighter.codeToHtml(code, {
    lang,
  })}
/\>

Import and use the new component:  
导入并使用新组件：

// 📂 src/pages/index.astro
\--\-
import Shiki from "@components/Shiki.astro";
// ...
\--\-

// Change AstroCode to Shiki (new component)

<Shiki
 code\={\`function Video({ video }) {
  return (
    <div>
      <Thumbnail video={video} />
      <a href={video.url}>
        <h3>{video.title}</h3>
        <p>{video.description}</p>
      </a>
      <LikeButton video={video} />
    </div>
  );
}\`}
  lang\="jsx"
/\>

And there we go! We’ve successfully loaded a custom theme.  
好了我们已成功加载自定义主题。

[![Comparing the previous highlighted code with the new Night Owl theme.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-06-25%20at%2013.55.54@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-06-25%20at%2013.55.54@2x.png)

_Comparing the previous highlighted code with the new Night Owl theme.  
将以前突出显示的代码与新的Night Owl主题进行比较。_  
  
  

For more customisations, we could spend time tweaking the different theme tokens in the `snippet-theme.json` file.  
对于更多的自定义，我们可以花时间调整 `snippet-theme.json` 文件中的不同主题令牌。

#### [](#pros-1)Pros 优点

*   Flexibility: we can customise the theme tokens as granularly as needed  
    灵活性：我们可以根据需要定制主题令牌

#### [](#cons-1)Cons 缺点

*   Requires more work 需要更多的工作
*   Support for dark and light theme  
    支持明暗主题

### [](#handling-light-and-dark-themes)Handling light and dark themes  
处理明暗主题

Supporting light and dark themes in Shiki (the underlying Astro syntax highlighter) is tricky because Shiki generates themes at build time.  
在Shiki（底层Astro语法高亮器）中支持浅色和深色主题是很棘手的，因为Shiki在构建时生成主题。

At the time a user toggles the site theme, no changes will be made to the syntax highlighting since it was generated at build time.  
当用户切换站点主题时，不会对语法突出显示进行任何更改，因为它是在生成时生成的。

When working with Astro components, a simple solution is to leverage CSS variables.  
在使用Astro组件时，一个简单的解决方案是利用CSS变量。

\--\-
import { Code as AstroCode } from "astro/components";
\--\-

// Among, other properties, pass a "css-variables" theme prop to the Code component
 <AstroCode theme\="css-variables" /\>

Then provide style tokens for both dark and light themes. Remember that this should be global. For example, we may do this in the `Baselayout.astro` layout component as shown below:  
然后为深色和浅色主题提供样式标记。请记住，这应该是全球性的。例如，我们可以在 `Baselayout.astro` 布局组件中执行此操作，如下所示：

// 📂 src/layouts/BaseLayout.astro
<style is:global\>
  @media (prefers-color-scheme: dark) {
    :root {
      \--astro\-code\-color\-text: #ffffff;
      \--astro\-code\-color\-background: black;
      \--astro\-code\-token\-constant: #86d9ca;
      \--astro\-code\-token\-string: #977cdc;
      \--astro\-code\-token\-comment: #757575;
      \--astro\-code\-token\-keyword: #77b7d7;
      \--astro\-code\-token\-parameter: #ffffff;
      \--astro\-code\-token\-function: #86d9ca;
      \--astro\-code\-token\-string\-expression: #c64640;
      \--astro\-code\-token\-punctuation: #ffffff;
      \--astro\-code\-token\-link: #977cdc;
    }
  }

  :root {
    \--astro\-code\-color\-text: #24292e;
    \--astro\-code\-color\-background: #ffffff;
    \--astro\-code\-token\-constant: #032f62;
    \--astro\-code\-token\-string: #032f62;
    \--astro\-code\-token\-comment: #6a737d;
    \--astro\-code\-token\-keyword: #d73a49;
    \--astro\-code\-token\-parameter: #24292e;
    \--astro\-code\-token\-function: #6f42c1;
    \--astro\-code\-token\-string\-expression: #c64640;
    \--astro\-code\-token\-punctuation: #ffffff;
    \--astro\-code\-token\-link: #977cdc;
  }
</style\>

If dark and light theme syntax highlighting is critical for your application, take a look at the [official documentation](https://github.com/shikijs/shiki/blob/main/docs/themes.md#theming-with-css-variables) for more information.  
如果深色和浅色主题语法突出显示对您的应用程序至关重要，请查看官方文档以获取更多信息。

[](#getting-started-with-content-collections)Getting Started with Content Collections  
内容集入门
---------------------------------------------------------------------------------------------

Consider building a large application driven by a lot of content whether that’s Markdown (`/md`), MDX (`.mdx`), JSON (`.json`) or YAML (`.yaml`) files.  
考虑构建一个由大量内容驱动的大型应用程序，无论是Markdown（ `/md` ），MDX（ `.mdx` ），JSON（ `.json` ）还是YAML（ `.yaml` ）文件。

One solution to best organise the project’s content could be to save the content data in a database where we can validate the document schema and make sure the required content fits the data model we desire.  
最好地组织项目内容的一个解决方案是将内容数据保存在数据库中，我们可以在其中验证文档模式并确保所需的内容符合我们所需的数据模型。

We may visually model these as collections of data saved in a database with a predefined data schema.  
我们可以将这些可视化地建模为保存在具有预定义数据模式的数据库中的数据集合。

[![Modelling data with a predefined schema in a database.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/predefined_schema_db.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/predefined_schema_db.png)

_Modelling data with a predefined schema in a database.  
使用数据库中的预定义模式对数据建模。_  
  
  

With Astro projects, we don’t particularly need a database to store and enforce our content data models.  
对于Astro项目，我们并不特别需要一个数据库来存储和执行我们的内容数据模型。

Enter content collections.  
输入内容集合。

Regardless of the size of the Astro project, content collections are the best way to organise our content document, validate the structure of the document and also enjoy out-of-the-box Typescript support when querying or manipulating the content collection.  
无论Astro项目的规模如何，内容集合都是组织我们的内容文档、验证文档结构的最佳方式，并且在查询或操作内容集合时还可以享受开箱即用的Typescript支持。

So, what’s a content collection?  
那么，什么是内容集合？

A content collection is any top-level directory in the `src/content` folder of an Astro project.  
内容集合是Astro项目的 `src/content` 文件夹中的任何顶级目录。

[![Content collections - top directories in src/content.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/content_collections.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/content_collections.png)

_Content collections - top directories in src/content.  
内容集合-src/content中的顶级目录。_  
  
  

Note that the `src/content` directory is strictly reserved for content collections. Don’t use this directory for anything else.  
请注意， `src/content` 目录严格保留用于内容集合。不要将此目录用于任何其他用途。

Now that we know what a content collection is, the individual documents or entries within a collection are referred to as collection entries.  
现在我们知道了什么是内容集合，集合中的各个文档或条目被称为集合条目。

[![Collection entries within a single collection.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/collection_entries.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/collection_entries.png)

_Collection entries within a single collection.  
单个集合中的集合项。_  
  
  

Collection entries are documents in formats such as Markdown or MDX. They can also be in data formats such as JSON or YAML. For consistency, you’ll find most collection entries with a consistent naming pattern e.g., kebab-case.  
集合条目是Markdown或MDX等格式的文档。它们也可以是JSON或YAML等数据格式。为了保持一致性，您会发现大多数集合条目都具有一致的命名模式，例如，烤肉串的案子

### [](#what-problems-do-content-collections-solve)What Problems Do Content Collections Solve?  
内容收集解决了哪些问题？

Littering a project with different content documents and no clear structure is a surefire way to create a mess.  
在一个项目中乱丢不同的内容文档，而且没有清晰的结构，这肯定会造成混乱。

The better solution: use content collections.  
更好的解决方案：使用内容集合。

Now, content collections aim to address three main problems:  
现在，内容收集旨在解决三个主要问题：

1.  Organising documents. 整理文件。
2.  Validating the document structure e.g., validating the frontmatter properties of a markdown file.  
    验证文档结构，例如，验证markdown文件的frontmatter属性。
3.  Provides strong type safety while querying and working with content collections.  
    在查询和使用内容集合时提供强类型安全。

### [](#organising-content-collections)Organising content collections  
组织内容集合

When working with content collections, note that only top-level directories in `src/content` count as collections. For example, with multiple collections such as `blogs`, `authors` and `comments`, we could accurately represent these distinct content types with three top-level directories within `src/content`.  
使用内容集合时，请注意，只有 `src/content` 中的顶级目录才算作集合。例如，对于 `blogs` 、 `authors` 和 `comments` 等多个集合，我们可以使用 `src/content` 中的三个顶级目录准确地表示这些不同的内容类型。

[![Organising different content collections.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/content_collection_example.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/content_collection_example.png)

_Organising different content collections.  
组织不同的内容集合。_  
  
  

If there’s a need to further organise content via subdirectories within a collection, that’s entirely acceptable! For example. The `blogs` content collection may have subdirectories to organise content via languages e.g., `en`, `fr`, etc.  
如果需要通过集合中的子目录进一步组织内容，这是完全可以接受的！比如说。 `blogs` 内容集合可以具有子目录以经由语言（例如， `en` 、 `fr` 等

[![Subdirectories within content collections.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/collection_subdirectories.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/collection_subdirectories.png)

_Subdirectories within content collections.  
内容集合中的子目录。_  
  
  

### [](#authoring-content-with-mdx)Authoring content with MDX  
使用MDX创作内容

Take a look at the existing content collection in the project.  
查看项目中现有的内容集合。

What do you see?  
你看到了什么？

You should find a `blog` collection in `src/content/blog` with a handful of `.mdx` files.  
您应该在 `src/content/blog` 中找到一个 `blog` 集合，其中包含少数 `.mdx` 文件。

[![Entries in the blog collection.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-11%20at%2006.44.39.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-11%20at%2006.44.39.png)

_Entries in the blog collection.  
博客集合中的条目。_  
  
  

Each `mdx` file refers to the collection entry for the blog collection. However, what is an `mdx` file?  
每个 `mdx` 文件引用博客集合的集合条目。什么是 `mdx` 文件？

MDX touts itself as the markdown for the component era. Think, what if we could use components in markdown? Well, with `MDX`, we can!  
MDX标榜自己是组件时代的降价产品。想想看，如果我们可以在markdown中使用组件会怎么样？#00000;，我们可以！

In these files, we can import components and embed them within our standard markdown content.  
在这些文件中，我们可以导入组件并将其嵌入到标准的markdown内容中。

In the installation section of this chapter, we installed the Astro MDX plugin by running `npx astro add mdx`.  
在本章的安装部分，我们通过运行 `npx astro add mdx` 安装了Astro MDX插件。

It’s about time we got started utilising MDX.  
是时候开始使用MDX了。

### [](#configuring-content-collections)Configuring content collections  
配置内容集合

A big part of content collections is ensuring a consistent collection entry format for every content collection.  
内容集合的很大一部分是确保每个内容集合的集合条目格式一致。

For example, assuming a number markdown or MDX collection entries, we can go ahead and ensure that every collection entry has the same frontmatter properties. As you can imagine, this protects the integrity of each collection entry and breeds confidence that no surprising bug will spring at us when working with the entries.  
例如，假设一个number markdown或MDX集合条目，我们可以继续确保每个集合条目都具有相同的frontmatter属性。可以想象，这保护了每个集合条目的完整性，并培养了信心，在处理条目时不会出现令人惊讶的bug。

So, how do we ensure such consistency?  
那么，我们如何确保这种一致性呢？

The way we do this is by creating collection schemas.  
我们这样做的方法是创建集合模式。

A schema enforces consistent collection entry data within a collection. This is also what powers the Typescript support we’ll get when working with the collection entries.  
架构在集合内强制执行一致的集合条目数据。这也是我们在处理集合条目时获得的Typescript支持的强大功能。

To create our collection schema, go ahead and create a `src/content/config.ts` file with the following content:  
要创建我们的集合模式，请继续创建一个包含以下内容的 `src/content/config.ts` 文件：

// Import utilities from astro:content
import { z, defineCollection } from "astro:content";

// Define the type and schema for one or more collections
const blogCollection \= defineCollection({
  type: "content",
  // an object of strings - title, year, month, day, and intro
  schema: z.object({
    title: z.string(),
    year: z.string(),
    month: z.string(),
    day: z.string(),
    intro: z.string(),
  }),
});

// Export a single collections object to register the collections
// The key should match the collection directory name in "src/content"
export const collections \= {
  blog: blogCollection, // add the blog collection
};

Take a look at the annotated code above.  
看看上面的注释代码。

You don’t need to memorise how to do this as you can always refer to the official documentation. However, remember that the schema for a project’s content collections is defined in a `src/content/config.ts` (or `.js` and `.mjs`) file.  
您不需要记住如何做到这一点，因为您可以随时参考官方文档。但是，请记住，项目内容集合的模式是在 `src/content/config.ts` （或 `.js` 和 `.mjs` ）文件中定义的。

If we break down what goes on in a collection configuration file, we have three main actions:  
如果我们分解集合配置文件中发生的事情，我们有三个主要操作：

1.  Import utilities from `astro:content`.  
    从 `astro:content` 导入实用程序。
2.  Define the content collection(s) schema via the `z` utility.  
    通过 `z` 实用程序定义内容集合架构。
3.  Export a single object of collection name key and schema value.  
    导出集合名称键和架构值的单个对象。

The schema is the brain behind guaranteeing our content contains the right data and also provides Typescript support — autocompletion and type-checking when querying the collection.  
模式是保证我们的内容包含正确数据的大脑，还提供Typescript支持--在查询集合时自动完成和类型检查。

I know the question you’re likely asking.  
我知道你想问的问题。

What’s the `z` utility exported from `astro:content`?  
从 `astro:content` 导出的 `z` 实用程序是什么？

The `z` utility re-exports the widely popular [zod](https://github.com/colinhacks/zod) library — a TypeScript-first schema validation library with static type inference. The `z` variable in the `config` is a convenient export from `zod`.  
`z` 实用程序重新导出了广受欢迎的zod库-一个TypeScript优先的模式验证库，具有静态类型推断。 `config` 中的 `z` 变量是从 `zod` 导出的一个方便。

#### [](#quick-zod)Quick Zod 快速佐德

While this is not a Zod book, the truth remains that if we will be defining schemas with Zod, it pays to understand the basics.  
虽然这不是一本佐德的书，但事实仍然是，如果我们将用佐德定义模式，理解基础知识是值得的。

So, here’s a quick intro.  
这里有一个简短的介绍。

First, consider the schema for our `blog` collection:  
首先，考虑我们的 `blog` 集合的模式：

z.object({
  title: z.string(),
  year: z.string(),
  month: z.string(),
  day: z.string(),
  intro: z.string(),
});

Let’s deconstruct this. 让我们解构一下。

Creating a schema starts with importing Zod. With, Astro that’s done via the import from `astro:content`  
创建模式从导入Zod开始。通过从 `astro:content` 导入完成Astro

import { z } from "astro:content";

To create a schema for a string property, use the `string` method as shown below:  
要为字符串属性创建模式，请使用如下所示的 `string` 方法：

const stringSchema \= z.string();

To create an object schema, you guessed right. We use the `object` method as shown below:  
要创建对象模式，您猜对了。我们使用 `object` 方法，如下所示：

const myObjectSchema \= z.object({});

Now, within this object, we may define properties as shown below:  
现在，在这个对象中，我们可以定义如下所示的属性：

const myObjectSchema \= z.object({
  someString: z.string(),
});

In our blog collection schema, we’re essentially saying that the markdown (and MDX) files within the `blog` collection must have string front matter properties of `title`, `year`, `month`, `day` and `intro`.  
在我们的博客集合模式中，我们实际上是说 `blog` 集合中的markdown（和MDX）文件必须具有字符串前端属性 `title` 、 `year` 、 `month` 、 `day` 和 `intro` 。

The frontmatter is represented by the object schema and its properties, the object keys.  
frontmatter由对象模式及其属性（对象键）表示。

Now, go ahead and view all the collection entries in the `blog` collection and note how they all have defined properties.  
现在，继续查看 `blog` 集合中的所有集合条目，并注意它们是如何定义属性的。

#### [](#the-astro-folder)The .astro folder .astro文件夹

As you create and work with content collections, Astro creates a `.astro` directory in the root of our project to keep track of important metadata for our content collections — mostly generated type information.  
当您创建和使用内容集合时，Astro会在我们项目的根目录中创建一个 `.astro` 目录，以跟踪我们内容集合的重要元数据-主要是生成的类型信息。

It’s safe to ignore this directory.  
忽略此目录是安全的。

The `.astro` directory is updated automatically as we run `astro dev` or `astro build` commands. However, if we find the type information not in sync, we can manually run `astro sync` at any time to update the `.astro` directory manually.  
当我们运行 `astro dev` 或 `astro build` 命令时， `.astro` 目录会自动更新。但是，如果发现类型信息不同步，我们可以随时手动运行 `astro sync` 手动更新 `.astro` 目录。

[](#query-and-render-content-collections)Query and render content collections  
查询和呈现内容集合
-----------------------------------------------------------------------------------------

So, we know how to create content collections and define their schemas. What next?  
因此，我们知道如何创建内容集合并定义它们的模式。接下来呢？

Content collections exist to be consumed in some way — typically by querying and rendering the collections.  
内容集合的存在是为了以某种方式被消费-通常是通过查询和呈现集合。

So, how do we get started with this?  
那我们该怎么开始呢

A collection consists of one or more collection entries. So, to query an entire collection, Astro provides the `getCollection()` method.  
集合由一个或多个集合条目组成。因此，为了查询整个集合，Astro提供了 `getCollection()` 方法。

Consider how we may fetch all blog posts in our project:  
考虑一下我们如何获取项目中的所有博客文章：

\--\-
import { getCollection } from 'astro:content'

// Get all entries from the blog collection
const allBlogPosts \= await getCollection('blog')
\--\-

To filter the collection entries, we may pass a second function argument to `getCollection` as shown below:  
为了过滤集合条目，我们可以将第二个函数参数传递给 `getCollection` ，如下所示：

\--\-
import { getCollection } from 'astro:content'

// Get all entries from the blog collection
const allBlogPosts \= await getCollection('blog', ({data}) \=> {
  // return only blogs from a certain year
  return data.year \=== '2023'
})
\--\-

Note that in our case, the `data` above refers to the frontmatter properties of our `MDX` blog entries.  
请注意，在我们的例子中，上面的 `data` 指的是我们的 `MDX` 博客条目的frontmatter属性。

How about getting a single collection entry?  
如何获得一个单一的集合条目？

Your first inclination may be to filter as shown below:  
您的第一个倾向可能是过滤，如下所示：

\--\-
import { getCollection } from 'astro:content'

// Get all entries from the blog collection
const allBlogPosts \= await getCollection('blog', ({data}) \=> {
  // return only a specific title
  return data.title \=== 'my-single-blog-title"
})
---

The above is technically valid. However, Astro provides a `getEntry()` method specifically for this case.  
以上内容在技术上是有效的。然而，Astro提供了专门针对这种情况的 `getEntry()` 方法。

Consider the usage below:  
考虑下面的用法：

import { getEntry } from "astro:content";

// Get a single blog entry with the entry slug
const blog \= await getEntry("blog", "introduction-to-react");

The example above will fetch the entry in the `src/content/blog/introduction-to-react.mdx` route.  
上面的示例将获取 `src/content/blog/introduction-to-react.mdx` 路由中的条目。

Note that both `getCollection` and `getEntry` return a [CollectionEntry](https://docs.astro.build/en/reference/api-reference/#collection-entry-type) type.  
请注意， `getCollection` 和 `getEntry` 都返回CollectionEntry类型。

Enough with the theory, let’s get back to building our project.  
理论到此为止，让我们继续构建我们的项目吧。

Find the next TODO on the `blog/index.astro` page:  
在 `blog/index.astro` 页面上找到下一个TODO：

📂 src/pages/blog/index.astro

<!\-- ❗️TODO: List and render (all) blog post cards \--\>

The goal is to fetch all the blogs in the blog content collection and render visual cards for each entry. Also, note that clicking each card should point to the actual blog.  
目标是获取博客内容集合中的所有博客，并为每个条目呈现可视卡片。另外，请注意，单击每张卡片应该指向实际的博客。

[![Rendering blog post cards.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-10%20at%2005.49.23.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-10%20at%2005.49.23.png)

_Rendering blog post cards.  
渲染博客明信片。_  
  
  

Consider the solution below:  
考虑下面的解决方案：

📂 src/pages/blog/index.astro

\--\-
// Import getCollection from astro:content
import { getCollection } from "astro:content";
// Import the BlogCard visual component
import BlogCard from "@components/BlogCard.astro";
// Import the getMonthName utility
import { getMonthName } from "@utils/getMonthName";

// Fetch all the blog posts
const allBlogPosts \= await getCollection("blog");
\--\-

{/\*\* render all blog posts \*\*/}
  <div class\="mt-12 flex flex-col gap-5 px-5 sm:-mx-5 lg:px-4"\>
    {
      allBlogPosts.map(({ data, slug }) \=> {
        const url \= \`/blog/${data.year}/${data.month}/${data.day}/${slug}\`;

        return (
          <BlogCard
            url\={url}
            date\={\`${getMonthName(+data.month)} ${data.day}, ${data.year}\`}
            title\={data.title}
          \>
            {data.intro}
          </BlogCard\>
        );
      })
    }
  </div\>

Note the URL of each blog constructed in the solution above:  
注意上面的解决方案中构建的每个博客的URL：

const url \= \`/blog/${data.year}/${data.month}/${data.day}/${slug}\`;

For example, the blog collection entry `data-fetching-with-react-server-components.mdx` will have the path: `/blog/2020/12/21/data-fetching-with-react-server-components`.  
例如，博客集合条目 `data-fetching-with-react-server-components.mdx` 将具有如下路径：#1。

Go ahead and click any of the blog cards. At the moment, they should lead to an empty page.  
继续，点击任何博客卡片。目前，它们应该导致一个空白的页面。

Let’s resolve that. 让我们解决这个问题。

[](#dynamic-routing)Dynamic routing 动态路由
----------------------------------------

Static routes are arguably easy to reason about. For example, `.astro`, `.md` and `.mdx` files in `src/pages` will automatically become pages on our website.  
静态路由可以说很容易推理。例如， `src/pages` 中的 `.astro` 、 `.md` 和 `.mdx` 文件将自动成为我们网站上的页面。

However, sometimes we require dynamic routes to prevent repetition. This typically happens when we have different routes with minimal UI changes between them.  
然而，有时我们需要动态路由来防止重复。这通常发生在我们有不同的路由，它们之间的UI变化最小的时候。

For example, consider our current project. The blogs will have different routes, but each blog’s look and feel are identical.  
例如，我们现在的项目。博客将有不同的路线，但每个博客的外观和感觉是相同的。

// example routes for different blogs
/blog/2020/12/21/data\-fetching\-with\-react\-server\-components
/blog/2023/04/24/some\-other\-blog\-title
/blog/2023/07/12/getting\-started\-with\-react

// 👀 Manually creating multiple pages for each blog
/pages/2020/12/21/data\-fetching\-with\-react\-server\-components.astro
/pages/2023/04/24/some\-other\-blog\-title.astro
/pages/2023/07/12/getting\-started\-with\-react.astro

Manually providing multiple pages for each blog is arguably tedious.  
手动为每个博客提供多个页面可以说是乏味的。

Instead of manually creating different pages to represent each blog, we may dynamically handle the routing in one of two ways.  
我们不需要手动创建不同的页面来表示每个博客，而是可以用两种方式之一动态地处理路由。

### [](#1-named-parameters)1\. Named parameters 1.命名参数

The URL structure of the blogs could be represented by `/${year}/${month}/${day}/${title}` where `title` represents the blog’s title and `year`, `month` and `day`, describe when the blog was published.  
博客的URL结构可以用 `/${year}/${month}/${day}/${title}` 表示，其中 `title` 表示博客的标题， `year` 、 `month` 和 `day` 描述博客发布的时间。

We could represent the variables in the route path with named parameters surrounded by square brackets.  
我们可以用方括号括起来的命名参数来表示路由路径中的变量。

For example, we can create a file in the `pages/blog` directory with the following file name:  
例如，我们可以在 `pages/blog` 目录中创建一个文件，文件名如下：

/\[year\]/\[month\]/\[day\]/\[title\].astro

Since our pages are statically built e.g., when we run the build script, all the routes must be determined at build time.  
由于我们的页面是静态构建的，例如，当我们运行构建脚本时，必须在构建时确定所有的路由。

To achieve this, we must export a `getStaticPaths` function that returns an array of objects that correspond to each route. Here’s how:  
为了实现这一点，我们必须导出一个 `getStaticPaths` 函数，该函数返回对应于每条路由的对象数组。以下是方法：

// 📂 pages/blog/\[year\]/\[month\]/\[day\]/\[title\].astro
\--\-
import BlogLayout from "@layouts/BlogLayout.astro";

export function getStaticPaths() {
    return \[
        {
            params: {
                title: "data-fetching-with-react-server-components",
                year: "2020",
                month: "12",
                day: "21",
            },
        },
    \];
}
\--\-

Note that `getStaticPaths` specifically returns an object with a `params` field that defines all the variables in the route path i.e., `title`, `year`, `month` and `day`  
请注意， `getStaticPaths` 特别返回一个带有 `params` 字段的对象，该字段定义了路由路径中的所有变量，即： `title` 、 `year` 、 `month` 和 `day`

To add another blog route, simply add another object with its `params` property:  
要添加另一个blog路由，只需添加另一个带有 `params` 属性的对象：

// 📂 pages/blog/\[year\]/\[month\]/\[day\]/\[title\].astro
\--\-
export function getStaticPaths() {
    return \[
        {
            params: {
                title: "data-fetching-with-react-server-components",
                year: "2020",
                month: "12",
                day: "21",
            },
        },
        {
            params: {
                title: "introducing-react-dev",
                year: "2023",
                month: "03",
                day: "16",
            },
        },
    \];
}
\--\-

With the route `params` defined, we then grab the variables and render each blog as shown below:  
定义了路由 `params` 后，我们抓取变量并渲染每个博客，如下所示：

// 📂 pages/blog/\[year\]/\[month\]/\[day\]/\[title\].astro
\--\-
import BlogLayout from "@layouts/BlogLayout.astro";

export function getStaticPaths() {
    return \[
        {
            params: {
                title: "data-fetching-with-react-server-components",
                year: "2020",
                month: "12",
                day: "21",
            },
        },
        {
            params: {
                title: "introducing-react-dev",
                year: "2023",
                month: "03",
                day: "16",
            },
        },
    \];
}

// Get the path variables from Astro.params
const { title, year, month, day } \= Astro.params;
\--\-

// Provide markup for each matched page
<BlogLayout title\="React Blog - React" header\="React Blog"\>
    <h1\>{title}</h1\>
    <p\>{year}</p\>
    <p\>{month}</p\>
    <p\>{day}</p\>
</BlogLayout\>

Clicking on the _data fetching with react server components_ and _introducing react dev blog_ cards should now render their accompanying page.  
点击使用react服务器组件的数据获取并引入react dev博客卡片现在应该会呈现它们的附带页面了。

[![Rendered blog markup.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-02%20at%2007.41.17.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-02%20at%2007.41.17.png)

_Rendered blog markup. 渲染的博客标记。_  
  
  

### [](#2-rest-parameters)2\. Rest parameters 2.静止参数

Rest parameters provide ultimate flexibility in our URL routing. For example, we may use `[...path]` to match file paths **of any depth**. Where `path` could be represented by any string, e.g., `[...file]` or `[...somestring]`.  
Rest参数为我们的URL路由提供了极大的灵活性。例如，我们可以使用 `[...path]` 来匹配任何深度的文件路径。其中 `path` 可以由任何字符串表示，例如， `[...file]` 或 `[...somestring]` 。

Following our existing example, how may we reduce the path `pages/blog/[year]/[month]/[day]/[title].astro` to simply `pages/blog/[...path].astro`  
按照我们现有的示例，我们如何将路径 `pages/blog/[year]/[month]/[day]/[title].astro` 简化为 `pages/blog/[...path].astro`

Delete the previous directories and file that made up `[year]/[month]/[day]/[title].astro` and create a single `blog/[...path].astro`.  
删除之前的目录和文件组成 `[year]/[month]/[day]/[title].astro` ，并创建一个 `blog/[...path].astro` 。

This new file will match the blog route.  
此新文件将与博客路由匹配。

Similarly, we need to provide a `getStaticPaths` function, however, the variable to be provided here is `path` as shown below:  
同样，我们需要提供一个 `getStaticPaths` 函数，但是这里要提供的变量是 `path` ，如下所示：

\--\-
import BlogLayout from "@layouts/BlogLayout.astro";

export function getStaticPaths() {
    return \[
        {
            params: {
                path: "2020/12/21/data-fetching-with-react-server-components",
            },
        },
        {
            params: {
                path: "2023/03/16/introducing-react-dev",
            },
        },
    \];
}

const { path } \= Astro.params;
\--\-

<BlogLayout title\="React Blog - React" header\="React Blog"\>
    <h1\>{path}</h1\>
</BlogLayout\>

Clicking on the _data fetching with react server components_ and _introducing react dev blog_ cards should now render their accompanying page.  
点击使用react服务器组件的数据获取并引入react dev博客卡片现在应该会呈现它们的附带页面了。

[![Rendered blog markup.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-02%20at%2007.40.03.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-02%20at%2007.40.03.png)

_Rendered blog markup. 渲染的博客标记。_  
  
  

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

[![Route priority order from first to last.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/route_priority.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/route_priority.png)

_Route priority order from first to last.  
从第一个到最后一个路由优先级顺序。_  
  
  

A decent example is to note that even though the dynamic path `[...path.astro]` matches the root path `/blog`, the static route `blog/index.astro` always takes priority while the dynamic route `[...path.astro]` kicks in for each blog page.  
一个很好的例子是，即使动态路径 `[...path.astro]` 匹配根路径 `/blog` ，静态路径 `blog/index.astro` 总是优先，而动态路径 `[...path.astro]` 则为每个博客页面启动。

[](#generate-routes-with-content-collections)Generate routes with content collections  
使用内容集合生成路由
--------------------------------------------------------------------------------------------------

Right now, we’re manually adding objects to the exported `getStaticPaths` function to define our blog paths.  
现在，我们正在手动添加对象到导出的 `getStaticPaths` 函数，以定义我们的博客路径。

However, our desired solution is to generate these from the blog content collection.  
然而，我们想要的解决方案是从博客内容集合中生成这些内容。

[![Automatically generate routes for each collection entry](/understanding-astro/understanding-astro-book/raw/master/images/ch5/auto_entry_route.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/auto_entry_route.png)

_Automatically generate routes for each collection entry.  
自动为每个收集条目生成路由。_  
  
  

To achieve this, we need to rework the `getStaticPaths` implementation to fetch all blog posts from the content collection and generate the required paths.  
为了实现这一点，我们需要重新修改 `getStaticPaths` 实现，从内容集合中获取所有博客文章，并生成所需的路径。

Consider the solution below:  
考虑下面的解决方案：

\--\-
import { getCollection } from "astro:content";
import BlogLayout from "@layouts/BlogLayout.astro";

// Make the function async
export async function getStaticPaths() {
    // Fetch all blog posts
    const allBlogPosts \= await getCollection("blog");
    // Dynamically construct the blog paths
    const paths \= allBlogPosts.map((blogEntry) \=> ({
        // construct params
        params: {
            path: \`${blogEntry.data.year}/${blogEntry.data.month}/${blogEntry.data.day}/${blogEntry.slug}\`,
        },
    }));

    // Eventually return the constructed paths
    return paths;
}

const { path } \= Astro.params;
\--\-

<BlogLayout title\="React Blog - React" header\="React Blog"\>
    <h1\>{path}</h1\>
</BlogLayout\>

Now, every single blog entry now has an associating path defined. Give this a try by clicking any blog link from the home page.  
现在，每个博客条目都定义了一个关联路径。给予着点击主页上的任何博客链接。

[![All blog paths now automatically handled.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-02%20at%2007.51.47.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-02%20at%2007.51.47.png)

_All blog paths now automatically handled.  
所有的博客路径现在自动处理。_  
  
  

### [](#rendering-each-blog-content)Rendering each blog content  
渲染每个博客内容

Just rendering the path of the blog was great for simplifying the previous concepts, however, that’s not quite our result.  
仅仅渲染博客的路径对于简化前面的概念是很好的，然而，这并不是我们的结果。

Let’s properly render each blog content. First here’s the solution:  
让我们正确渲染每个博客内容。首先是解决方案：

\--\-
import { getCollection } from "astro:content";
import BlogLayout from "@layouts/BlogLayout.astro";

// Make the function async
export async function getStaticPaths() {
    const allBlogPosts \= await getCollection("blog");
    // dynamically construct the blog paths
    const paths \= allBlogPosts.map((blogEntry) \=> ({
        // construct params
        params: {
            path: \`${blogEntry.data.year}/${blogEntry.data.month}/${blogEntry.data.day}/${blogEntry.slug}\`,
        },
        // 👀 Pass blogEntry as props to be later accessed in the markup via Astro.props
        props: {
            blogEntry,
        },
    }));

    //Eventually return the constructed paths
    return paths;
}

// Get the blog entry from the props
const { blogEntry } \= Astro.props;

// get blog content via entry.render()
const { Content } \= await blogEntry.render();
\--\-

<BlogLayout title\="React Blog - React" header\="React Blog"\>
    <!\-- Render the Content \--\>
    <Content /\>
</BlogLayout\>

Let’s deconstruct this solution.  
让我们解构这个解决方案。

The most important piece to the solution puzzle is passing every single blog entry as a `prop` in the `getStaticPath` function.  
解决方案难题最重要的部分是在 `getStaticPath` 函数中将每个博客条目作为 `prop` 传递。

Doing this allows us to reference each entry in the component markup section via `Astro.props`.  
这样做允许我们通过 `Astro.props` 引用组件标记部分中的每个条目。

Secondly, every queried collection entry has a `render()` method that renders the entry to `HTML`. The solution utilises this to render each blog.  
其次，每个查询的集合条目都有一个 `render()` 方法，该方法将条目呈现给 `HTML` 。该解决方案利用它来渲染每个博客。

const { Content } \= await blogEntry.render();
//...
<Content /\>;

[![The rendered blog content.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-02%20at%2008.48.36.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-02%20at%2008.48.36.png)

_The rendered blog content.  
渲染的博客内容。_  
  
  

[](#mdx-components)MDX components MDX组件
---------------------------------------

Let’s get back to MDX.  
让我们回到MDX。

The most impressive feature of MDX is the ability to use components with standard markdown content.  
MDX最令人印象深刻的特性是能够使用具有标准markdown内容的组件。

Let’s consider practical examples.  
让我们考虑实际的例子。

### [](#customised-html-elements)Customised HTML elements  
自定义HTML元素

When MDX content is rendered to HTML, the eventual output uses standard HTML elements.  
当MDX内容呈现为HTML时，最终输出使用标准HTML元素。

For example, if we had the following MDX content:  
例如，如果我们有以下MDX内容：

\# Title

This is a paragraph

This will yield an HTML result similar to the following:  
这将产生类似于以下内容的HTML结果：

<h1\>Title</h1\>
<p\>This is a paragraph</p>

The good news is, instead of relying on standard HTML elements, we can specific components to be used instead of HTML elements. For example, we may provide our own styled header and paragraph components in place of the standard `h1` and `p` HTML elements.  
好消息是，我们可以使用特定的组件来代替HTML元素，而不是依赖于标准的HTML元素。例如，我们可以提供自己的样式化的头和段落组件来代替标准的 `h1` 和 `p` HTML元素。

To do this, create an object of HTML element to custom component mapping.  
为此，创建一个HTML元素对象到自定义组件映射。

// sample MDX component map

// Provide custom header and paragraph
import H1 from "./H1.astro"; // custom Astro component
import P from "./P.astro"; // custom paragraph component

// map of HTML element to custom component
export const mdxComponents \= {
  h1: H1,
  p: P,
};

Now, when the MDX content is rendered to HTML, pass the component map as shown below:  
现在，当MDX内容呈现为HTML时，传递组件映射，如下所示：

\--\-
import {getEntry} from 'astro:content'
// import the component map
import { mdxComponents } from '../mdxComponents'

// Get a collection entry
const blogCollection \= await getEntry('blog', 'some-title')
// Get the entry Content
const { Content } \= await blogEntry.render();
\--\-

{/\*\* Render to HTML and pass the components map\*\*/}
<Content components\={mdxComponents} /\>

Let’s put this into action.  
让我们付诸行动吧。

Take a look at the `src/components/mdxComponents.ts` file in the project. It contains a list of HTML elements and associated custom Astro components.  
看看项目中的 `src/components/mdxComponents.ts` 文件。它包含HTML元素和相关的自定义Astro组件的列表。

We’ll import this object and pass it to the blog entry `<Content />` as shown below:  
我们将导入此对象并将其传递给博客条目 `<Content />` ，如下所示：

// 📂 pages/blog/\[...path\].astro
\--\-
import { mdxComponents } from "@components/mdxComponents";
// ... other imports
\--\-

<BlogLayout title\="React Blog - React" header\="React Blog"\>
    {/\*\* 👀 pass the components down to Content \*\*/}
    <Content components\={mdxComponents} /\>
</BlogLayout\>

With this, we should now have properly styled components in place of the bland HTML elements.  
这样，我们现在应该有适当样式的组件来代替乏味的HTML元素。

[![Leveraging custom components for the MDX HTML output.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-10%20at%2006.39.24.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-10%20at%2006.39.24.png)

_Leveraging custom components for the MDX HTML output.  
利用自定义组件进行MDX HTML输出。_  
  
  

Consider the full list of available HTML elements that can be overwritten with custom components in the official MDX documentation.  
考虑一下官方MDX文档中可用的HTML元素的完整列表，这些元素可以被自定义组件覆盖。

### [](#internal-components)Internal components 内部组件

Components can also be imported and directly rendered within MDX. That’s part of the fun!  
组件也可以导入并直接在MDX中呈现。这就是乐趣的一部分！

Go ahead and open the first blog route in `/blog/2020/12/21/data-fetching-with-react-server-components` and find the first `TODO` on the page.  
继续，打开 `/blog/2020/12/21/data-fetching-with-react-server-components` 中的第一个博客路径，并在页面上找到第一个 `TODO` 。

[![TODO: add the Intro component.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-10%20at%2006.42.47.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-10%20at%2006.42.47.png)

_TODO: add the Intro component.  
TODO：添加Intro组件。_  
  
  

To resolve this TODO, we need to import and render the `Intro` component in `src/components/Intro.astro`.  
为了解决这个TODO，我们需要导入并渲染 `src/components/Intro.astro` 中的 `Intro` 组件。

Consider the solution below:  
考虑下面的解决方案：

// 📂 src/content/blog/data-fetching-with-react-server-components.mdx
\--\-

import Intro from "@components/Intro.astro";

{/\*\* First content after the frontmatter and other imports\*\*/}
<Intro\>
  2020 has been a long year. As it comes to an end we wanted to share a special
  Holiday Update on our research into zero-bundle-size \*\*React Server
  Components\*\*.
</Intro\>
\--\-

[![The rendered Intro component.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-02%20at%2009.07.29.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-02%20at%2009.07.29.png)

_The rendered Intro component.  
渲染的简介组件。_  
  
  

We imported and rendered an Astro component right in the MDX file. How amazing!  
我们在MDX文件中导入并呈现了Astro组件。太神奇了！

Note that the `---` syntax represents dividers (as seen in 1 and 2 above) and not code fences as used to define markdown frontmatter.  
请注意， `---` 语法表示除法器（如上面的1和2所示），而不是用于定义markdown frontmatter的代码围栏。

There’s no limit to how many components we can import and render in an MDX file. So, we can go further and render another component as shown below:  
在MDX文件中导入和呈现的组件数量没有限制。因此，我们可以进一步渲染另一个组件，如下所示：

{
  /\*\* Import the Note component \*\*/
}
import Note from "@components/Note.astro";

{
  /\*\* Render at the bottom of the file \*\*/
}
<Note\>React Server Components are still in research and development.</Note\>;

[![The rendered Note component.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-02%20at%2010.43.07.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-02%20at%2010.43.07.png)

_The rendered Note component.  
渲染的Note组件。_  
  
  

Note that, unlike JavaScript imports that must be at the top of the file, we can import components in an MDX file anywhere aside from the frontmatter section.  
注意，与JavaScript导入必须位于文件顶部不同，我们可以在MDX文件中导入组件，而不是frontmatter部分。

I typically prefer to keep the imports at the top of the document, right after the frontmatter, but you may also colocate the imports close to where they are rendered. Both options work!  
我通常更喜欢将导入放在文档的顶部，就在frontmatter后面，但是您也可以将导入放在它们呈现的位置附近。两种选择都有效！

### [](#external-imports)External imports 外部进口

We’ve seen different imported components in our MDX documents. Luckily, it gets even more fun.  
我们在MDX文档中看到了不同的导入组件。幸运的是，它变得更加有趣。

We can also import and render external components e.g., from NPM in MDX.  
我们还可以导入和渲染外部组件，例如，从MDX中的NPM。

Go ahead and install `astro-embed`  
继续安装 `astro-embed`

    npm install astro-embed
    

`astro-embed` lets us embed components such as Tweets and Youtube videos in an Astro project.  
`astro-embed` 让我们在Astro项目中嵌入诸如Tweets和Youtube视频之类的组件。

In the same blog in `/blog/2020/12/21/data-fetching-with-react-server-components` consider the next TODO:  
在 `/blog/2020/12/21/data-fetching-with-react-server-components` 的同一个博客中，考虑下一个TODO：

\## Reference

To introduce React Server Components, we have prepared a talk
and a demo. If you want, you can check them out during the.
holidays, or later when work picks back up in the new year.

❗️TODO: Add Youtube video embed here

To resolve this, go ahead and import the `Youtube` component from `astro-embed` and render the component with an `id` prop as shown below:  
要解决这个问题，请继续从 `astro-embed` 导入 `Youtube` 组件，并使用 `id` 道具渲染该组件，如下所示：

\## Reference

To introduce React Server Components, we have prepared a talk and a demo. If you want, you can check them out during the holidays, or later when work picks back up in the new year.

import { YouTube } from "astro-embed";

<YouTube id\="https://youtu.be/TQQPAU21ZUw" />

[![The rendered Youtube component.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-10%20at%2007.05.09.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-10%20at%2007.05.09.png)

_The rendered Youtube component.  
渲染的Youtube组件。_  
  
  

Note that we’re colocating the import statement close to the component render. However, we may move the import higher up the file as well.  
注意，我们将import语句放在组件呈现附近。但是，我们也可以将导入移到文件的更高位置。

{/\*\* ✅ This is correct \*\*/}

import { YouTube } from "astro-embed";

<YouTube id\="https://youtu.be/TQQPAU21ZUw" />

{/\*\* ✅ This is equally correct \*\*/}

{/\*\* Keep all imports on top, right after the frontmatter \*\*/}

import Intro from "@components/Intro.astro";
import { YouTube } from "astro-embed";

{/\*\* Render other content ... and component much later \*\*/}

<YouTube id\="https://youtu.be/TQQPAU21ZUw" />

### [](#autoimport)AutoImport 自动导入

The `Youtube`, `Intro` and `Note` components are used across all the blogs. Right now, importing the components every single time seems repetitive.  
`Youtube` 、 `Intro` 和 `Note` 组件用于所有博客。现在，每次导入组件似乎都是重复的。

With components we want to be reused across our entire MDX files, how about we automatically import these i.e. without manually duplicating the import in every MDX document?  
对于我们希望在整个MDX文件中重用的组件，我们自动导入这些组件（即而无需在每个MDX文档中手动复制导入？

To achieve this, we will leverage the `astro-auto-import` package.  
为了实现这一点，我们将利用 `astro-auto-import` 包。

With `astro-auto-import`, we can easily import components or modules automatically and utilize them in MDX files without the need for manual importing.  
使用 `astro-auto-import` ，我们可以轻松地自动导入组件或模块，并在MDX文件中使用它们，而无需手动导入。

First, install `astro-auto-import`: 首先，安装 `astro-auto-import` ：

npm install astro-auto-import

`astro-auto-import` works as an Astro integration. To use it, we must update the project `astro.config.mjs` file as shown below:  
`astro-auto-import` 作为Astro集成。要使用它，我们必须更新项目 `astro.config.mjs` 文件，如下所示：

// other imports ...
// import AutoImport
import AutoImport from "astro-auto-import";

export default defineConfig({
  integrations: \[
    // Pass AutoImport in the integrations array
    AutoImport({
      imports: \[
        /\*\*
         \* Generates:
         \* import Intro from './src/components/Intro.astro';
         \*/
        "./src/components/Intro.astro",
        "./src/components/Note.astro",
        /\*\*
         \* Generates:
         \* import { YouTube } from 'astro-embed';
         \*/
        { "astro-embed": \["YouTube"\] },
      \],
    }),
    react(),
    tailwind(),
    mdx(),
  \],
});

To use `AutoImport` we pass it into the `integrations` array and invoke `AutoImport` with an imports list:  
为了使用 `AutoImport` ，我们将其传递到 `integrations` 数组中，并使用导入列表调用 `AutoImport` ：

AutoImport({
  imports: \[
    "./src/components/Intro.astro",
    "./src/components/Note.astro",
    { "astro-embed": \["YouTube"\] },
  \],
});

The `imports` represents a list of imports to be automatically added to our MDX files.  
`imports` 表示要自动添加到MDX文件中的导入列表。

A string with the path of the import such as `"./src/components/Intro.astro"` will generate a default import such as `import Intro from './src/components/Intro.astro'`.  
带有导入路径的字符串（如 `"./src/components/Intro.astro"` ）将生成默认导入（如 `import Intro from './src/components/Intro.astro'` ）。

An object such as `{ "astro-embed": ["YouTube"] }` generates a named import such as `import { Tweet, YouTube } from 'astro-embed'`.  
一个对象（如 `{ "astro-embed": ["YouTube"] }` ）生成一个命名导入（如 `import { Tweet, YouTube } from 'astro-embed'` ）。

With these in place, we must now remove the manual imports in the MDX files and rely on the `AutoImport` magic ✨  
有了这些，我们现在必须删除MDX文件中的手动导入，并依靠 `AutoImport` 神奇的

Neat! 好极了！

[](#integration-spotlight-astro-seo)Integration spotlight: Astro SEO  
集成聚光灯：Astro SEO
--------------------------------------------------------------------------------------

You’ve seen a lot of Astro integrations already! Think `@astrojs/react` for having React islands in an Astro project, or the official `@astrojs/tailwind` integration for using tailwind in Astro.  
你已经看到了很多Astro集成了！想想 `@astrojs/react` 在Astro项目中使用React islands，或者在Astro中使用顺风的官方 `@astrojs/tailwind` 集成。

Generally speaking, integrations add new functionality and behaviour to an Astro project, usually with just a few lines of code.  
一般来说，集成会为Astro项目添加新的功能和行为，通常只需要几行代码。

Sounds like a win!  
听起来像是赢了！

In this section, let’s discuss `astro-seo`, an integration that makes it straightforward to add SEO-relevant information to any Astro app.  
在本节中，让我们讨论 `astro-seo` ，这是一个集成，可以直接将SEO相关信息添加到任何Astro应用程序。

You know the rodeo.  
你知道牛仔牛仔竞技表演。

First, install the integration:  
首先，安装集成：

npm install astro\-seo

To use `astro-seo`, we import the `SEO` component and pass it relevant props as seen below:  
要使用 `astro-seo` ，我们导入 `SEO` 组件并传递相关的props，如下所示：

// 📂 src/layouts/BaseLayout.astro
\--\-
import { SEO } from "astro-seo";
// ...
\--\-
<html lang\="en"\>
  <head\>
    <meta charset\="utf-8" /\>
    <link rel\="icon" type\="image/svg+xml" href\="/favicon.svg" /\>
    <meta name\="viewport" content\="width=device-width" /\>
    <meta name\="generator" content\={Astro.generator} /\>

    <SEO
      title\={title}
      description\={description}
      openGraph\={{
        basic: {
          title,
          type: "website",
          image: "https://react.dev/images/og-home.png",
        },
      }}
      twitter\={{
        creator: "@reactjs",
      }}
      extend\={{
        meta: \[
          {
            name: "twitter:image",
            content: "https://react.dev/images/og-home.png",
          },
          { name: "twitter:title", content: "@reactjs" },
          {
            name: "twitter:description",
            content: description,
          },
        \],
      }}
    /\>
  {/\*\* ... \*\*/}
</head\>
{/\*\* ... \*\*/}
</html\>

This will generate relevant meta tags including open-graph meta tags for a more SEO-compliant application.  
这将生成相关的Meta标签，包括开放图元标签，用于更符合SEO的应用程序。

[](#custom-404-pages-in-astro)Custom 404 pages in Astro  
Astro中的自定义404页面
-------------------------------------------------------------------------

Custom 404 pages are easy to reason about in Astro. Create a `404.astro` or any other relevant page file ending in `src/pages`. This will build a `404.html` page that most deployment services will use if an invalid page is requested and not found.  
自定义404页面在Astro很容易推理。创建 `404.astro` 或任何其他以 `src/pages` 结尾的相关页面文件。这将生成一个 `404.html` 页面，如果请求无效页面但未找到，大多数部署服务将使用该页面。

Let’s do this for our project.  
让我们为我们的项目做这个。

Create a `404.astro` page in `src/pages` with the following content:  
在 `src/pages` 中创建一个包含以下内容的 `404.astro` 页面：

// 📂 src/pages/404.astro
\--\-
import BaseLayout from "@layouts/BaseLayout.astro";
\--\-

<BaseLayout title\="Redirecting ..." page\="index" /\>

<script is:inline\>
// lazy redirect. This is better done server-side: discussed in the next book's chapter
const { pathname } \= window.location;

window.location.replace(\`https://www.react.dev${pathname}\`);
</script\>

Our `404` page comes with a twist.  
我们的 `404` 页面有一个转折。

It renders a blank page via `<BaseLayout />` and automatically redirects the user to the accompanying path on `www.react.dev`. Viola!  
它通过 `<BaseLayout />` 呈现一个空白页面，并自动将用户重定向到 `www.react.dev` 上的相应路径。维奥拉

Give this a try by visiting the API reference link on the homepage.  
通过访问主页上的API参考链接来给予一下。

[![The API reference link.](/understanding-astro/understanding-astro-book/raw/master/images/ch5/CleanShot%202023-07-10%20at%2007.28.40.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch5/CleanShot%202023-07-10%20at%2007.28.40.png)

_The API reference link.  
API参考链接。_  
  
  

[](#conclusion)Conclusion 结论
----------------------------

Building rich content applications is right up Astro’s alley! With content collections, we can build large content-driven applications with organisation and confidence.  
构建丰富的内容应用程序是正确的Astro的小巷！有了内容集合，我们可以构建大型内容驱动的应用程序，有组织性和信心。

Footnotes 页签
------------

1.  For Markdown files, it’s possible to use a number of plugins such as [https://rehype-pretty-code.netlify.app/](https://rehype-pretty-code.netlify.app/) [↩](#user-content-fnref-1-7480127aa737d860f674069ffe7b7221)  
    对于Markdown文件，https://rehype-pretty-code.netlify.app/
    
