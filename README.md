# tumbler.documents

[![Apache License](http://img.shields.io/badge/license-APACHE2-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0)

Brief tutorials for tumbler

## スタートアップガイド

### 1. はじめに

#### 1.1. 環境

Fairy I/O Tumbler は Raspberry Pi Compute Module を搭載し、Raspbian Stretch がインストールされています。納品書類に従って Wi-Fi 接続を完了し、Raspbian Stretch に ssh で外部からログインできることを前提とします。

#### 1.2 ハードウェアバージョンの確認

お持ちの Fairy I/O Tumbler のバージョンと同梱品を確認してください。先行出荷ロットの場合、プリインストールされているライブラリが古くなっている場合がありますので、このドキュメントに従ってライブラリ群を更新してください。

### 2. ライブラリ構成

libmimixfe

mimi(R) XFE の機能が実装されたライブラリです。Tumbler は 16 個のマイクから、最大 48kHz, 16bit, 16ch、1ch のスピーカーフィードバック信号、1ch の外部入力信号の合計 18ch の同期信号を取得することができます。この同期信号を利用し、ビームフォーミングや、エコーキャンセル、発話区間抽出などの前段信号処理を行うためのライブラリが libmimixfe です。

libmimixfe は、Tumbler のハードウェア層からの信号を入力とし、設定に従った信号処理済の音声データが出力されます。この音声データを mimi(R) クラウドへ送信することで、音声認識などの結果を得ることができます。この信号処理済の音声を、mimi(R) クラウドではなく、サードパーティサービスに送信するプログラムを開発することで、サードパーティサービスを利用したシステムを構築することも可能です。

libmimixfe はバイナリライブラリの形式で提供されます。利用時には、他のライブラリが必要となりますので、libmimixfe のドキュメントを参照してください。

libmimiio

libmimiio は mimi(R) WebSocket API Service を実装したクライアント通信ライブラリで、音声データを入力とし、mimi(R) クラウドに音声データを送信し、音声認識などの結果を得ることができるライブラリです。WebSocket による双方向通信を利用することで、リアルタイムの音声データの送信と結果の受信が可能となります。

libmimixfe はオープンソースとして提供されます。ビルド時には、Poco C++ library などが必要となります。Poco はプレビルドバイナリが github 上で公開されているので、そちらを参照してください。



