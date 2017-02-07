---
layout: post
title: Publishing a book on Leanpub
sortorder: 4068
date: 2016-09-01
updated: Jan 5 2017
ignoredate: 0
photo-front-url: /res/blog-erlang-card.jpg
photo-front-class: grid-image-wrapper-square
disqus_comments: 1
disqus_identifier: 2016-09-01-leanpub-scrivener
ignoreall: 0
---

**A few days ago I published my first book on Leanpub. Overall, it was a very good experience with no major problems.**

[Leanpub](https://leanpub.com) is a self-publishing platform that encourages *lean* publishing: Even if the book is not finished it should be made available to potential readers and buyers. It is like a kickstarter book project where readers support the writing of a book, not knowing if they will ever get a finished product.

It is a good idea to publish the book in its infant state, but there are pitfalls as well. I published the first chapters of the book and then it stayed there for a long time, because I was contracted for an unexpected project and could not write. Fortunately the readers I had at that time did not demand their money back. It was a bit embarassing for me - all the time estimations I had were completely blown away.

Estimations were also wrong, because unexpected issues can occur:

* Code highlighting was not always working. I have to stress that this issue also had to do with misunderstandings how the highlighting engine works. In any case, whenever I went to Leanpub's Google group my issues were answered within the delays of dfferent time zones and support was very helpful.
* Formatting with markdown did not always bring the expected result. I remember trying to define a table and wasted a whole day making this work. It is this sort of problem where you have something working, then you add a feature like in this case a row or column and it totally falls apart. Eventually I gave up and formatted it in a different way, because *epub* and *mobi* would not render the table as I wanted anyway.
* I had to work out my writing process and it took me a while until I was happy.

Once everything was in place and my external project had finished writing the book was moving on a fair pace. The most important thing that can be said about Leanpub is that it never got into my way. When I wanted to create the book to preview it is was just doing it without any problems. I used Dropbox publishing, so my texts were copied to the shared folder and the results were loaded to this folder as well where I could download it from. There were a few times when the website was not available, but I guess this had to do with the different time zones and nightly maintenance on the Leanpub servers.

Let's examine my writing process a little bit more:

* As mentioned before, all file exchange between my computer and Leanpub was done via a Dropbox shared folder.
* I did not want to work on the Dropbox folder, so I created a project on my computer as working folder.
* Being a software developer, I set up a git project to make sure I have versions of my files and pushed the local repository to a private GitHub repository.
* I also did not want to work directly on the markup files that are used to create the book. The reason again is to keep files I work on separated from the files I created a book from, even if it is a preview only. Both sets of files are in the git repository and if something goes wrong - and it will! - it is possible to go back to a previous version.
* All this sounds a bit complicated, but I never lost anything I have written. It needs a fair amount of copying text, though. This can be achieved by doing it manually or automating it. I wrote some scripts for automation, but most of the time I just copied changed text around, especially at a later stage of the book. Sometimes it is good not to trust your own programming abilities 100%...
* It is not only text that had to be copied, but also images and code examples. One of the challenges was to keep the running number of the code examples correct. The examples are numbered like *Example 4-2* which means example number two in chapter 4. First, I went through the chapters and did the numbering manually, but when the chapters got larger and the changes more, I just wrote a small Perl script to automate this task.
* A very important, but also a bit boring task is proof reading before it can be given to somebody else for editing. Reading through 300 pages again and again is not very pleasant and takes some time.

I wrote the book on a MacBook Pro with lots of memory to have all applications I need opened including one or two virtual machines. My editor for the text is [Scrivener](https://www.literatureandlatte.com/scrivener.php) - I used it for some time now and it deserves its own blog post. For the code I used different editors, but mostly [Atom](https://atom.io/).

Leanpub also provides a PDF version that can be uploaded to Amazon for offering a print-on-demand book. In fact, they encourage authors to do this once the book is 100% finished. In my case the publisher Apress approached me and in December 2016 the book was published by them. This means that I had to take down the book on Leanpub and it is not available there anymore.

**Conclusion**

It was a very good experience for me to publish on Leanpub. They don't take a lot of money, so there is a nice chunk of royalties left. I can only recommend it to anyone who wants to publish a book.
