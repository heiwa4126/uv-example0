# uv-example0

uv をパッケージマネージャとして使う練習。

[uv の GitHub の Features](https://github.com/astral-sh/uv?tab=readme-ov-file#features)
にあるやつに、

- タスクランナーとして[PoeThePoet](https://pypi.org/project/poethepoet/) - .venv の下
- フォーマッター兼リンターとして[ruff](https://pypi.org/project/ruff/) - `uv tool install`で

を足したところ。PyPI に出すところまでやってみる予定

## uv のインストール

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
hello = "uv run hello.py"
check = "ruff check"
format = "ruff format"
```

を追加して、`poe format` とか実行してみる。

※ poe は ./.venv を見る。上の `check` と `format` は .venv の下の ruff。
参照: [Change the executor type](https://poethepoet.natn.io/global_options.html#change-the-executor-type)

## プロジェクトをクローンして始める

```sh
git clone xxxx && cd xxxx
uv sync  # または `uv sync --lock`
poe hello
```
