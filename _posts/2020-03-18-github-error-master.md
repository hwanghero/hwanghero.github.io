---
title: "git push ([GIT err]! [rejected] master -> master (fetch first)"
categories: github
---
https://m.blog.naver.com/PostView.nhn?blogId=chandong83&logNo=220745427790&proxyReferer=https%3A%2F%2Fwww.google.com%2F

To https://github.com/chandong83/pi_qt5.git
! [rejected] master -> master (fetch first)
error: failed to push some refs to 'https://github.com/chandong83/pi_qt5.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

처음으로 github를 사용해보려하다가
실수로 잘 못 만들어서 다 없고 다시하려고 하는데
위와 같이 에러가 나면서 진행이 안됐다.

결론적으로는 기존 데이터가 손실이 있을 수 있어서 진행이 안되게 하는것이다.

아래처럼 명령으로 업로드하면 강제로 진행을 할 수 있게 된다.
단, 기존 데이터는 보장 못한다.
git push origin +master

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
