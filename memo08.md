# Vim Script

VimScript の変数や関数のスコープはプレフィックスで判断する

- g: グローバルスコープ(default)
- v: Vim によって定義されたグローバルスコープ
- l: 関数ローカルスコープ(関数内の default)
- b: バッファローカル
- w: ウインドウローカル
- t: タブローカル
- s: :source された Vim script に対してローカル
- a: 関数の引数

Vim のオプション(set で変更するもの)には`&`をつけることでアクセスできる。
`let &ignorecase = 0`

ドット演算子で文字結合が可能
`let g:cat_statement = g:animal_name . 'is a cat'`

出力は`echo`を使う

出力を記録する場合は`:echomsg or :echom`を使う
`echom g:animal_name . 'is an animal'`
`echom 'here is an another message'`

上記のコマンドをしたあと、`:messages`で見れる

```vim
function! IsProperName(name)
  if a:name =~? '\(Mr\|Miss\) .\+'
    return 1
  endif
  return 0
endfunction

let animal_names = {
  \ 'cat': 'Miss Cattington',
  \ 'dog': 'Mr Dogson',
  \ 'parrot': 'Polly'
  \ }

call filter(animal_names, 'IsProperName(v:val)')

echo animal_names
```

`v:val`で辞書のバリューに展開される。
`v:key`ならキーに展開される。

Vim script 難しいから見直す。

ローカルのプラグイン置き場がわからなかった(neovim)

`~/.vim/ => ~/.config/nvim` らしいです。
