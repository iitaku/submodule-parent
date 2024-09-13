# submodule-parent

以下のようなサブモジュールを含むレポジトリを例に git submodule の使い方についてかく。
```
submodule-parent/
├── README.md
└── child (https://github.com/iitaku/submodule-child.git のサブモジュール)
    └── README.md
```

## How to

submodule-child を submodule-parent にサブモジュールとしてルートディレクトリに child という名前で追加する

```
git submodule add https://github.com/iitaku/submodule-child.git child
```

submodule-parent を clone してサブモジュールを適切な状態に初期化する
```
git clone https://github.com/iitaku/submodule-parent.git
git submodule update --init --recursive
```

submodule-parent の最新のmainブランチをpullしてサブモジュールも最新の状態にする
```
git pull origin main
git submodule update
```

サブモジュールの子側の変更を親側に取り込む
```
cd child
<なにか変更する>
git add .
git commit -m "Updated"
git push origin main # <-- submodule-child の push
cd ..
git add child
git commit -m "Updated child"
git push origin main # <-- submodule-parent の push
```
