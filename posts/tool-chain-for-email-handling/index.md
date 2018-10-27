<!--
.. title: tool chain for email handling
.. slug: tool-chain-for-email-handling
.. date: 2018-10-27 21:15:57 UTC+08:00
.. tags: tool, email, vim
.. category: tool
.. link: 
.. description: 
.. type: text
-->

# Background
Using email everyday, so the efficiency to handle email defines the efficiency of your day.

# Email handling principle 
1. Limit the access or notification of email, but pull the update with specific timeslot per day.
2. Get rid of redundancies like HTML email, but pure text (or markdown into html automatically if needed)
3. Filtering, Labeling and "Zero Inbox" is key for email handling

# Tool Chain for email
After searching for years, these tools are choosen for efficient email handling:

Email Client: Neomutt together with mbsync, msmtp; 
Filtering: marina or mu;
Editor: vim with muttdown;
Calendar: ? TBD with one terminal tool, 
Contact: abook with khard? ;
Misc: urlscan, w3m, gpgme, etc; 

# Working flow and procedure

## Config Email
TBD, suggest follow dotfile procedure.


## Recieving Email

Taking your specific time slot for email, than just open terminal and:
```shell
mbsync -a 
```
## Sorting/Labeling Email

## Write Email
Vim would be the major working force for this task with fancy tools included such as auto complete and spell checking.

### Raw Text
Normal working follow editing txt file in vim. 
TBD for special plugin to handle email more efficiently.

###Rich Format
Add muttdown for sending out rich format by using muttdown.

### Spellcheck: vim
To move to a misspelled word, use **]s** and **[s**. 
**z=**, and Vim will suggest a list of alternatives that it thinks may be correct.
**zg** command and Vim will add it to its dictionary.
You can also mark words as incorrect using **zw**.

```vim
;enable spell
set nospell
;disable spell
set spell
;change default lang
set spell spelllang=en_us
```
## Calendar handling

## Contact 
Abook auto complete integration
How to sync with cloud.

# Reference

* [hwo to spell check within vim](https://www.linux.com/learn/using-spell-checking-vim)
* [muttdown](https://github.com/Roguelazer/muttdown)
* [a modern setup of mutt](https://webgefrickel.de/blog/a-modern-mutt-setup)
* [why mu](http://blog.iodoru.org/post/2017-07-18-mu/)
