# Git と Vim を統合する(vim-fugitive)

vim-fugitive の説明

:Gstatus

- `-` はファイルからステージング領域に移動、もしくはステージング領域から削除する
- `cc or :Gcommit` でステージング領域のファイルをコミットする
- `D or :GDiff` で差分を開く
- `g?`でヘルプ表示

# vimdiff を使う

`neovim -d` で neovim で vimdiff 使える

`do or :diffget` do は(diff obtain) 差分をアクティブなウインドウに移動する。違いを取り込む
`dp or :diffput` dp は(diff put) 差分をアクティブなウインドウからプッシュする

全体適応版
`:%diffget`
`:%diffput`

`git mergetool` の見方

上 3 つのウインドウに下ウインドウ
左から
ローカル、共通の base-branch、マージ元

- LOCAL
- BASE
- REMOTE
- MERGED

- `:diffg R` REMOTE の短縮形
- `:diffg B` BASE の短縮形
- `:diffg L` LOCAL の短縮形

上記のショートカット設定しよう

tmux をうまく使いこなしたいなぁ
