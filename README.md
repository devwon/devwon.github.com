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
=======
# Jekyll Tipue Search

Full-text search in Jekyll with [Tipue Search](https://github.com/Tipue/Tipue-Search). No plugin necessary. Fully compatible with Github Pages.

The search index at `tipuesearch/tipuesearch_content.js` is generated with Liquid. The [Tipue Search jQuery plugin](http://www.tipue.com/search) uses Javascript to search the index and display a list of results.

View a [live demo running on Github Pages](https://jekylltools.github.io/jekyll-tipue-search/search/). The code and configuration for the demo is in the [gh-pages branch](https://github.com/jekylltools/jekyll-tipue-search/tree/gh-pages).

## Installation

1. Add the `assets/tipuesearch` folder and all contents to your site.

2. Add the Tipue Search scripts & styles to your theme head. Some of these lines are [optional, see the docs for info](http://www.tipue.com/search/docs/?d=1):

  ```
  {% if page.tipue_search_active or layout.tipue_search_active %}
  <link rel="stylesheet" href="{{ "/assets/tipuesearch/css/normalize.css" | relative_url }}">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
  <script src="{{ "/assets/tipuesearch/tipuesearch_content.js" | relative_url }}"></script>
  <link rel="stylesheet" href="{{ "/assets/tipuesearch/css/tipuesearch.css" | relative_url }}">
  <script src="{{ "/assets/tipuesearch/tipuesearch_set.js" | relative_url }}"></script>
  <script src="{{ "/assets/tipuesearch/tipuesearch.min.js" | relative_url }}"></script>
  {% endif %}
  ```

3. Add the Tipue Search search form, results display and script to your site. Use the example search page `search.html` for reference. Set `tipue_search_active: true` in the front-matter of every page or layout where you want to display search results. See the Tipue Search documentation for configuration of the [search form](http://www.tipue.com/search/docs/?d=1) and [display of search results](http://www.tipue.com/search/docs/?d=3):

  ```
  <form action="{{ page.url | relative_url }}">
    <div class="tipue_search_left"><img src="{{ "/assets/tipuesearch/search.png" | relative_url }}" class="tipue_search_icon"></div>
    <div class="tipue_search_right"><input type="text" name="q" id="tipue_search_input" pattern=".{3,}" title="At least 3 characters" required></div>
    <div style="clear: both;"></div>
  </form>

  <div id="tipue_search_content"></div>

  <script>
  $(document).ready(function() {
    $('#tipue_search_input').tipuesearch();
  });
  </script>
  ```

## Usage

Refer to the [Tipue Search documentation](http://www.tipue.com/search/docs/) and [browse the code](https://github.com/Tipue/Tipue-Search) to understand how Tipue Search works, and how to best integrate it into your site.

### Including pages and collections

By default, only posts are included in the search index. Pages and collections are not included.

Add the following to `_config.yml` to include pages and collections. `collections` is an array containing a list of collections you want to include.

```
tipue_search:
  include:
    pages: true
    collections: [apples, oranges]
```

### Excluding from search index

Exclude single documents from the search index with a front-matter variable:

```
exclude_from_search: true
```

Exclude multiple files, tags or categories using a setting in `_config.yml`. `files` is an array containing a list of file paths to be excluded. `tags` and `categories` are arrays containing lists of tags and categories you want to exclude.

```
tipue_search:
  exclude:
    files: [search.html, _apples/gragg.md, _oranges/valencia.md]
    tags: [tag1, tag2]
    categories: [category1, category2]
```
