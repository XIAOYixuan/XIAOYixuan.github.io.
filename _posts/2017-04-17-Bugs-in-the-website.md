---
title: "Bugs in the websit"
tags: [Jekyll, website]
---
Just a tiny post.

I'm experiencing (maybe) some bugs in my blog project. Everything works fine when I use jekyll serve, and my mathjax support and new posts presentation suck when I upload my websit to my github repo...

Still figuring out why...But just too many exams coming. Busy AF these days.  I will probably fix them in May...

-----maybe 4 hours later-------
fixed

The following scrips should be added to _include/script, not the html files in layout.
```html
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ TeX: { equationNumbers: { autoNumber: "all" } } }); </script>

<script type="text/x-mathjax-config">
          MathJax.Hub.Config({
           tex2jax: {
             inlineMath: [ ['$','$'], ["\\(","\\)"] ],
             processEscapes: true
           }
         });
</script>
  
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
       
```

[This blog](http://csega.github.io/mypost/2017/03/28/how-to-set-up-mathjax-on-jekyll-and-github-properly.html) is helpful.

