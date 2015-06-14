---
layout: post
title: Time with Aurelia
date: 2015-05-01
sortorder: 4090
---

**The year 2015 started with the preview-release of a new Javascript framework: Aurelia. Web developers are not really dhort of frameworks, but somehow nobody is fully satisfied with the offers. I decided to take a closer look.**

Introduction Aurelia
I assume in the following description that you have gone through the getting started tutorial and have setup your environment.

Introduction Kanban Board Light application

Step 1:
I started to copy a few folders and files from the skeleton project into a folder that only had the license and readme file from a new GitHub repository and the hidden .git-folder.

img

The gulp definition file (gulpfile.js) just links to the files in the build-folder, which define tasks like *watch*, *serve* etc. and does not need to be changed. The file package.json will be familiar to Node.js developers. I changed title, author name, urls etc and I also removed the bootstrap and font-awesome packages to have a clean minimal install.

img

Step 2:
The commands npm install and jspm install -y download and create node-modules and download javascript files. This process takes a little while, but eventually the application folder presents itself like this:

Two folders (node_modules, jspm_packages) were created and also the file config.js, which contains the jspm configuration similar to package.json for npm.
There are lots of files in those two folders, but for now we take it as it is without looking into details what the files are are.

Step 3:
Before we forget, let's add a .gitignore file and add the folders jspm_packages and node_modules to it, otherwise about 160 MB would be stored unnecessarily on GitHub.

Step 4:
So far, there is only the framework in the application folder. We need to create the entry point for the application. I opted to use the attribute aurelia-main as body attribute, which gives more freedom with configuring modules that are used. So we create index.html in root, create a folder src and add a file main.js with the following content:

{% highlight javascript linenos %}
export function configure(aurelia) {
  aurelia.use
  .defaultBindingLanguage()
  .defaultResources()
  .router()
  .eventAggregator()

  aurelia.start().then(a => a.setRoot('landing', document.body));
}
{% endhighlight %}

We set the root of our application to landing, so we need to create a landing.html and a landing.js file in src. The html is simple:

{% highlight html linenos %}
<template>
  <section>
    <h2>${pagetitle}</h2>
  </section>
</template>
{% endhighlight %}

The corresponding js file just defines a model class with one property:

{% highlight javascript linenos %}
export class PageConfiguration{
  constructor(){
    this.pagetitle = 'Kanban Board Light';
  }
}
{% endhighlight %}

Running the command gulp serve or gulp watch builds the ES5 js files and runs a server. Neat is that with gulp watch a browserlink is established and whenever a file in src changes, a re-build starts and the browser is updated, tested with Chrome and IE on a Windows 8.1 system.

Step 5:
We need to setup routing. Our *application* has two pages - a home page with a list of projects and a project details page.

Step 6:
Both our pages use external libraries.
For the project details page we use drag and drop. The javascript library interact.js encapsulates all the features we need.
The home page has a chart to indicate the activity in projects - we use the TreeMap control from Syncfusion's Essential Studio.

How do we integrate these libraries without breaking Aurelia's spirit?
