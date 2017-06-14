---
layout: post
title:  "commandlinefu"
date:   2017-05-22 18:00:00
categories: wisdom
---

[http://datascienceatthecommandline.com/](http://datascienceatthecommandline.com/)

```bash
$ sudo pip install csvkit
$ csvlook --help
$ echo -e "a,b\n1,2\n3,4" | csvlook
|----+----|
|  a | b  |
|----+----|
|  1 | 2  |
|  3 | 4  |
|----+----|
```

Pipe Viewer (pv): meassure / throtle: [http://www.commandlinefu.com/commands/view/4434/live-ssh-network-throughput-test](http://www.commandlinefu.com/commands/view/4434/live-ssh-network-throughput-test)


All Time Greats: [http://www.commandlinefu.com/commands/browse/sort-by-votes](http://www.commandlinefu.com/commands/browse/sort-by-votes)

```bash
$ basename a/b/c/foo.txt
foo.txt

$ dirname a/b/c/foo.txt
a/b/c
```

```bash
sudo !! # run last command as root
```

```bash
python -m SimpleHTTPServer
```

```bash
'ALT+.' # place last argument
```

```bash
mount | column -t
```

```bash
echo "ls -l" | at midnight
```

```bash
sshfs name@server:/path/to/folder /path/to/mount/point
```
