

Breadcrumbs
-----------

1.  [understanding-astro-book](/understanding-astro/understanding-astro-book/tree/master)

/

ch4.md
======

 master

Breadcrumbs
-----------

1.  [understanding-astro-book](/understanding-astro/understanding-astro-book/tree/master)

/

ch4.md
======

t

Blame

Latest commit
-------------

[![ohansemmanuel](https://avatars.githubusercontent.com/u/10930234?s=40&v=4)](/ohansemmanuel)[ohansemmanuel](/understanding-astro/understanding-astro-book/commits?author=ohansemmanuel)

[🐛 fix: resolves syntax autosave error](/understanding-astro/understanding-astro-book/commit/5f7580ec8ca3c5b06f42ce06bc256bee434a9ba6 "🐛 fix: resolves syntax autosave error")

[5f7580e](/understanding-astro/understanding-astro-book/commit/5f7580ec8ca3c5b06f42ce06bc256bee434a9ba6) · 

History
-------

[History](/understanding-astro/understanding-astro-book/commits/master/ch4.md)

[](/understanding-astro/understanding-astro-book/commits/master/ch4.md)

1048 lines (752 loc) · 36.5 KB

 master

Breadcrumbs
-----------

1.  [understanding-astro-book](/understanding-astro/understanding-astro-book/tree/master)

/

ch4.md
======

Top

File metadata and controls
--------------------------

*   Preview
    
*   Code
    
*   Blame
    

1048 lines (752 loc) · 36.5 KB

[Raw](/understanding-astro/understanding-astro-book/raw/master/ch4.md)

[](https://github.dev/)[](https://github.dev/)

[](/understanding-astro/understanding-astro-book/edit/master/ch4.md)

[](#-understanding-astro)🚀 Understanding Astro  
🚀 了解Astro
============================================================

By [Ohans Emmanuel](https://www.ohansemmanuel.com/) 作者：Ohans Emmanuel

  
  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch3/watch-instead@3x.png)](https://ohans.me/understanding-astro-udemy)

  
  

[![](/understanding-astro/understanding-astro-book/raw/master/images/ch3/view-project.png)](https://github.com/understanding-astro/astro-islands-showcase)

  
  

[](#chapter-4-the-secret-life-of-astro-component-islands)Chapter 4: The Secret Life of Astro Component Islands  
第四章：天体组件岛的秘密生活
-------------------------------------------------------------------------------------------------------------------------------

Component islands are the secret to Astro’s super-fast narrative. It’s time to learn everything about them.  
组件岛屿是Astro超快速叙事的秘密。是时候了解他们的一切了。

[](#what-youll-learn)What you’ll learn 您将学到的内容
----------------------------------------------

*   Hands-on experience working with framework components in Astro.  
    在Astro中使用框架组件的实践经验。
*   Responsible hydration and why it matters.  
    负责任的水合作用及其重要性
*   How component islands work in Astro.  
    组件岛如何在Astro中工作。
*   Why islands are essential.  
    为什么岛屿必不可少

[](#how-islands-work-in-astro)How islands work in Astro  
岛屿在Astro中如何工作
-----------------------------------------------------------------------

Assume we’ve got an Astro application with static content: a navigation bar, some main content, a footer and a side pane.  
假设我们有一个包含静态内容的Astro应用程序：导航栏、一些主要内容、页脚和侧窗格。

[![A static astro page structure.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/a.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/a.png)

_A static astro page structure.  
静态天文页面结构。_  
  
  

If we need to introduce some interactivity content in the side pane of the application, how could we achieve this?  
如果我们需要在应用程序的侧面板中引入一些交互内容，我们如何实现这一点？

[![Adding interactive content to the static page.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/b.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/b.png)

_Adding interactive content to the static page.  
向静态页面添加交互式内容。_  
  
  

Astro provides the following ways to do this:  
Astro提供了以下方法来做到这一点：

*   We've seen how this works: introduce a `<script>` element to handle interactivity within your Astro component.  
    我们已经看到了它是如何工作的：引入一个 `<script>` 元素来处理Astro组件中的交互性。
*   Use a supported framework component, and leverage a component island.  
    使用受支持的框架组件，并利用组件岛。

The second option is the focus of this chapter.  
第二个选项是本章的重点。

At the time of writing, Astro lets you use components built with `React`, `Preact`, `Svelte`, `Vue`, `SolidJS`, `AlpineJS` or `Lit` in your Astro components. Moving on, I’ll refer to these as **framework components**.  
在撰写本文时，Astro允许您在Astro组件中使用使用 `React` 、 `Preact` 、 `Svelte` 、 `Vue` 、 `SolidJS` 、 `AlpineJS` 或 `Lit` 构建的组件。接下来，我将把这些称为框架组件。

[![Leveraging framework components in Astro.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/framework-components.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/framework-components.png)

_Leveraging framework components in Astro.  
利用Astro中的框架组件。_  
  
  

So, why would we use framework components and not just provide native support via a `<script>` element?  
那么，为什么我们要使用框架组件，而不仅仅是通过 `<script>` 元素提供原生支持呢？

It would be best to stick with a `<script>` element in cases where you can get by with vanilla Javascript or Typescript. However, there are cases where we may favour a framework component. For example:  
如果你可以使用vanilla JavaScript或Typescript，最好坚持使用 `<script>` 元素。然而，在某些情况下，我们可能会倾向于框架组件。举例来说：

\-**Design systems**: using a pre-existing design system in an Astro project can save time, depending on the use case. It also helps keep all your applications looking and feeling the same way.  
\- 设计系统：在Astro项目中使用预先存在的设计系统可以保存时间，具体取决于用例。它还有助于保持所有应用程序的外观和感觉相同。

\-**Open-source**: we might consider utilising a feature-rich open-source framework component already existing instead of building some highly interactive component from scratch. This way, we can easily use an open-source framework component in Astro.  
\- 开源：我们可以考虑利用已经存在的功能丰富的开源框架组件，而不是从头开始构建一些高度交互的组件。这样，我们就可以轻松地在Astro中使用开源框架组件。

\-**Ease of development**: we may find building richer stateful user interfaces easier, more manageable, and faster to implement via framework components than vanilla Javascript / Typescript provided in `<script>`.  
\- 易于开发：我们可能会发现，通过框架组件构建更丰富的有状态用户界面比 `<script>` 中提供的普通JavaScript / Typescript更容易、更易于管理、更快。

  

To use a framework component in Astro, we leverage component islands.  
为了在Astro中使用框架组件，我们利用组件岛。

Let’s return to our example application.  
让我们回到我们的示例应用程序。

Assuming we’ve weighed the pros and cons and decided to introduce a framework component, the following section highlights the steps to take.  
假设我们已经权衡了利弊并决定引入框架组件，那么下一节将重点介绍要采取的步骤。

### [](#step-1-build-an-astro-site)Step 1: Build an Astro site  
步骤1：建立Astro站点

We can’t use framework components without having some Astro site to use them in.  
我们不能使用框架组件没有一些天文网站使用它们。

We’ve already seen how to build static sites with Astro, so creating a new static project is unnecessary. Instead, let’s start a new Astro with a project I’ve prepared.  
我们已经看到了如何使用Astro构建静态站点，因此创建一个新的静态项目是不必要的。相反，让我们开始一个新的Astro与一个我已经准备好的项目。

Clone the project: 克隆项目：

git clone https://github.com/understanding-astro/astro-islands-visual-example.git

Then, install dependencies and start the application via the following:  
然后，安装依赖项并通过以下方式启动应用程序：

npm install
npm run start

This will run the project in one of your local ports.  
这将在您的一个本地端口中运行项目。

[![The astro islands visual example project.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-11%20at%2014.06.52@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-11%20at%2014.06.52@2x.png)

_The astro islands visual example project.  
阿斯特罗群岛视觉范例项目。_  
  
  

The project takes the same form as our hypothetical example — it’s got a navigation, main content, footer and side pane.  
该项目采用与我们假设的示例相同的形式-它有一个导航，主内容，页脚和侧面板。

[![A static astro page structure.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/a-1.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/a-1.png)

_A static astro page structure.  
静态天文页面结构。_  
  
  

Within the side pane, there’s a `slot` to render our interactive content via a framework component.  
在侧窗格中，有一个 `slot` 通过框架组件呈现我们的交互式内容。

In `src/pages/index.astro`, you’ll find the code responsible for rendering the page as shown below:  
在 `src/pages/index.astro` 中，您会发现负责渲染页面的代码如下所示：

// 📂 src/pages/index.astro
\--\-
import DefaultIslandLayout from "../layouts/DefaultIslandLayout.astro";
\--\-

<DefaultIslandLayout /\>

`DefaultIslandLayout` provides the layout for the entire page and includes a `slot` for rendering whatever children elements are passed to it. Initialise the project locally and take a look!  
`DefaultIslandLayout` 提供整个页面的布局，并包括一个 `slot` ，用于呈现传递给它的任何子元素。在本地初始化项目并查看！

### [](#step-2-install-the-framework-integration)Step 2: Install the framework integration  
步骤2：安装框架集成

Astro provides official integrations for the supported framework components. In this example, we’ll use the `react` framework.  
Astro为支持的框架组件提供官方集成。在这个例子中，我们将使用 `react` 框架。

It’s important to note that the steps described here are the same regardless of the framework component of your choosing. Therefore, I’m sticking to `react` as many more developers arguably use it.  
需要注意的是，无论您选择的框架组件是什么，这里描述的步骤都是相同的。因此，我坚持使用 `react` ，因为有更多的开发人员可以使用它。

The most convenient way to add your framework integration is to use the `astro add` command, e.g., to add `react`, run the following commands:  
添加框架集成的最方便的方法是使用 `astro add` 命令，例如：要添加 `react` ，请运行以下命令：

# using NPM
npx astro add react
# Using Yarn
yarn astro add react
# Using PNPM
pnpm astro add react

This will automatically add the relevant framework dependencies to our project.  
这将自动向我们的项目添加相关的框架依赖项。

[![Running astro add react.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-11%20at%2014.56.20@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-11%20at%2014.56.20@2x.png)

_Running astro add react.  
运行astro add react。_  
  
  

The command will also automatically update our project configuration, `astro.config.mjs`, to include the framework integration.  
该命令还将自动更新我们的项目配置 `astro.config.mjs` ，以包含框架集成。

[![Updating the project config file.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-11%20at%2014.57.00@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-11%20at%2014.57.00@2x.png)

_Updating the project config file.  
正在更新项目配置文件。_  
  
  

Essentially, this breaks down the installation of a framework into our Astro project into two distinct processes:  
本质上，这将框架安装到我们的Astro项目中分解为两个不同的过程：

1.  Install the framework dependencies.  
    安装框架依赖项。
2.  Add the relevant framework integration in the project config file.  
    在项目配置文件中添加相关的框架集成。

If we didn’t use the `Astro add` command, we could achieve the same results manually by installing the framework dependencies and adding the framework integration in our project configuration file.  
如果我们不使用 `Astro add` 命令，我们可以通过安装框架依赖项并在项目配置文件中添加框架集成来手动实现相同的结果。

### [](#step-3-write-the-component-framework)Step 3: Write the component framework  
步骤3：编写组件框架

Our framework component will be a glorified counter. Assuming the page consists of an article a reader can upvote, we’ll build an upvote button.  
我们的框架组件将是一个美化的计数器。假设页面包含一篇读者可以支持的文章，我们将构建一个支持按钮。

[![The upvote counter illustrated.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/upvote-counter.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/upvote-counter.png)

_The upvote counter illustrated.  
上投票计数器图示。_  
  
  

Here’s the annotated `UpvoteContent` React component:  
下面是带注释的 `UpvoteContent` React组件：

<!\-- 📂 src/components/UpvoteContent.tsx \--\>

import { useState } from "react";

// The maximum number of upvotes available
const MAX\_COUNT \= 50;

export const UpvoteContent \= () \=> {
  // the initial state of the upvote counter
  const \[upvoteCount, setUpvoteCount\] \= useState(0);

  return (
    <div\>
      <button
       // update state when a user clicks the counter. check if
       //The maximum count value was reached first.
        onClick\={() \=> {
          setUpvoteCount((prevCount) \=>
            prevCount < MAX\_COUNT ? prevCount + 1 : prevCount
          );
        }}
      \>
       { /\*\* Upvote counter SVG icon. shortened for brevity \*\*/}
        <svg /\>
        Upvote
      </button\>

      <div\>
        <div\>{\`${upvoteCount} upvotes\`}</div\>

		{/\*\* show a growing visual bar based on the upvote count \*\*/}
        <div
          style\={{
            width: \`${upvoteCount}%\`,
          }}
        /\>

		{/\*\* show a warning if the maximum count has been reached\*\*/}
        {upvoteCount \=== MAX\_COUNT && (
          <div\>
            Max upvote reached
          </div\>
        )}
      </div\>
    </div\>
  );
};

Don’t worry if you don’t understand `react`. The goal here is to know how to work with framework components in Astro. We could build the same component using any other framework we choose, e.g., Vue or Svelte.  
如果你不懂，不要担心 `react` 。这里的目标是了解如何在Astro中使用框架组件。我们可以使用我们选择的任何其他框架构建相同的组件，例如，Vue或Svelte

### [](#step-4-render-the-component-framework)Step 4: Render the component framework  
步骤4：渲染组件框架

Let’s go ahead and render the framework component as shown below:  
让我们继续渲染框架组件，如下所示：

<!\-- 📂 src/pages/none.astro \--\>
\--\-
import { UpvoteContent } from "../components/UpvoteContent.jsx";
import DefaultIslandLayout from "../layouts/DefaultIslandLayout.astro";
\--\-

<DefaultIslandLayout\>
  <UpvoteContent /\>
</DefaultIslandLayout\>

*   Create a new page in `src/pages/none.astro`  
    在 `src/pages/none.astro` 中创建新页面
    
*   Render the `UpvoteContent` component as a child of `DefaultIslandLayout`, i.e.:  
    将 `UpvoteContent` 组件渲染为 `DefaultIslandLayout` 的子组件，即：
    
    <DefaultIslandLayout\>
      <UpvoteContent /\>
    </DefaultIslandLayout\>
    
*   `DefaultIslandLayout` takes the `UpvoteContent` child component and renders it within its layout slot.  
    `DefaultIslandLayout` 获取 `UpvoteContent` 子组件，并在布局槽中渲染它。
    

Now, open the `/none` page in the browser, and we should have the rendered `UpvoteContent` component rendered.  
现在，在浏览器中打开 `/none` 页面，我们应该已经呈现了渲染的 `UpvoteContent` 组件。

[![Rendering the framework component.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-13%20at%2012.59.52@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-13%20at%2012.59.52@2x.png)

_Rendering the framework component.  
呈现框架组件。_  
  
  

The upvote counter is successfully rendered, but clicking the button doesn’t increase the count!  
向上投票计数器已成功呈现，但单击按钮不会增加计数！

What’s going on? 🥹  
你在干什么？🥹

#### [](#its-not-a-bug-its-a-feature)It’s not a bug. It’s a feature.  
不是虫子。这是一个特色。

By default, when you render a framework component, Astro automatically renders it to HTML ahead of time, i.e., Astro strips out all of the component JavaScript.  
默认情况下，当你渲染一个框架组件时，Astro会自动提前将其渲染为HTML，即，Astro剥离了所有JavaScript组件。

Essentially, you get no interactivity from framework components by default.  
本质上，默认情况下，您不会从框架组件中获得交互性。

[![#NoJavscriptByDefault](/understanding-astro/understanding-astro-book/raw/master/images/ch4/no-js-by-default.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/no-js-by-default.png)

_If Astro launched a Twitter campaign, #NoJavscriptByDefault would make an excellent hashtag.  
如果Astro发起了Twitter活动，#NoJavscriptByDefault将成为一个很好的标签。_  
  
  

As it stands, what we currently have is technically not an island. We have the component markup rendered with no interactivity.  
从技术上讲，我们现在所拥有的并不是一个岛屿。我们呈现的组件标记没有交互性。

[](#responsible-hydration)Responsible hydration 负责任的水合作用
--------------------------------------------------------

Astro helps you minimise Javascript bloat when using framework components by leveraging responsible hydration.  
Astro通过利用负责任的水合作用，帮助您在使用框架组件时最小化JavaScript膨胀。

If Astro renders your framework component to `100%` HTML, how do you hydrate (make interactive) the framework component?  
如果Astro将你的框架组件渲染为 `100%` HTML，你如何使框架组件水合（使之交互）？

In the context of Astro development, responsible hydration refers to Astro making no decision on when to hydrate your framework component and leaving that decision entirely up to the developer.  
在Astro开发的背景下，负责任的水合指的是Astro不决定何时水合你的框架组件，并将决定完全留给开发人员。

This is powerful but comes with the burden of decision resting on us — developers.  
这是强大的，但伴随着决策的负担落在我们开发人员身上。

When technical decisions such as this need to be made, they must be made against specific requirements. In this case, the decision lies in evaluating two criteria, namely **priority** and **interactivity**.  
当需要做出诸如此类的技术决策时，它们必须针对特定的要求做出。在这种情况下，决定在于评估两个标准，即优先级和交互性。

*   Priority: is this a high or low-priority user interface element?  
    优先级：这是一个高优先级还是低优先级的用户界面元素？
*   Interactivity: should this element be interactive as soon as possible?  
    互动性：这一要素是否应尽快具有互动性？

We may represent this on a 2d plane as follows:  
我们可以在2D平面上表示这一点如下：

[![Representing priority and interactivity on a 2d plane.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/hydration-plane.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/hydration-plane.png)

_Representing priority and interactivity on a 2d plane.  
在二维平面上表示优先级和交互性。_  
  
  

There are four attributes you can pass to your rendered framework component, e.g.,  
有四个属性可以传递给呈现的框架组件，例如

<ReactComponent attribute /\>

These attributes are called client directives (or, more generically, template directives). Here are the five client directives that control the hydration of your framework component:  
这些属性称为客户端指令（或者更一般地称为模板指令）。下面是控制框架组件水合的五个客户端指令：

*   `client:load`
*   `client:only`
*   `client:visible`
*   `client:media`
*   `client:idle`

[![Representing the client template directives on a priority - interactivity plane.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/responsible-hydration-astro-plane.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/responsible-hydration-astro-plane.png)

_Representing the client template directives on a priority - interactivity plane.  
在优先级交互平面上表示客户端模板指令。_  
  
  

### [](#clientload)client:load 客户端：加载

`client:load` should be used for high-priority interface elements that must be interactive as soon as possible.  
`client:load` 应该用于必须尽快交互的高优先级界面元素。

*   Priority: high 优先级：高
*   Interactivity: high

We may go ahead and render our `UpvoteContent` component as shown below:  
我们可以继续渲染我们的 `UpvoteContent` 组件，如下所示：

// 📂 src/pages/index.astro
\--\-
import { UpvoteContent } from "../components/UpvoteContent.jsx";
import DefaultIslandLayout from "../layouts/DefaultIslandLayout.astro";
\--\-

<DefaultIslandLayout\>
  <UpvoteContent client:load /\>
</DefaultIslandLayout\>

Here are the hydration steps:  
以下是补水步骤：

1.  Render the component HTML (not hydrated).  
    渲染组件HTML（未水合）。
2.  Wait for the page to load.  
    等待页面加载。
3.  Load component Javascript.  
    加载组件JavaScript。
4.  Hydrate component. 水合物组分。

The load event is fired when the page has loaded, including all dependent resources such as stylesheets, scripts, iframes, and images.  
加载页面时触发load事件，包括所有依赖资源，如样式表、脚本、iframe和图像。

It’s important to note that clicking the upvote button will not trigger any upvotes before hydration.  
需要注意的是，点击向上投票按钮不会在水合之前触发任何向上投票。

### [](#clientonly)client:only 客户端：仅

`client:only` behaves similarly to `client:load`. It should be used for elements where you want to skip server-side rendering (the component will not be initially rendered to HTML) but make it interactive as soon as it’s shown to the user on the client.  
`client:only` 的行为类似于 `client:load` 。它应该用于您希望跳过服务器端呈现的元素（组件最初不会呈现为HTML），但一旦在客户端显示给用户，就立即使其具有交互性。

*   Priority: medium (we’re okay not showing the initial component HTML)  
    优先级：中等（我们可以不显示初始组件HTML）
*   Interactivity: high (as soon as it’s shown to the user)  
    互动性：高（一旦显示给用户）

We may go ahead and render our `UpvoteContent` component as shown below:  
我们可以继续渲染我们的 `UpvoteContent` 组件，如下所示：

// 📂 src/pages/index.astro
\--\-
import { UpvoteContent } from "../components/UpvoteContent.jsx";
import DefaultIslandLayout from "../layouts/DefaultIslandLayout.astro";
\--\-

<DefaultIslandLayout\>
  <UpvoteContent client:only\="react" /\>
</DefaultIslandLayout\>

It’s essential to pass the framework name as shown above. Otherwise, Astro doesn’t know what framework Javascript to load. This is because this isn’t determined on the server.  
传递框架名称是必要的，如上所示。否则，Astro不知道加载什么框架JavaScript。这是因为这不是在服务器上确定的。

<ReactComponent client:only\="react" /\>
<PreactComponent client:only\="preact" /\>
<SvelteComponent client:only\="svelte" /\>
<VueComponent client:only\="vue" /\>
<SolidComponent client:only\="solid-js" /\>

Here are the hydration steps:  
以下是补水步骤：

1.  Do not render component HTML.  
    不呈现组件HTML。
2.  Wait for the page to load.  
    等待页面加载。
3.  Load component Javascript.  
    加载组件JavaScript。
4.  Hydrate component. 水合物组分。

The difference between `client:only` and `client:load` is whether to render a static component HTML before the element is interactive. `client:only` is particularly handy when rendering components requiring client (browser) APIs.  
`client:only` 和 `client:load` 之间的区别在于是否在元素交互之前呈现静态组件HTML。 `client:only` 在渲染需要客户端（浏览器）API的组件时特别方便。

### [](#clientvisible)client:visible 客户端：可见

`client:visible` should be used for low-priority interface elements below the fold (far down the page) or resource-intensive; you don’t want to load them if the user never sees the component.  
`client:visible` 应该用于文件夹下方（页面下方）或资源密集型的低优先级界面元素;如果用户从未看到组件，则不希望加载它们。

*   Priority: low 优先级：低
*   Interactivity: low 互动性：低

We may go ahead and render our `UpvoteContent` component as shown below:  
我们可以继续渲染我们的 `UpvoteContent` 组件，如下所示：

// 📂 src/pages/index.astro
\--\-
import LargeMainContentLayout from "../layouts/LargeMainContentLayout.astro";
import { UpvoteContent } from "../components/UpvoteContent.jsx";
\--\-

<LargeMainContentLayout\>
  <UpvoteContent client:visible /\>
</LargeMainContentLayout\>

Note that I’m importing a different `LargeMainContentLayout` layout in the code block above. The layout is responsible for pushing the island off the initial viewport.  
注意，我在上面的代码块中导入了一个不同的 `LargeMainContentLayout` 布局。布局负责将岛推出初始视口。

Here are the hydration steps:  
以下是补水步骤：

1.  Render component HTML. 渲染组件HTML。
2.  Wait for the element to be visible (uses `IntersectionObserver` ).  
    等待元素可见（使用 `IntersectionObserver` ）。
3.  Load component Javascript.  
    加载组件JavaScript。
4.  Hydrate component. 水合物组分。

### [](#clientmedia)client:media 客户端：媒体

`client:media` should be used for low-priority interface elements only visible on specific screen sizes, e.g., sidebar toggles.  
`client:media` 应用于仅在特定屏幕尺寸上可见的低优先级界面元素，例如，侧栏切换。

*   Priority: low 优先级：低
*   Interactivity: low 互动性：低

We may go ahead and render our `UpvoteContent` component as shown below:  
我们可以继续渲染我们的 `UpvoteContent` 组件，如下所示：

// 📂 src/pages/index.astro
\--\-
import { UpvoteContent } from "../components/UpvoteContent.jsx";
import DefaultIslandLayout from "../layouts/DefaultIslandLayout.astro";
\--\-

<DefaultIslandLayout\>
  <UpvoteContent client:media\="(max-width: 30em)" /\>
</DefaultIslandLayout\>

Here are the hydration steps:  
以下是补水步骤：

1.  Render component HTML 渲染组件HTML
2.  Check if the media query matches  
    检查媒体查询是否匹配
3.  Load component Javascript  
    加载组件JavaScript
4.  Hydrate component 水合物组分

### [](#clientidle)client:idle 客户端：空闲

`client:idle` should be used for low-priority interface elements that don’t need to be immediately interactive.  
`client:idle` 应该用于不需要立即交互的低优先级界面元素。

*   Priority: medium 优先级：中等
*   Interactivity: medium (lower priority in comparison to `client:load`)  
    互动性：中等（优先级低于 `client:load` ）

We may go ahead and render our `UpvoteContent` component as shown below:  
我们可以继续渲染我们的 `UpvoteContent` 组件，如下所示：

// 📂 src/pages/index.astro
\--\-
import { UpvoteContent } from "../components/UpvoteContent.jsx";
import DefaultIslandLayout from "../layouts/DefaultIslandLayout.astro";
\--\-

<DefaultIslandLayout\>
  <UpvoteContent client:idle /\>
</DefaultIslandLayout\>

Here’s the hydration step visualised:  
以下是可视化的水合步骤：

1.  Render component HTML. 渲染组件HTML。
2.  Wait for the page to load.  
    等待页面加载。
3.  Wait for the `requestIdleCallback` event to be fired  
    等待 `requestIdleCallback` 事件被触发
    
    > If `requestIdleCallback` isn’t supported, use only the document `load` event.  
    > 如果不支持 `requestIdleCallback` ，则仅使用文档 `load` 事件。
    
4.  Load component Javascript.  
    加载组件JavaScript。
5.  Hydrate component. 水合物组分。

[](#using-multiple-frameworks)Using multiple frameworks  
使用多个框架
----------------------------------------------------------------

Theoretically, we can use multiple framework components in an Astro application. This is a powerful feature, but it shouldn’t be abused.  
理论上，我们可以在Astro应用程序中使用多个框架组件。这是一个强大的功能，但不应该被滥用。

It does make for powerful demos of what’s possible with Astro. However, there are only a few real-world cases where we might want to do this, e.g., composing autonomous micro frontends on an Astro page.  
它确实使强大的演示什么是可能与Astro。然而，只有少数现实世界的情况下，我们可能想要这样做，例如，在Astro页面上合成自主微前端。

Within an Astro component, the following is valid:  
在Astro组件中，以下内容有效：

\--\-
 // import different framework components
 import SpecialReactComponent from '../components/
SpecialReactComponent.jsx'

 import SpecialVueComponent from '../components/
SpecialVueComponent.jsx'

import SpecialSvelteComponent from '../components/
SpecialSvelteComponent.jsx'
\--\-

<!\-- render the components \--\>
<SpecialReactComponent client:load/\>
<SpecialVueComponent client:idle/\>
<SpecialSvelteComponent client:load/\>

Let’s see a real example in practice.  
让我们看看一个真实的的例子。

### [](#an-upvote-counter-in-vue)An upvote counter in Vue  
Vue中的upvote计数器

Recall that we built the initial `UpvoteContent` component using React. We’ll now create the `UpvoteContent` component using Vue and render both components in our Astro project.  
回想一下，我们使用React构建了初始 `UpvoteContent` 组件。现在我们将使用Vue创建 `UpvoteContent` 组件，并在Astro项目中渲染这两个组件。

Here’s the annotated implementation:  
下面是带注释的实现：

<!-- 📂 src/components/UpvoteContent.vue \-->
<script\>
export default {
  data() {
   // data properties used in the UI template
    return {
      upvoteCount: 0,
      maxUpvoteCount: 50,
    };
  },
  methods: {
	// method called when you click the upvote button
    upvote() {
      if (this.upvoteCount < this.maxUpvoteCount) {
        this.upvoteCount++;
      }
    },
  },
};
</script\>

<template\>
  <div\>
    <button
	  // Attach a click event handler and invoke "upvote."
      @click\="upvote"
    >
	 {/\*\* Collapsed svg for brevity \*\*/}
      <svg ../>
      Upvote
    </button\>

    <div\>
      <div\>
        Vue
      </div\>
      <div\>{{ \`${upvoteCount} upvotes\` }}</div\>

	   {/\*\* Increase the width of the div by "count percentage"\*\*/}
      <div :style\="{ width: \`${upvoteCount}%\` }" />

		{/\*\* Render this section only if
		  the count is equal to the max count  \*\*/}
      <div
        v-if\="upvoteCount \=== maxUpvoteCount"
      >
        Max upvote reached
      </div\>
    </div\>
  </div\>
</template\>

And that’s it! 就是这样！

### [](#rendering-different-framework-components)Rendering different framework components  
呈现不同的框架组件

The rendering process for framework components is essentially the same. Let’s go ahead and render the React and Vue `UpvoteContent` components on a new page, as shown below:  
框架组件的呈现过程本质上是相同的。让我们继续在新页面上渲染React和Vue `UpvoteContent` 组件，如下所示：

<!\-- 📂 src/pages/multiple\-frameworks.astro \--\>
\--\-
import { UpvoteContent } from "../components/UpvoteContent.jsx";
import UpvoteContentVue from "../components/UpvoteContent.vue";
import DefaultIslandLayout from "../layouts/DefaultIslandLayout.astro";
\--\-

<DefaultIslandLayout\>
  <UpvoteContent client:load /\>
  <UpvoteContentVue client:load /\>
</DefaultIslandLayout\>

*   We create a new page in `pages/multiple-frameworks.astro`.  
    我们在 `pages/multiple-frameworks.astro` 中创建一个新页面。
*   We import both React and Vue components.  
    我们同时导入React和Vue组件。
*   We render both components in an identical pattern and with the same client directive, `client:load`.  
    我们以相同的模式和相同的客户端指令 `client:load` 渲染这两个组件。

It’s also essential to add Vue support to the project by running the following:  
通过运行以下命令将Vue支持添加到项目中也很重要：

npx astro add vue

This will install the relevant Vue dependencies and add the integration support in the Astro config file.  
这将安装相关的Vue依赖项并在Astro配置文件中添加集成支持。

Once that’s done, we may view the running application on route `/multiple-frameworks`.  
完成后，我们可以查看路由 `/multiple-frameworks` 上运行的应用程序。

[![The React and Vue component rendered in a single Astro page Route.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-13%20at%2015.39.40@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-13%20at%2015.39.40@2x.png)

_The React and Vue component rendered in a single Astro page Route.  
React和Vue组件呈现在单个Astro页面Route中。_  
  
  

As expected, both components are rendered and work just as expected.  
正如预期的那样，这两个组件都按预期进行渲染和工作。

[](#sharing-state-between-component-islands)Sharing state between component islands  
组件岛之间共享状态
-----------------------------------------------------------------------------------------------

As we work with component islands in Astro, you will inevitably need to share certain application states between component islands.  
当我们在Astro中使用组件岛时，您将不可避免地需要在组件岛之间共享某些应用程序状态。

[![Sharing state between two upvote islands.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/islands-share-state.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/islands-share-state.png)

_Sharing state between two upvote islands.  
在两个上投票岛之间共享状态。_  
  
  

For example, let’s assume we want our `UpvoteContent` components to share the same counter values.  
例如，假设我们希望 `UpvoteContent` 组件共享相同的计数器值。

Regardless of the component framework, every framework has its construct for sharing UI state between components, e.g., between React or Vue components.  
无论组件框架如何，每个框架都具有其用于在组件之间共享UI状态的构造，例如，React或Vue组件之间。

However, when working within Astro components, we need a solution that works framework agnostic, i.e., not tied to a single framework.  
然而，当在Astro组件中工作时，我们需要一个与框架无关的解决方案，即：而不是一个单一的框架。

Here are some tremendous framework-agnostic solutions we can choose from:  
以下是我们可以从中选择的一些强大的框架不可知的解决方案：

*   **Signals**: These are great for expressing state based on reactive principles. We may use [signals from Preact](https://github.com/preactjs/signals), [signia from tldraw](https://github.com/tldraw/signia) or [Solid signals](https://www.solidjs.com/docs/latest) outside a component context.  
    信号：这些信号非常适合根据反应原理表达状态。我们可以使用来自Preact的信号、来自tldraw的信号或组件上下文之外的Solid信号。
*   **[Vue’s reactivity API](https://vuejs.org/guide/scaling-up/state-management.html#simple-state-management-with-reactivity-api)**: This can be an excellent ready-to-use solution if you already utilise Vue components in your Astro project.  
    Vue的反应性API：如果您已经在Astro项目中使用Vue组件，这可能是一个优秀的即用型解决方案。
*   **[Svelte’s stores](https://svelte.dev/tutorial/writable-stores)**: This can also be a great out-of-the-box solution if you already use Svelte components in your Astro project.  
    Svelte商店：如果您已经在Astro项目中使用了Svelte组件，这也是一个很好的开箱即用解决方案。
*   **[Nano stores](https://github.com/nanostores/nanostores)**: This is a tiny framework-agnostic library for state management.  
    Nano商店：这是一个用于状态管理的小型与框架无关的库。

In this example, we’ll use Nano stores mainly because they are lightweight (less than 1kb) and don’t add a lot of Javascript footprint to our application.  
在这个例子中，我们将使用Nano商店，主要是因为它们是轻量级的（小于1kb），并且不会为我们的应用程序添加大量JavaScript足迹。

### [](#how-nano-store-works)How nano store works  
纳米商店如何工作

At a high level, what we’re trying to achieve is to remove the state values from within our framework components and manage them via `nanastores`.  
在高层次上，我们试图实现的是从框架组件中移除状态值，并通过 `nanastores` 管理它们。

We’ll create a new `upvoteCounter` state variable within nanostore. We will then propagate changes to this state variable to our framework components.  
我们将在nanostore中创建一个新的 `upvoteCounter` 状态变量。然后，我们将对这个状态变量的更改传播到我们的框架组件。

[![Propagating state variables from nanostore.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/nanostore-share-variable.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/nanostore-share-variable.png)

_Propagating state variables from nanostore.  
从纳米存储区传播状态变量。_  
  
  

### [](#install-nano-store)Install nano store 安装nano store

To use nanostore, we must install the library into our project. Run the following installation command:  
要使用nanostore，我们必须将库安装到我们的项目中。运行以下安装命令：

npm install nanostores @nanostores/vue @nanostores/react

*   `nanostores` represents the base library for creating and managing our state values  
    `nanostores` 表示用于创建和管理状态值的基本库
*   To guarantee that the framework component is re-rendered whenever a state value changes, we will use the React and Vue integrations for nanostores through `@nanostores/react` and `@nanostores/vue`, respectively.  
    为了保证每当状态值发生变化时框架组件都会重新渲染，我们将分别通过 `@nanostores/react` 和 `@nanostores/vue` 对nanostore使用React和Vue集成。

### [](#create-the-state-value)Create the state value  
创建状态值

Our example includes sharing the upvote count value across multiple framework components.  
我们的示例包括跨多个框架组件共享upvote计数值。

To create a state value, nanostores use atoms to store strings, numbers, and arrays.  
为了创建状态值，nanostore使用原子来存储字符串、数字和数组。

Let’s create an atom to hold the counter state variable:  
让我们创建一个原子来保存计数器状态变量：

<!\-- 📂 src/stores/upvote.ts \--\>
import { atom } from "nanostores";

export const upvoteCountStore \= atom(0);

*   We create a new file in `src/stores/upvote.ts`.  
    我们在 `src/stores/upvote.ts` 中创建一个新文件。
*   We import `atom` from `nanostore`.  
    我们从 `nanostore` 导入 `atom`
*   We create a new state number value called `upvoteCountStore`.  
    我们创建一个名为 `upvoteCountStore` 的新状态编号值。

We may think of atoms as small pieces of state to be shared across components in our application.  
我们可以把原子看作是在应用程序中的组件之间共享的小的状态片段。

### [](#using-the-state-value-in-framework-components)Using the state value in framework components  
在框架组件中使用状态值

In the React component, we will leverage the `useStore` hook provided in `@nanostores/react` to retrieve the state value from the `upvoteCountStore`:  
在React组件中，我们将利用 `@nanostores/react` 中提供的 `useStore` 钩子从 `upvoteCountStore` 中检索状态值：

// 📂 src/components/UpvoteContent.tsx

import { useStore } from "@nanostores/react";
import { upvoteCountStore } from "../stores/upvote";

const MAX\_COUNT \= 50;

export const UpvoteContent \= () \=> {
  // Get the state value from the created store
  const upvoteCount \= useStore(upvoteCountStore);

  return (
    <div\>
      <button
        onClick\={() \=> {
          if (upvoteCount < MAX\_COUNT) {
            //Update the store via the set method
            upvoteCountStore.set(upvoteCount + 1);
          }
        }}
      \>
        {/\*\* The rest of the code stays the same \*\*/}
        Upvote
      </button\>
      {/\*\* The rest of the code stays the same \*\*/}
    </div\>
  );
};

The code has been annotated for ease of comprehension. Take a look.  
为了便于理解，代码已经做了注释。看一下

With the Vue component, we may leverage `props` for reactivity as shown below:  
对于Vue组件，我们可以利用 `props` 进行反应，如下所示：

<script\>
  import { useStore } from "@nanostores/vue";
  import { upvoteCountStore } from "../stores/upvote";

  export default {
    // setup props to be used in the UI template
    setup(props) {
      return {
        // Set the value of the upvoteCount from the store
        upvoteCount: useStore(upvoteCountStore),
        maxUpvoteCount: 50,
      };
    },

    methods: {
      upvote() {
        if (this.upvoteCount < this.maxUpvoteCount) {
          // Update the store via the set method
          upvoteCountStore.set(this.upvoteCount + 1);
        }
      },
    },
  };
</script\>

<template\> { /\*\* The rest of the code stays the same \*\*/} </template\>

Lovely! 太好了！

Now, if we try the application, both framework components should have synced upvote values!  
现在，如果我们尝试这个应用程序，两个框架组件应该已经同步了upvote值！

[![Synced upvote state values via nanostores.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-15%20at%2007.20.20.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-15%20at%2007.20.20.png)

_Synced upvote state values via nanostores.  
通过nanostores同步upvote状态值。_  
  
  

[](#passing-props-and-children-to-framework-components)Passing props and children to framework components  
向框架组件传递道具和子项
------------------------------------------------------------------------------------------------------------------------

Most framework components support receiving data via props and children. These are equally supported when rendering framework components in Astro.  
大多数框架组件支持通过props和child接收数据。在Astro中渲染框架组件时同样支持这些。

For example, we currently have the upvote button label hardcoded.  
例如，我们目前已经硬编码了upvote按钮标签。

[![The upvote label.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-05-19%20at%2018.06.54@2x.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-05-19%20at%2018.06.54@2x.png)

_The upvote label. 上投票标签。_  
  
  

We could make this dynamic via props as shown below:  
我们可以通过props使其动态化，如下所示：

// 📂 src/pages/load.astro --- import { UpvoteContent } from
"../components/UpvoteContent.jsx"; import DefaultIslandLayout from
"../layouts/DefaultIslandLayout.astro"; ---

<DefaultIslandLayout\>
  <UpvoteContent client:load label\="Click" />
</DefaultIslandLayout\>

We’d then handle the prop in the `UpvoteContent` React component as usual:  
然后我们会像往常一样在 `UpvoteContent` React组件中处理prop：

// 📂 src/components/UpvoteContent.tsx
export const UpvoteContent \= (props: { label: string }) \=> {
  // ... render props.label
};

It’s important to note that we can pass any primitive as props, and they will work as expected.  
需要注意的是，我们可以将任何原语作为props传递，它们将按预期工作。

However, be careful with function props. Function props will only work during server rendering and fail when used in a hydrated client component, e.g., as an event handler. This is because functions cannot be serialised (transferred from the server to the client).  
但是，要小心使用函数道具。函数props仅在服务器渲染期间工作，并且在水合客户端组件中使用时失败，例如作为事件处理器。这是因为函数不能被序列化（从服务器传输到客户端）。

Children are often treated as a prop type - depending on the framework component used. For example, React, Preact and Solid use the special `children` prop, while Svelte and Vue use the `<slot />` element. These are both supported when working with framework components in Astro.  
根据所使用的框架组件，子项通常被视为道具类型。例如，React、Preact和Solid使用特殊的 `children` 道具，而Svelte和Vue使用 `<slot />` 元素。在Astro中使用框架组件时，这两个组件都受支持。

For example, with our React `<UpvoteContent />` component, we could go ahead and receive a component description as `children`:  
例如，对于我们的React `<UpvoteContent />` 组件，我们可以继续并接收组件描述为 `children` ：

<UpvoteContent client:load\>
  <em\>An upvote counter created using React</em\>
</UpvoteContent\>

This will change nothing until we explicitly handle the `children` prop within the `<UpvoteContent>` component, as shown below:  
这不会改变任何东西，直到我们在 `<UpvoteContent>` 组件中显式处理 `children` prop，如下所示：

// The component accepts props as an argument
export const UpvoteContent \= (props: PropsWithChildren<{}\>) \=> {
  const upvoteCount \= useStore(upvoteCountStore);

  return (
    <\>
      {/\*\* Render the content of the children prop\*\*/}
      <div\>{props.children}</div\>

      <div\>{/\*\* The rest of the component goes here\*\*/}</div\>
    </\>
  );
};

[![Rendering the React component child element.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-15%20at%2012.50.27.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-15%20at%2012.50.27.png)

_Rendering the React component child element.  
渲染React组件子元素。_  
  
  

With our Vue `<UpvoteContent />` component, we could equally receive a component description as children:  
对于Vue `<UpvoteContent />` 组件，我们同样可以接收到一个组件描述作为子组件：

<UpvoteContentVue client:load\>
  <em\>An upvote counter created using Vue</em\>
</UpvoteContentVue\>

However, we must reference this via a `<slot>` element. This is a fundamental difference in how libraries like React / Preact and Vue / Svelte deal with references to the children prop.  
但是，我们必须通过一个 `<slot>` 元素引用它。这是React / Preact和Vue / Svelte等库如何处理对子程序的引用的根本区别。

Here’s how to reference the children element in `UpvoteContentVue`:  
下面是如何引用 `UpvoteContentVue` 中的children元素：

// 📂 src/components/UpvoteContent.vue
<template\>
 <div\>
  <div\>
    <!\-- the slot element renders the children element \--\>
    <slot /\>
  </div\>

  <div\>
   <!\-- The rest of the template goes here \--\>
  </div\>
 </div\>
</template\>

Additionally, we may use multiple slots to group and reference children within our framework components.  
此外，我们可以使用多个插槽来分组和引用框架组件中的子组件。

Consider the following example with multiple children elements:  
考虑以下具有多个子元素的示例：

\--\-
 import { UpvoteContent } from "../components/UpvoteContent.jsx"
\--\-

<UpvoteContent\>
  <ul slot\="social-links"\>
	<li\><a href\="https://twitter.com/understanding-astro"\>Twitter</a\></li\>
    <li\><a href\="https://github.com/understanding-astro"\>GitHub</a\></li\>
  </ul\>

  <em slot\="description"\>An upvote counter created using React</em\>
</UpvoteContent\>

Note that we have two children nodes referenced by the slot names `social-links` and `description`, respectively.  
请注意，我们有两个子节点，分别由插槽名称 `social-links` 和 `description` 引用。

Within `<UpvoteContent />`, we may reference these separately as shown below:  
在 `<UpvoteContent />` 中，我们可以单独引用这些内容，如下所示：

export const UpvoteContent \= ({ props }) \=> {
  return (
    <\>
      <div\>{props.description}</div\>
      <div\>{props.socialLinks}</div\>
      {/\*\* ... \*\*/}
    </\>
  );
};

It is important to note that the `kebab-case` slot names in the Astro component are referenced as `camelCase` values on the `props` object.  
需要注意的是，Astro组件中的 `kebab-case` 插槽名称被引用为 `props` 对象上的 `camelCase` 值。

[![Reference the kebab-case slot names as camelCase in React or Preact.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/kebab_to_camel_case.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/kebab_to_camel_case.png)

_Reference the kebab-case slot names as camelCase in React or Preact.  
在React或Preact中引用kebab-case插槽名称作为camelCase。_  
  
  

In Svelte and Vue, the slots will be referenced using a `<slot>` element with a `name` attribute. Here’s the implementation in `<UpvoteContentVue />` :  
在Svelte和Vue中，插槽将使用带有 `name` 属性的 `<slot>` 元素引用。下面是 `<UpvoteContentVue />` 的实现：

<template\>
  <slot name\="description" /\>
  <slot name\="social-links" /\>
</template\>

Please note how the slot `kebab-case` names are preserved.  
请注意插槽 `kebab-case` 名称是如何保留的。

[![Rendering the React and Vue component children elements.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-16%20at%2008.07.52.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-16%20at%2008.07.52.png)

_Rendering the React and Vue component children elements.  
渲染React和Vue组件子元素。_  
  
  

[](#nested-framework-components)Nested framework components  
嵌套框架组件
--------------------------------------------------------------------

In an Astro file, we may also nest framework components, i.e., pass framework components as children. For example, the following is valid:  
在Astro文件中，我们还可以嵌套框架组件，即，将框架组件作为子级传递。例如，以下内容是有效的：

<DefaultIslandLayout\>
  <UpvoteContent client:load\>
    <div slot\="description"\>
     <!\-- This is a nested <UpvoteContent /\> component --\>
      <UpvoteContent client:load\>
        <em slot\="description"\>This is the nested component</em\>
      </UpvoteContent\>
    </div\>
  </UpvoteContent\>
</DefaultIslandLayout\>

As expected, this renders the nested `UpvoteContent` component:  
正如预期的那样，这将呈现嵌套的 `UpvoteContent` 组件：

[![Rendering nested framework components.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/CleanShot%202023-03-16%20at%2009.00.38.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/CleanShot%202023-03-16%20at%2009.00.38.png)

_Rendering nested framework components.  
呈现嵌套框架组件。_  
  
  

Recursively rendering the same component is rarely the goal we want to achieve. However, rendering nested framework components is powerful because we can compose an entire framework component application as we see fit.  
递归渲染同一个组件很少是我们想要达到的目标。然而，呈现嵌套框架组件是非常强大的，因为我们可以根据需要组合整个框架组件应用程序。

[![Nesting multiple child components to make a more significant application.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/nesting-framework-component.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/nesting-framework-component.png)

_Nesting multiple child components to make a more significant application.  
嵌套多个子组件以生成更重要的应用程序。_  
  
  

[](#astro-island-gotchas)Astro Island gotchas 阿斯特罗岛
---------------------------------------------------

As developers, we are often responsible for inadvertently breaking things. Although debugging can be an enjoyable challenge, consider the following boundaries with Astro Islands.  
作为开发人员，我们经常要对无意中破坏的东西负责。尽管调试可能是一个令人愉快的挑战，但请考虑以下与Astro Islands的界限。

### [](#1-do-not-use-an-astro-component-in-a-framework-component)1\. Do not use an Astro component in a framework component  
1.不要在框架组件中使用Astro组件

Consider the following example of importing a `.astro` component and rendering it within a React component:  
考虑下面的例子，导入一个 `.astro` 组件并在React组件中渲染它：

import { OurAstroComponent } from "../components/OurAstroComponent";

const OurReactComponent \= () \=> {
  return (
    <div\>
      <OurAstroComponent /\>
    </div\>
  );
};

<OurReactComponent client:load /\>

This is an invalid use. The reason is that the React component is rendered a React “island”. Consequently, the island should contain only valid React code. This is the same for other framework component islands.  
这是无效的用法。原因是React组件被渲染为React“孤岛”。因此，这个岛应该只包含有效的React代码。这对于其他框架组件岛是相同的。

[![Do not render an Astro component as a framework component child without a <slot>.](/understanding-astro/understanding-astro-book/raw/master/images/ch4/wrong-astro-island-composition.png)](/understanding-astro/understanding-astro-book/blob/master/images/ch4/wrong-astro-island-composition.png)

_Do not render an Astro component as a framework component child without a slot.  
不要将Astro组件渲染为没有插槽的框架组件子组件。_  
  
  

To overcome this, consider using the slot pattern earlier discussed to pass static content from an Astro component:  
要克服这个问题，请考虑使用前面讨论的slot模式来传递来自Astro组件的静态内容：

\--\-
 import { OurReactComponent } from "../components/OurReactComponent"
import { OurAstroComponent } from "../components/OurAstroComponent"
\--\-

<OurReactComponent client:load\>
 <!\-- pass Astro component as a child via a named slot \--\>
 <OurAstroComponent slot\="description" /\>
</OurReactComponent\>

### [](#2-do-not-hydrate-an-astro-component)2\. Do not hydrate an Astro component  
2.不要水合Astro组件

Consider the following naive example to hydrate an Astro component using a client directive:  
考虑以下简单的示例，使用客户端指令来处理Astro组件：

\--\-
 import { OurAstroComponent } from "../components/OurAstroComponent"
\--\-

<OurAstroComponent client:load /\>

This is invalid. Astro components have no client-side runtime. However, use a `<script>` tag if you need to interactivity.  
这无效。Astro组件没有客户端运行时。但是，如果需要交互性，请使用 `<script>` 标签。

[](#why-islands)Why islands? 为什么是岛屿？
------------------------------------

Typically, most materials would place this section at the start of the chapter. However, there are certain instances where it's more beneficial to showcase practical use cases before diving into the reasons behind them. In addition, this approach could foster an intuitive understanding, which is what I've adopted here.  
通常情况下，大多数材料会将本节放在本章的开头。然而，在某些情况下，在深入了解其背后的原因之前展示实际用例会更有益。此外，这种方法可以促进直观的理解，这就是我在这里采用的。

So, why focus on islands? What advantages do they offer?  
为什么要关注岛屿？它们提供了哪些优势？

### [](#1-performance)1\. Performance 1.业绩表现

One of the main advantages is improved performance. We can significantly enhance our site’s speed by converting most of our website to static HTML and selectively loading Javascript through islands only when necessary. This is because Javascript is one of the slowest assets to load per byte.  
主要优点之一是性能改善。我们可以通过将大部分网站转换为静态HTML，并在必要时通过孤岛选择性地加载JavaScript，从而显著提高网站的速度。这是因为JavaScript是每个字节加载最慢的资产之一。

### [](#2-responsible-hydration)2\. Responsible hydration  
2.负责任的水合作用

If Javascript is expensive to parse and execute, the decision to load it should be carefully taken (from a performance perspective). Also, no one solution fits all application types and use cases. As such, controlling when a component island is hydrated puts you in charge of your website performance.  
如果JavaScript的解析和执行成本很高，那么加载它的决定应该谨慎（从性能的角度来看）。此外，没有一个解决方案适合所有应用程序类型和用例。因此，控制组件岛何时水合可以让您负责您的网站性能。

### [](#3-parallel-loading)3\. Parallel loading 3.平行加载

Lastly, it’s essential to utilise parallel loading. This means that when we load several islands, they won’t have to wait for each other to become hydrated. Instead, each island is considered a distinct unit that loads and becomes hydrated independently, in isolation.  
最后，必须使用并行加载。这意味着，当我们加载几个岛屿，他们将不必等待对方成为水合。相反，每个岛被认为是独立地加载和水合的独特单元，孤立地。

[](#conclusion)Conclusion 结论
----------------------------

In this chapter, we learned about component islands in Astro and how they work. We also explored why framework components are sometimes preferred over vanilla Javascript or Typescript via a `<script>` element.  
在本章中，我们了解了Astro中的组件岛及其工作原理。我们还探讨了为什么框架组件有时会比vanilla JavaScript或Typescript更受欢迎，而不是通过 `<script>` 元素。

We also went through the steps to use a framework component in an Astro application, including building a static site, installing the framework, and writing the component. Finally, we experimented using a React and Vue component to demonstrate the use of framework components. See you in the next chapter!  
我们还介绍了在Astro应用程序中使用框架组件的步骤，包括构建静态站点、安装框架和编写组件。最后，我们尝试使用React和Vue组件来演示框架组件的使用。下一章再见！
