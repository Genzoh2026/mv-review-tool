# MV Review Tool

動画を見ながら「ここを直したい」を時刻・位置つきで書き留める、単体 HTML のレビューツールです。
動画はブラウザ内で再生するだけで、どこにもアップロードされません。依存・ビルドはありません。

A single-file HTML tool for leaving timestamped, positioned revision notes on a video.
Videos stay in your browser; nothing is uploaded.

## 使い方 / Usage

1. `index.html` をブラウザで開く(GitHub Pages の URL でも可)
2. 「動画」で動画ファイルを選ぶ
3. 動画上をクリック → その時刻・位置にマークを追加し、右のコメント欄に指示を書く。位置を指さない指示は「全体コメントを追加」
4. 「Markdown をコピー」「JSON 保存」「MD 保存」で書き出す

指示はブラウザの localStorage に動画ファイル名ごとに自動保存されます。

| 操作 | キー |
|---|---|
| 再生 / 一時停止 | Space |
| 1コマ戻る / 進む | ← / → |
| 1秒戻る / 進む | Shift+← / Shift+→ |

FPS は自動判定されません。動画に合わせて上部の欄で設定してください(既定 24)。コマ送りとフレーム番号に使われます。

## カット表 CSV(任意)

読み込むと、タイムラインにカットの境目が出て、各指示にカット番号とラベルが付きます。
ヘッダー行つきの UTF-8 CSV で、`no`, `start_s`, `end_s` が必須、`section`, `label`, `lyric_or_note` は任意です。
例: [`examples/cuts.csv`](examples/cuts.csv)

## 注意

- localStorage はブラウザ・端末ごとです。別の端末へは JSON / MD で書き出してください
- 動画の再生可否はブラウザが対応するコーデック(H.264/AAC の MP4 など)に依存します
- 動作確認は Chrome のみです。Firefox・Safari では未確認です
- 書き出した指示書を AI エージェントなど外部のサービスに貼ると、その内容は相手に渡ります。未公開の情報を書いた場合は、貼り付け先を確認してください(このツール自体は何も送信しません)
- 個人の試作ツールで、無保証です(MIT)。要望や不具合への対応は約束できません

## License

MIT
