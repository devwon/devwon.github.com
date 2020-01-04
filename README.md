## devwon.github.io

> Mickey 테마로 만든 혜린의 jekyll blog

![devwon's blog screenshots](/assets/images/demo.png "devwon's blog")

## Images

1. devwon.github.io/assets/images/ : 로고 이미지, 아이콘 등
2. devwon.github.io/assets/images/hero/ : 콘텐츠 내의 이미지
2. devwon.github.io/assets/images/thumbnail/ : 메인 페이지의 썸네일 이미지

## Development

[블로그 글 업로드 순서]
1. _posts/ 에 마크다운 파일 추가(주로 github editor를 쓰는 편..)
2. git pull
3. html파일 생성 : jekyll build --incremental --watch (auto-regeneration) *- -no -watch 로 쓰면 자동으로 재생성 안됨 (yaml 파일 수정 후 jekyll serve 필요)
4. 정상적으로 노출되는지 확인

참고)
한 가지 알아둘 점은, _config.yml 파일은 수정해도 바로 반영되지 않습니다. 이 파일은 jekyll serve를 Ctrl-C를 입력해 종료하고 다시 실행해야 반영됩니다.
jekyll serve 명령은 실행하면 _site 디렉토리의 파일들을 전부 다시 생성합니다. 블로그의 규모가 작을 때는 문제가 되지 않지만, 커졌을 때는 생성에 걸리는 시간이 부담스러울 수 있습니다. 그럴 때는 --skip-initial-build라는 option을 사용하면 생성 과정을 생략하고 바로 웹 서버가 동작합니다.

During development, simply run `gulp` in terminal and it will compile the jekyll site, compile Sass, create post thumbnails, launch BrowserSync & watch files for changes and recompile.

Source Sass files are located in `_scss/`, included into `main.scss`, and compile to `assets/css/main.css`.

Post thumbnails are automatically resized via Gulp's image resize package, and moved to `assets/images/thumbnails`. Any featured images you put in `assets/images/hero` will be automatically created

## plugins

1. 댓글 : [disqus](https://disqus.com)
2. 메일 구독 : [mailchimp](https://mailchimp.com)

+추가 예정

## Author of theme

**Vincent Chan**
- <https://github.com/vincentchan>
- <https://twitter.com/vincentchan>

See Mickey in action with [the demo site](http://vincentchan.github.io/mickey) or [Author's blog](http://aneverendingdream.com).


## License

Open sourced under the [MIT license](LICENSE.md).

**Disclaimer: This Jekyll theme is not affiliated with Disney. Obviously :)**
