# KobitoKey_QWERTY

分割型キーボード KobitoKey (QWERTY 配列 / 記号は日本語 JIS) の keymap 定義。

物理配置は左右各 4 段 × 5 列、合計 40 キー。キー位置番号は左手上段の Q が `0`、右手下段の RCtrl が `39` (左→右、上→下)。

## レイヤー一覧

| # | ラベル | 呼び出し | 用途 |
|---|---|---|---|
| 0 | DEFAULT | 起動時 | 通常入力 |
| 1 | FUNCTION | 左手親指 Space (位置 33) ホールド | 記号 |
| 2 | NUMBER | 左手親指 Space (位置 32) ホールド | 数字・F キー・括弧マクロ |
| 3 | MOVE | 右手親指 BS (位置 37) ホールド | カーソル / ページ移動 |
| 4 | BLUETOOTH | 左手 LWin (位置 31) ホールド | BT ペアリング / bootloader |
| 5 | MOUSE | 右トラックボール操作で自動発動 | マウスクリック / 修飾キー |

## 凡例

- `▽` = 下位レイヤーに透過 (`&trans`)
- `─` = キー無効 (`&none`)
- 2段表記のセル: 上段=タップ / 下段=ホールド (例: `Space` / `(L1)`)
- `MB1..MB5` = マウスボタン (左 / 右 / 中 / 戻る / 進む)
- `→ L0` = `&to 0` (Layer 0 に明示遷移)
- 表中央の `│` は左右手の境界 (左 5 列 / 右 5 列)

---

## Layer 0 — DEFAULT

| | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|
| Q | W | E | R | T | │ | Y | U | I | O | P |
| A | S | D | F | G | │ | H | J | K | L | - |
| Z | X | C | V | B | │ | N | M | , | . | @<br>RShift |
| LCtrl | LWin<br>(L4) | Space<br>(L2) | Space<br>(L1) | MB1 | │ | MB2 | Enter<br>RShift | BS<br>(L3) | RAlt | RCtrl |

---

## Layer 1 — FUNCTION (記号)

| | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|
| ! | " | # | $ | % | │ | ( | ) | < | > | ~ |
| & | ' | - | = | _ | │ | { | } | ; | : | \| |
| ^ | ` | + | * | ? | │ | [ | ] | / | \\ | @ |
| ▽ | ▽ | ▽ | ▽ | ▽ | │ | ▽ | ▽ | ▽ | ▽ | ▽ |

---

## Layer 2 — NUMBER (数字・F キー・括弧マクロ)

| | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2 | 3 | 4 | 5 | │ | 6 | 7 | 8 | 9 | 0 |
| ─ | F2 | ─ | ─ | F5 | │ | ─ | F7 | F8 | ─ | F12 |
| ─ | ─ | ─ | ─ | ─ | │ | ─ | `[]←` | `()←` | ─ | ─ |
| ▽ | ▽ | ▽ | ▽ | ▽ | │ | ▽ | ▽ | ▽ | ▽ | ▽ |

`[]←` / `()←` はマクロ (下記 Macros セクション参照)。

---

## Layer 3 — MOVE (カーソル / ページ移動)

| | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|
| Esc | Ctrl+Shift+Tab | Shift+Ctrl+PgUp | ─ | ─ | │ | ─ | Home | ↑ | End | BS |
| BS | Shift+Tab | PgDn | Tab | ─ | │ | MB4 | ← | ↓ | → | MB5 |
| Ins | ─ | LAlt | ─ | ─ | │ | ─ | Ctrl+Home | LAlt | Ctrl+End | ▽ |
| ▽ | ▽ | ▽ | ▽ | ▽ | │ | ▽ | ▽ | ▽ | ▽ | ▽ |

---

## Layer 4 — BLUETOOTH

| | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|
| BT 0 | BT 1 | BT 2 | BT 3 | BT 4 | │ | ─ | ─ | ─ | ─ | ─ |
| ─ | ─ | ─ | ─ | bootloader | │ | ─ | ─ | ─ | ─ | ─ |
| ─ | ─ | ─ | ─ | ─ | │ | ─ | ─ | ─ | ─ | ─ |
| BT CLR | BT CLR ALL | ─ | ─ | ─ | │ | ─ | ─ | ─ | ─ | ─ |

- `BT 0..4` = `&bt BT_SEL 0..4` (プロファイル選択)
- `BT CLR` = 現プロファイルのペアリング消去
- `BT CLR ALL` = 全ペアリング消去

---

## Layer 5 — MOUSE (Auto Mouse Layer)

| | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|
| ▽ | ▽ | ▽ | ▽ | ▽ | │ | ▽ | MB1 | MB3 | MB2 | ▽ |
| ▽ | ▽ | ▽ | ▽ | ▽ | │ | ▽ | ▽ | ▽ | ▽ | ▽ |
| ▽ | ▽ | ▽ | ▽ | ▽ | │ | ▽ | ▽ | ▽ | ▽ | ▽ |
| LShift | ▽ | LCmd | LShift | LAlt | │ | ▽ | ▽ | ▽ | → L0 | RAlt |

---

## Combos

同時押しで発動 (timeout 50ms)。

| キー位置 | 物理キー (Layer 0) | 発動 | 用途 |
|---|---|---|---|
| 0 + 1 | Q + W | Esc | Escape |
| 10 + 11 | A + S | Tab | Tab |
| 12 + 13 | D + F | LANG2 | 英数 (JIS) |
| 16 + 17 | J + K | LANG1 | かな (JIS) |
| 8 + 9 | O + P | Win+Shift+S | 範囲スクショ |

---

## Macros

| 名前 | 呼び出し位置 | 動作 |
|---|---|---|
| `m_kakko` | Layer 2 右手 R2 C2 | `[` → `]` → `←` |
| `m_paren` | Layer 2 右手 R2 C3 | `(` → `)` → `←` |

括弧を入力してカーソルを内側に戻す。

---

## Auto Mouse Layer

右トラックボールを操作すると自動で Layer 5 (MOUSE) に切り替わる。ZMK の `zip_temp_layer` (input-processor-temp-layer) で実装。

定義ファイル: `config/boards/shields/KobitoKey/KobitoKey_left.overlay`

### 設定値

| 項目 | 値 | 意味 |
|---|---|---|
| 対象レイヤー | 5 (MOUSE) | 切り替え先 |
| 滞留時間 | 5000ms | 最後の入力から Layer 5 が維持される時間 |
| 発動アイドル | 350ms | 直前のキー押下からこの時間経過するまで Layer 5 に入らない (誤爆防止) |

### 切り替わる条件

- 右トラックボールを動かす
- ただし直前のキー押下から 350ms 以内は発動しない

### 抜ける条件

1. 最後のトラボ入力 / マウスボタン押下から 5000ms 経過
2. **excluded-positions 以外**のキーを押した瞬間に解除

### excluded-positions (押しても Layer 5 を抜けないキー)

マウスクリック / 修飾キーが連続入力されても Layer 5 が切れないようにするための除外リスト。

| 位置 | Layer 5 上のキー |
|---|---|
| 12 | MB1 (左手 R1 C2) |
| 13 | MB2 (左手 R1 C3) |
| 30 | スクリーンショット LG(LS(S)) (左手 R3 C0) |
| 33 | MB1 (左手 R3 C3) |
| 34 | MB2 (左手 R3 C4) |

### 設定を変えたいときの箇所

| 目的 | 変更箇所 |
|---|---|
| 滞留時間 | overlay の `<&zip_temp_layer 5 5000>` の第 2 引数 |
| 発動アイドル | `zip_temp_layer` ノードの `require-prior-idle-ms` |
| excluded 対象 | `&zip_temp_layer { excluded-positions = <...>; };` |
| 対象レイヤー変更 | `<&zip_temp_layer 5 5000>` の第 1 引数 |

---

## LED 表示 (電池状態)

Xiao BLE 内蔵の RGB LED を `caksoylar/zmk-rgbled-widget` で制御。**左 (central) 側のみ**有効で、表示するのは**左側自身の電池残量**のみ (右側の電池は右自身の LED では表示しない)。

定義ファイル: `config/boards/shields/KobitoKey/KobitoKey_left.conf`

### 発動タイミング

- 起動時に一度ブリンク
- 電池残量が閾値を跨いだ時にブリンク
- 残量が CRITICAL 以下の間は定期的にブリンク

### 閾値 & 色

| 残量 | 色 | 表示 |
|---|---|---|
| 60 % 以上 | 🟢 緑 | 起動時 / 変化時にブリンク |
| 30 – 60 % | 🟡 黄 | 起動時 / 変化時にブリンク |
| 10 – 30 % | 🔴 赤 | 起動時 / 変化時にブリンク |
| 10 % 未満 | 🔴 赤 | 定期ブリンク |
| 電池未検出 | 🟣 マゼンタ | ブリンク |

閾値は `CONFIG_RGBLED_WIDGET_BATTERY_LEVEL_HIGH=60` / `LOW=30` / `CRITICAL=10`。色はデフォルト値のまま (widget 既定)。

### 設定を変えたいときの箇所

| 目的 | 変更箇所 (`KobitoKey_left.conf`) |
|---|---|
| 電池閾値 | `CONFIG_RGBLED_WIDGET_BATTERY_LEVEL_HIGH` / `LOW` / `CRITICAL` |
| 電池色 | `CONFIG_RGBLED_WIDGET_BATTERY_COLOR_HIGH` / `MEDIUM` / `LOW` / `CRITICAL` / `MISSING` |
| 右側の電池も表示 | `CONFIG_RGBLED_WIDGET_BATTERY_SHOW_PERIPHERALS=y` |
| ブリンク間隔 | `CONFIG_RGBLED_WIDGET_INTERVAL_MS` |
