---
thumbnail: 'https://picsum.photos/1280/720?random=5 #111'
title: Gitå¸¸ç¨å½ä»¤
date: 2021-12-06 22:43:43
tags:
- ð¥åç«¯
- ðç¬è®°
- ð¥Git
---

# æ¥çç¨æ·ååé®ç®±å°å

 `git config user.name  git config user.email`

# ä¿®æ¹ç¨æ·ååé®ç®±å°å

  `git config --global user.name  "xxxx"   git config --global user.email  "xxxx"`

# åå»ºSSHå¯å

`ssh-keygen -t rsa -C "ï¼é®ç®±ï¼"`

# åéè¿ç¨ä»åº

`git clone` 

# æå­æ´æ¹

`git add .`

# æäº¤æ´æ¹

`git commit -m 'xxxx'`

# æ¥çæäº¤æä»¶æ¯å¦ä¿®æ¹

`git status`

# æ¥çåå²æäº¤ï¼ç®æ çæ¬ï¼

`git log`

# æ¥çææåæ¯

`git branch -a`

# åæ¢åæ¯

`git checkout (åæ¯å)`

# ä»è¿ç¨åæ¯ä¸è½½ææ°ä»£ç å¹¶åå¹¶

`git pull (è¿ç¨ä»åºå) (è¿ç¨åæ¯)`

# ä»è¿ç¨åæ¯ä¸ä¼ ææ°ä»£ç å¹¶åå¹¶

`git push (è¿ç¨ä»åºå) (è¿ç¨åæ¯)` 

# è¯¥éé¡¹å¯ä»¥åå¹¶ä¸¤ä¸ªç¬ç«å¯å¨ä»åºçåå²

`git pull origin master --allow-unrelated-histories`

# æ°å»ºè¿ç¨ä»åºå°å

`git remote add <è¿ç¨ä»åºå> <è¿ç¨ä»åºå°å>`

# åéçæ¬æä½

`git reset --hard <ç®æ çæ¬>`

`git checkout (åæ¯å)`

# æäº¤æ¶ä¸ä¼çææ°çæäº¤

`git add .`

`git commit --amend`

`git push -f`
