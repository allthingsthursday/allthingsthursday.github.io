---
layout: post
title: "Creating an AngularJS app"
date: 2014-09-08
tags: ['SEP']
---

After working on a few projects where a significant portion of the development is done in AngularJS, I have had grandiose ideas of writing some blog posts about the world of AngularJS. It's a wonderful world where JavaScript development does not have to be painful or overly messy and code can be unit tested. 

While deciding what kind of pet project I would use for the aforementioned blog posts, I decided to start setting up the environment. I copied over the seed app and started adjusting dependencies when I realized that this was the better place to start: how do you set up the environment and app for development?

This post will provide a quick-start guide for getting a basic AngularJS app up and running for development on Windows using the angular-seed project on GitHub. Most of the below instructions can also be found in the angular-seed README.md file, but if you are lazy like me, just read on.

Before getting started, you will need [Node.js][node] and [Git][git]. You most likely have them already. If you don't, you should, so go install them...

If you want to set up automatic unit test feedback, you will also want to install [PhantomJS][phantom] and [Growl][growl].

Ok, now that you have everything you need, the easiest way to get started is to clone the angular-seed project on GitHub. 

<code>git clone https://github.com/angular/angular-seed.git</code>

Copy the contents of this directory, minus the .git folder and .gitignore file, to your project root. I do it this way so I can keep a clean local version of the angular-seed project ready to go. Once you have done this once, you can start from this step and be up and running pretty much instantly.

Next, install the packages and dependencies, by running <code>npm install</code> from your project root. This will install all the node packages listed in package.json along with the bower packages listed in bower.json.

Once the default packages are installed, there are a few additions I like to make:

<pre><code>npm install karma-jasmine --save-dev
npm install karma-phantomjs-launcher --save-dev
npm install karma-growl-reporter --save-dev
</code></pre>

Finally, to update karma.conf.js to use PhantomJS to run unit tests and report the results through Growl, make sure the 'browsers' and 'plugins' entries match below and add the 'reporters' entry:

 
{% highlight javascript %}
    browsers : ['PhantomJS'],

    plugins : [
            'karma-chrome-launcher',
            'karma-firefox-launcher',
            'karma-phantomjs-launcher',
            'karma-jasmine',
            'karma-junit-reporter',
            'karma-growl-reporter'
            ],

    reporters : ['growl','progress'],
{% endhighlight %}

You're ready to go. To start your test runner, from your project root, run <code>npm test</code>. Each time you save a change, your karma tests will run and report status via Growl.

To start a local web server, run <code>npm start</code>.

That's it. You now have an AngularJS app ready for development. Happy coding!

[node]: http://nodejs.org
[git]: http://git-scm.com
[phantom]: http://phantomjs.org/download.html
[growl]: http://www.growlforwindows.com/gfw/

