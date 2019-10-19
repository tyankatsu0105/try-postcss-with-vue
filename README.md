# try-postcss-with-vue

https://github.com/postcss/postcss-dark-theme-class
のテスト

```scss
:root {
  --text-color: black;
  --background-color: white;
}

@media (prefers-color-scheme: dark) {
  :root {
    --text-color: white;
    --background-color: black;
  }
}

p{
  color: var(--text-color);
}
body {
  background: var(--background-color);
}
```

# 仕組み
- prefers-color-schemeを全ブラウザに対応させるためのpolifyll的な感じ
- postcssプラグインを適用する際にオプションに渡したクラスが自動で付与される。
デフォルトはこんな感じ
```js
module.exports = {
  plugins: {
    'postcss-dark-theme-class': {
      darkClass: 'is-dark', //ダークモード時 クラス名は自由に変えられるよ
      lightClass: 'is-light' //ライトモード時 クラス名は自由に変えられるよ
    },
  },
};

```
- そのため、htmlにクラスを付与させる必要がある
- このプラグインを使うと、 `p.is-dark {}`とか書かなくて済むようになり、prefers-color-schemeメディアクエリをまるで全ブラウザでもいけるように書ける

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

# 参照
- https://developer.mozilla.org/ja/docs/Web/CSS/@media/prefers-color-scheme
- https://blog.jxck.io/entries/2018-11-10/dark-mode-via-prefers-color-scheme.html