---
title: "github git삭제 후 다시 git 생성"
categories: github
---

1) rm -rf .git

2) 현재 소스들로 git repository 다시 생성하기

git init

git add README.md

git commit -m "first commit"

git remote add name https://(저장소 주소)

git push -u origin master

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
