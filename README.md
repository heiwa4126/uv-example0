# uv-example0

uv の練習。

[uv の GitHub の Features](https://github.com/astral-sh/uv?tab=readme-ov-file#features)
にあるやつに、
タスクランナーとして[poethepoet](https://pypi.org/project/poethepoet/)
と、
フォーマッター兼リンターとして[ruff](https://pypi.org/project/ruff/)
を足したところ。

PyPI に出すところまでやってみる。

## 最初の手順

```sh
uv init uv-example0
cd uv-example0
uv add --dev ruff poethepoet
code .
```

で、terminal 開くと venv 下にいるので、`pyproject.toml`に

```toml
[tool.poe.tasks]
check = "uv run ruff check"
format = "uv run ruff format"
```

を追加して、`poe format` とか実行してみる。

### 議論するべき点

poethepoet のタスクは、venv 下にあるものとして書くべきなのか。
それとも venv 下になくても動くように書くべきか。
(たぶん後者)
