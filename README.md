# chatux-server-llm

ローカル環境で動作する文章生成 AI チャットボットです。
CPU だけで動作します。（NVIDIA のグラボは不要）

# 最低要件

- 第 8 世代以降の Corei 3
- メインメモリ 8G バイト
- ストレージ 10G バイト（SSD を強く推奨）
- OS: Linux/Windows11 で動作を確認しています。
- その他: Linux 用の簡易インストーラ/サーバー起動用のスクリプトあり

# インストール手順（Linux 版）

任意のディレクトリで、付属の簡易インストーラスクリプトを実行してください。

```
bash ./install_linux.sh
```

# インストール手順（Windows 版）

本サイトからなんらかの方法で環境一式をダウンロードし、任意のフォルダに配置したのち、PowerShell から次のコマンドを実行してください。

```
python3 -m venv venv
venv/Scripts/activate
pip3 install -r requirements.txt
ct2-transformers-converter --model line-corporation/japanese-large-lm-3.6b-instruction-sft --low_cpu_mem_usage --output_dir line-sft --quantization int8 --force

python ct2-main.py
```

# 実行時の注意

初回実行時のみ、インターネットから大量のダウンロードが発生するため、しばらくお待ちください。
エラーがなければ AI サーバーが起動しますので、
ブラウザから次の URL を開いてください。

```
http://127.0.0.1:8001/
```

次のような画面が表示されれば起動成功です。お楽しみください。

![Alt text](img/img01.png)

次の画像をクリックすると youtube で応答速度を確認できます。

[![応答イメージ](img/img02.png)](https://youtu.be/h3-edtm-NLQ)

# TIPS

- メモリ不足で言語モデル変換できない方は
  [huggingface](https://huggingface.co/sehiro/LINE-ct2-jp)
  から変換済のモデルをダウンロードしてください。
  もっともメモリを使う「ct2-transformers-converter」コマンドの実行をスキップできます。

- つよつよ CPU をお持ちの方は次のオプションを追加すると、AI エンジンがより高速に動作する可能性があります。（副作用として若干メインメモリの消費量が増えます）

```
python ct2-main.py --maxspeed ON
```

## 開発版

本当はブランチを切るのが正当な手法なのでしょうが、
開発版のコードもこちらで一時的に公開しておきます。
AI エンジンを llama.cpp に差し替えることで
主に Llama 系言語モデルの高速化を狙っています。

ただインストールに C コンパイルが必要等、
初心者にはかなりインストールのハードルが高いと思われるため、
現状はソースを読んで理解できる方だけお使い頂けると…。

- https://huggingface.co/mmnga/ELYZA-japanese-Llama-2-7b-fast-instruct-gguf
からggufファイルをダウンロードして「models」フォルダに配置してください。

- コマンドプロンプト等から次のコマンドを入力してください

```
pip install -r requirements-cpp.txt
python3 cpp-main.py
```

## ToDo

- Windows 版インストーラの開発
- 各種パラメータの微調整
- 設定ファイルのサポート
- LoRA のサポート

# ライセンス

MIT
