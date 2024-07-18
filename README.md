# age-calculation

年齢計算のプログラム

- ユーザーは生まれた年は数値を入力
- 生まれた月と日はセレクトボックスで選択
- 上記を入力すると、現在の年齢と次の誕生日まであと何ヶ月か分かる

## 解決した点

- 次の誕生日まであと何ヶ月あるかの計算ができるようになった
- 誕生日が来る前は‐1 歳になるようにした

## デプロイ

- gh-pages をインストールしてみた → デプロイ自体はできたっぽいけど真っ白
- vite.config.js に base を追加してみた

## 参考

parseInt()関数 https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/parseInt
