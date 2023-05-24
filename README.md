# Re:View 40秒で支度しな

40秒で技術書典向けの出稿用フォーマット編集＆出力環境をInitするやつ

* 出典: [WindowsでDocker+Re:VIEWを使う](https://github.com/vvakame/docker-review/blob/master/doc/windows-review.md)

# QuickStart

## GUIレイアウト による初回生成.

localhost:18000 へアクセスし初回の生成をする

```bash
$ docker compose run --rm --service-ports review review-init -w sampledoc
...
 => => naming to docker.io/vvakame/review:5.7                                                                                                0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
Please access http://<thishost>:18000 from Web browser.
[2023-05-24 05:19:26] INFO  WEBrick 1.6.1
[2023-05-24 05:19:26] INFO  ruby 2.7.4 (2021-07-07) [x86_64-linux-gnu]
[2023-05-24 05:19:26] INFO  WEBrick::HTTPServer#start: pid=1 port=18000
[2023-05-24 05:24:46] INFO  going to shutdown ...
[2023-05-24 05:24:47] INFO  WEBrick::HTTPServer#start done.
$ 
```

## PDF生成

出力できたこと確認する

```bash
$ cp docker-compose.yml Dockerfile sampledoc/
$ cd ./sampledoc
$ docker compose run --rm review rake pdf
 version            Show the Docker-Compose version information
$ docker compose run --rm review rake pdf
[+] Running 1/1
 ⠿ Network sampledoc_default  Created                                                                                     0.6s
review-pdfmaker  config.yml
ℹ INFO    compiling sampledoc.tex  
⚠ WARN sampledoc.re:1: headline is empty.
⚠ WARN sampledoc.re:1: headline is empty.
ℹ INFO    uplatex -interaction=nonstopmode -file-line-error -halt-on-error __REVIEW_BOOK__.tex
ℹ INFO    uplatex -interaction=nonstopmode -file-line-error -halt-on-error __REVIEW_BOOK__.tex
ℹ INFO    uplatex -interaction=nonstopmode -file-line-error -halt-on-error __REVIEW_BOOK__.tex
ℹ INFO    dvipdfmx -d 5 -z 9 __REVIEW_BOOK__.dvi
✔ SUCCESS built book.pdf           
$ 
```

以後、sampledoc/sampledoc.re など書籍の内容を作っていく。

Fin.