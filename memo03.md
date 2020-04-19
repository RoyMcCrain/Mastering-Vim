# 遅いプラグインをプロファイリングする

`--startuptime <ファイル名>`で vim を起動するとログを吐ける。

```vim
157.438  000.269  000.269: sourcing /usr/local/Cellar/neovim/HEAD-251b20e/share/nvim/runtime/plugin/tarPlugin.vim
157.784  000.245  000.245: sourcing /usr/local/Cellar/neovim/HEAD-251b20e/share/nvim/runtime/plugin/tohtml.vim
157.976  000.107  000.107: sourcing /usr/local/Cellar/neovim/HEAD-251b20e/share/nvim/runtime/plugin/tutor.vim
158.358  000.270  000.270: sourcing /usr/local/Cellar/neovim/HEAD-251b20e/share/nvim/runtime/plugin/zipPlugin.vim
```

3 カラムあるうちの右側が起動でかかった時間（真ん中も同じ？）

000.269 ミリ秒とかかかっているが 500.000 ミリ秒超えると起動の遅さに気づくらしい。

# 特定のアクションをプロファイリングする

```bash
:profile start profile.log
:profile func *
:profile file *
```

これでログが出せる
`set foldmethod=indent` して `zM` すると見やすい

カーソル合わせて`*`で検索

# コマンドを再マッピングする

`:map` 再帰的なマッピングに用いられる(他のカスタムマッピングに影響する)
`:noremap` 非再帰的なマッピングに用いられる(デフォルトマッピングのみ影響する)

`:map`は主にプラグインの提供するカスタムマッピングに対して使う
`:noremap`は主に組み込みマッピングに対して使う

## 使用可能な特殊文字

- <space> : スペースキー
- <esc> : ESC キー
- <cr>, <enter> : エンターキー
- <tab> : タブキー
- <bs> : バックスペースキー
- <up>, <down>, <left>, <right> : 矢印キー
- <pageup>, <pagedown>, : Page Up と Page Down
- <f1>, ~ , <f12> : ファンクションキー
- <home>, <insert>, <del>, <end>, : Home, Insert, Delete, end キー

あるキーバインドに何もしてほしくない場合は、`<nop>` No Operation

# マッピングの確認

`:map`
`:map g` g から始まるマッピングを表示

# Leader キー

default はバックスラッシュ(\)だがカンマ(,)に置き換えが一番人気らしい。
私はスペースを利用するので下記のように設定する。
`let mapleader = "\<space>"`
得所文字の前にバックスラッシュ必須。シングルクォートではなくダブルクォート

# Vim のグローバル変数

大抵、`g:`が先頭に来る
