---
title: DustJS | Getting Started
layout: guides
permalink: /guides/base-and-override-templates/
---

# Base and Override Templates

An important need in developing a multi-page web application is to have common elements of the pages defined just once and shared by all pages (<a href="http://en.wikipedia.org/wiki/Don%27t_repeat_yourself\" target="_blank">DRY - Don't repeat yourself</a>). Dust provides this with the concept of blocks, inline-partials, and base and override templates. Consider a common case where several pages share a header and footer but have different body content.

Blocks in the base template can contain default content and a child template can override that content. A block tag has the form of {+name}default Content{/name}. In the following example, the base template has three blocks: pageHeader, bodyContent, and pageFooter. The pageHeader and pageFooter have default content that is shown if the child template does not override them.  You'll notice below that without a child template, the base template renders the default header and footer content, but no body content.

<dust-demo template-name="base-template">
<dust-demo-template>&lt;div class=&quot;page&quot;&gt;
  &lt;h1&gt;{+pageHeader}LinkedIn{/pageHeader}&lt;/h1&gt;
  &lt;div class=&quot;bodyContent&quot;&gt;
    {+bodyContent/}
  &lt;/div&gt;
  &lt;div class=&quot;footer&quot;&gt;
    {+pageFooter}
       &lt;a href=&quot;/contactUs&quot;&gt;Contact Us&lt;/a&gt;
    {/pageFooter}
  &lt;/div&gt;
&lt;/div&gt;
</dust-demo-template>
<dust-demo-json>{}</dust-demo-json>
</dust-demo>


Now that we have defined a base template with the named blocks pageHeader, bodyContent, pageFooter , let's look at how a child template can use it to supply body content and override the pageFooter. First, you insert the base template as a partial. Then you use one or more "inline partials" defining the values for the named blocks in the template.  You'll see in the example below that we override the bodyContent block and the pageFooter block, while we leave the pageHeader block alone, thereby using it's default.

<dust-demo template-name="child-template">
<dust-demo-template>{! First, insert the base template as a partial !}
{&gt;&quot;base-template&quot;/}
{&lt;bodyContent}
&lt;p&gt;This your body&lt;/p&gt;
{/bodyContent}
{&lt;pageFooter}
       This is your NEW footer
{/pageFooter}
</dust-demo-template>
<dust-demo-json>{}</dust-demo-json>
</dust-demo>

One thing to be wary of is that the name given to inline partials are global to that template chain.  For example, {<name}xxx{/name}, defines the generic "name" as an inline partial. This may be what you want, but remember the pains caused by global variables in JavaScript.  Only use generic names for inline partials with the knowledge that a template later in the chain can override it.