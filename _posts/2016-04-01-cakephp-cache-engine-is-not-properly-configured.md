---
layout: post
title: "CakePHP: \"Cache engine is not properly configured\" Error"
date: 2016-04-01 15:04:00
author: Mitchell Artin
tags: open-source php frameworks error tutorial
category: blog
---
I was working on a CakePHP site (v. 3.2.3 with PHP 7.0.5) and got the following unhelpful error:
```
Cache engine Cake\Cache\Engine\FileEngine is not properly configured.
RuntimeException
```

![CakePHP Cache engine Error]({{ site.baseurl }}/assets/posts/cakephp_cache_engine_error.png)

I resolved this by correcting permissions on the 'logs' and 'tmp' directories in my web app directory.  When installing with CakePHP with Composer, by default it will give 'logs' and 'tmp' directories globally writeable permissions.  You can restore these with the following command
```
chmod 777 tmp -R
chmod 777 logs -R
```

However, this can definitely be more secure.  Change the owner of these directories to the account your http daemon runs as.  Make sure that this user only has write permissions recursively to these directories.

Stumbled upon this page and have no idea what CakePHP is?  It is a PHP framework that follows the MVC architecture to make development faster and easier.  [Check it out!](http://cakephp.org)
