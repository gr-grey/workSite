---
title: quartz website setup
date: 2024-02-28
description: "The equivalence of forking multiple quartz."
tags: records
---

If we want multiple quartz websites (e.g. one for serious stuff one for fun), we need multiple repos.
But github does not allow forking a repo twice, so here's a workaround.

```bash
git clone https://github.com/jackyzha0/quartz.git gr-grey.xyz
# cd to dir
git remote remove origin
git remote add origin git@github.com:gr-grey/gr-grey.xyz
git push -u origin v4

# set upstream for future updates
git remote add upstream https://github.com/jackyzha0/quartz.git

npm i
npx quartz create

npx quartz build --serve --port 8081 
# or
npx quartz build --serve --port 8081 --wsPort 3002
```

Basically by cloning the repo and reset origin, we link it to our own github account, and by setting upstream we can sync it when quartz version is updated.