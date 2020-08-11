# Hexo Theme Unit Test

This is a dummy Hexo site for theme unit test. You should test your theme before release.

This test doesn't contain the default theme. You have to install the theme you want to test before starting.

## Usage

1. Clone this repository

    ``` bash
    $ git clone https://github.com/hexojs/hexo-theme-unit-test.git
    ```

2. Install your own theme and modify `theme` setting in `_config.yml`.
3. Run server and start testing. Make sure all styles  are displayed properly.
4. Once test is done, you can [submit your theme](https://hexo.io/docs/themes.html#Publishing)!

## Checklist

### `<head>`

- Use the proper [DOCTYPE](https://en.wikipedia.org/wiki/Document_Type_Declaration).
  If you don't know which doctype you should use, `<!DOCTYPE html>` is recommended.
- UTF8 charset

    ``` html
    <meta charset="utf-8">
    ```

- Proper titles for different pages
- Favicon support

    ``` html
    <link rel="icon" href="path/of/favicon">
    ```

### Index

- Only display excerpts. (Better with a "Read More" link)
- [Pagination](https://hexo.io/docs/configuration.html#Pagination)

### Post

- Display post categories and tags.
- Disqus comment support.
- Display the post date.
- Support `photo` and `link` layout.
- Posts without title should be accessible.

### Performance

- Use [fragment_cache](https://hexo.io/docs/helpers.html#fragment_cache)
  It caches render result across post/pages, see [#1769](https://github.com/hexojs/hexo/issues/1769) for the impact

### Optional

- Responsive design
- i18n
- Post share
- SEO
- RSS [Autodiscovery](http://www.rssboard.org/rss-autodiscovery) support
  * Example:
  ``` html
  <link rel="alternate" href="path/of/rss" type="application/atom+xml">
  ```
  * Some RSS plugins (e.g. [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed) 2.1+) insert autodiscovery by default. There is a slight performance benefit if a theme inserts it, instead of the plugin. To take advantage of that, autodiscovery needs to be disabled in the plugin.
    ``` yml
    feed:
      autodiscovery: false
    ```
  * hexo-generator-feed plugin could generate more than one type of RSS (e.g. Atom & RSS2). Here is an example EJS snippet for multi-format support by utilizing [`feed_tag`](https://hexo.io/docs/helpers#feed-tag) helper:
    ``` js
    <%- feed_tag() %>
    ```
    * If you want to support other plugins, in addition to hexo-generator-feed:
    ``` js
    <% if (config.feed) { %>
      <%- feed_tag() %>
    <% } else if (theme.rss) { %>
      <%- feed_tag(theme.rss) %>
    <% } %>
    ```
  * If you decide to support autodiscovery, we recommend checking the updates of [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed/releases) (or any other RSS plugin that your theme prefers) from time to time. The configuration and functionality of an RSS plugin may change over time.

## Resources

- [Theme](https://hexo.io/docs/themes.html)
- [Variables](https://hexo.io/docs/variables.html)
- [Helpers](https://hexo.io/docs/helpers.html)
