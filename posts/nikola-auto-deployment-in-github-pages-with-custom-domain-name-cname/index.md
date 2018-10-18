<!--
.. title: nikola auto deployment in github pages with custom domain name (CNAME)
.. slug: nikola-auto-deployment-in-github-pages-with-custom-domain-name-cname
.. date: 2018-10-18 22:10:45 UTC+08:00
.. tags: nikola, github, git
.. category: 
.. link: 
.. description: 
.. type: text
-->

Nikola has a neat feature that could deploy automatically in github pages, and it create master branches to fit the gh_pages deployment purpose and scr branch to records the raw data of config, theme, posts and so on.

While github pages is applicable to using the custom domain name accordingly, which acutally creating a CNAME file with xxx.youdomain.com as contents.

It seems currently Nikola did not expected that CNAME as master's content so you have to checkout master manually, and add that CNAME file with the domain name you intend to use, and push into github by youself. * Reminding * the CNAME file created in src branch won't work since nikola github_deploy would ignore and won't copy CNAME into master branch. So if you don't do it manally the auto deploy would be over written again & again even through you settle down the domain name in setting page of github repo or added in "src" branch. 

BTW, the even .gitignore need to double check also in master branch, all these branches would share this simple config file...
