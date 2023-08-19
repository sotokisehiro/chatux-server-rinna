# chatux-server-llm

ローカル環境で動作する文章生成 AI チャットボットです。
CPU だけで動作します。（NVIDA のグラボは不要）

# 要件

- 第 8 世代以降の Corei 3
- メインメモリ 8G バイト
- ストレージ 10G バイト（SSD を強く推奨）
- OS: Linux/Windows11 で動作を確認しています。
- その他: Linux 用の簡易インストーラ/サーバー起動用のスクリプトあり

# インストール手順（Linux 版）

付属の簡易インストーラスクリプトを実行してください。

```
bash ./install_linux.sh
```

インターネットから大量のダウンロードが発生するため、しばらくお待ちください。
エラーがなければ AI サーバーが起動しますので、
ブラウザから次の URL を開いてください。

```
http://127.0.0.1:8001/
```

次のような画面が表示されれば起動成功です。お楽しみください。

![Alt text](img/img01.png)

## ToDo

- Windows 版インストーラの開発
- LoRA のサポート

# ライセンス

MIT
