---
layout: post
title:  "tabulator character and column command"
date:   2020-06-10 10:00:00
categories: devops
---

In the bash escape sequences can be interpreted in a string with prepended dollar and single quotes:

```bash
echo $'one\ttwo'
```

the **tabulator** character seperates table cells better then spaces or semicolons

TSV is better CSV. If you have to deal with excel on window use a tab seperated csv file in UTF-16 with **byte order mark**.

Editors have a **tabstop** in spaces or inch in the case of ms word.

The unix command **column** calculates the neede tabstop over all rows and displays the data nicely formated:

```
mysql -u root -pxxxxxx -B -e "select * from customer;" mydatabase | column -t -s $'\t'
```

As can be seen here this is handy for mysql because it seperates table cells with tabs with the shell client

the mount command uses only a space to seperate data, but can be also formated nicely as a table:

```
mount | column -t -s " "
```

