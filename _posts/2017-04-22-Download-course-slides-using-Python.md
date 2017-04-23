---
title: "Download lecture slides using Python"
tags: [Tricks, Web Scraping]
---

Recently I've got a lot of things to do...including downloading files from course webpages. Quite annoying that I have to click the download button on different pages again and again.

This is a  note about what I've done to download slides(pdf) using Python. The basic idea is quite straight-forward:

+ parse the html and extract all the pdf links using [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
+ download pdf files using [urllib2](https://docs.python.org/2/library/urllib2.html)

To be explicit, [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) is a library that could pull data out of html files. Therefore we first need to download the html file which contains the pdf links.

```python
import urllib2
from bs4 import BeautifulSoup as bs
# open the url and return the context(string)
response = urllib2.urlopen(url)

# parse the context using 'html5lib' parser
soup = bs(response, 'html5lib')
```
Then we interate through all the lines with the <a\>   tag and grab the pdf URLs within that tag. This step is crazily easy using BeautifulSoup.



```python
filetype = "pdf"
hostname =  "https://arxiv.org"

for i, link in enumerate(soup.findAll('a')):
	if filetype not in str(link): continue 
	pdf = link.get('href').strip()
	# join links to get pdf's complete link
 	pdflink = urllib2.urlparse.urljoin(hostname, pdf)
```
**Caveat**: *link.get()* actually returns the **relative path **of the pdf file, which is also the **absolute path** for the **current host**, we need the **complete path** to download files, which is the concatenation of the current host name and relative path. 

For example, suppose we wanna download a paper from https://arxiv.org/abs/1508.07909 and the relative path is "\pdf\1508.07909", then the complete path is:
	
+ "https://arxiv.org" + "\pdf\1508.07909" = "https://arxiv.org/pdf/1508.07909.pdf"

Finally, we create an empty pdf file and write the data grabbed from pdflink into it.
```python
	# open the pdflink	
	pdfRes = urllib2.urlopen( pdflink) 
	# extract file name
	pdfName = pdf[ pdf.rfind('/')+1 : ]
	
	pdfFile = open(pdfName, 'wb')
	# get data from pdflink
	pdfFile.write( pdfRes.read() )
	
	pdfFile.close()

```

<br>


## Other related materials:

+ [Here](http://web.stanford.edu/~zlotnick/TextAsData/Web_Scraping_with_Beautiful_Soup.html) is a more detailed tutorial  about **web scraping with BeautifulSoup**.


+ Comments under [this question](https://www.reddit.com/r/learnpython/comments/3deixu/how_to_write_a_python_script_to_download_all_the/) refer downloading files using **wget** on Linux.

+ [This page](http://www2.warwick.ac.uk/fac/sci/statistics/staff/academic-research/firth/software/pdfjam/) introduces a very powerful and light command **pdfjam**. It surpports common pdf operations. like joining and n-upping. My top 2 favourites:

	+ joining: ```pdfjam a.pdf b.pdf -o notes.pdf```
	+ n-upping: ```pdfjam --nup 3x2  --landscale *.pdf -o slides.pdf```

