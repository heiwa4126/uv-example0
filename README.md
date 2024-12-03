# uv-example0

uv の練習。

[uv の GitHub の Features](https://github.com/astral-sh/uv?tab=readme-ov-file#features)
にあるやつに、
タスクランナーとして[poethepoet](https://pypi.org/project/poethepoet/)
と、
フォーマッター兼リンターとして[ruff](https://pypi.org/project/ruff/)
を足したところ。

PyPI に出すところまでやってみる。

## uvのインストール

1. [Installation | uv](https://docs.astral.sh/uv/getting-started/installation/#__tabbed_1_2)
2. インストール後、パスを通すなど指示に従う。
3. `uv tool install poethepoet` PoeThePoet だけはユーザ単位でインストールしておく。
   時々 `uv tool upgrade --all` で更新する。

## プロジェクトを作る手順

```sh
uv init uv-example0
cd uv-example0
uv add --dev ruff
code .
```

で、terminal 開くと venv 下にいるので、`pyproject.toml`に

```toml
[tool.poe.tasks]
check = "ruff check"
format = "ruff format"
```

を追加して、`poe format` とか実行してみる。

※ poe は ./.venv を見る。参照: [Change the executor type](https://poethepoet.natn.io/global_options.html#change-the-executor-type)
