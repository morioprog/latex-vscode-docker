# latex-vscode-docker

[VS Code Remote Development](https://code.visualstudio.com/docs/remote/remote-overview)上の LaTeX 環境．

## 使い方

1. VS Code の拡張機能[Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)をインストール
1. リポジトリを clone し，それを VS Code で開く
1. 右下に通知が表示されるので，`Reopen in Container`を選択
   - コマンドパレットからでも開ける
1. 開かれたディレクトリ(`/root/workdir`)が，このリポジトリ直下の`workdir`ディレクトリとリンクしています

## Git の設定

`~/.ssh`と`~/.gitconfig`をマウントしているので，そこに設定されていれば動作するはずです．
