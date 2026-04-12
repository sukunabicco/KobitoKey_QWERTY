# KobitoKey D7ピン診断 TODO

## 現在の状況 (2026-04-12)
- 左手側の R/F/V/LCTRL（Col4 = D7列）が反応しない
- D7 GPIO自体は正常（tester_xiaoで確認済み）
- D7パッドのはんだは良好（追いはんだ済み）
- → PCB配線の断線が疑われる
- kscanログ版ファームをプッシュ済み（`2de59f4`）、GitHub Actionsビルド待ち

## 次のアクション
- [ ] GitHub Actionsのビルド完了を確認
- [ ] Artifactsからダウンロード
  - [ ] `KobitoKey_left-seeeduino_xiao_ble-zmk.uf2`（ログ版）
  - [ ] `settings_reset-seeeduino_xiao_ble-zmk.uf2`（復旧用・PCに保管）
- [ ] ログ版uf2を左XIAOに書き込み
- [ ] PuTTYでCOMポート接続（115200 baud）
- [ ] kscanログで切り分け
  - [ ] 正常キー（E）を押す → ログ出力を確認
  - [ ] 問題キー（R）を押す → ログが出るか確認

## 結果別の次ステップ
- **Rでログなし** → PCB配線断線 → テスターで導通確認 → ジャンパワイヤ修理
- **Rでログあり** → ファームウェア側の問題 → 設定見直し

## リセットループした場合の復旧
1. BOOTパッド押しながらUSB接続（またはリセット2回タップ）
2. settings_reset.uf2を書き込み
3. USBルートハブの電源管理を無効化（デバイスマネージャー）
4. 再度ブートローダーモード → 通常ファームを書き込み

## デバッグ完了後の復元
- [ ] build.yaml: `zmk-usb-logging` → `studio-rpc-usb-uart` に戻す
- [ ] KobitoKey_left.conf: デバッグ行削除、Studio有効に戻す
- [ ] コミット＆プッシュ → 通常ファームを再ビルド
