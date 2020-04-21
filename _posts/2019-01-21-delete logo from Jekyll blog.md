---
published: true
---
## To delete the logo from your blog on Jekyl

I chose the Sleek template for my blog on Jekyll. But ought to change the logo name: Sleek on the top left side of the blog. In html language, the logo that appears on the left side of the header.html. 

I tried to change the name of the logo by accessing the **logo.svg** file under **blog/includes/** on my blog repository that I forked to my git repo. The file stores an id under **<path>**, which entails the name of the logo. The content in the file (name of one’s **git repo/blog/_includes/logo.svg**) looks like the following:

<svg class="logo" …
<g id="logo"...
**<path d=.............id="name of the logo"></path>**
</g>
</svg>

But that did not work. 

A workaround I tried removed the logo entirely from the header. Because the logo is a part of the header on the blog page, I accessed header.html under **my_git_repo_name/blog_/includes/** (here one’s git repo name appears in the place of my_git_repo_name).

The html file includes the following classes (not exactly in the following order):
<header>
<div>
<a>
<span>

Under the **<div class="header__logo--container">** appears the following line:
**{% include logo.svg %}**

I removed the line and published the blog. The logo disappeared. 

**Before removing the line:**							
<div class="header__logo--container">      
{% include logo.svg %}                          
</div>

**After removing the line:**
<div class="header__logo--container">
</div>

The logo still appears in the **logo.svg** file under **blog/_includes/** but does not appear on the header of the blog page.
