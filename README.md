# PATLITE Signal Tower HTTP Control

PATLITE NHシリーズなどのシグナルタワーを、Home AssistantからHTTP制御するためのスクリプトBlueprintです。

---

# 主な機能

- LED制御
- 点滅パターン制御
- ブザーパターン制御
- ブザー自動停止
- アラーム自動解除
- Home Assistant GUI対応
- HTTPベース制御
- 追加Integration不要

---

# 対応機種

- PATLITE NH Series

---

# 必要な設定

`configuration.yaml` に以下を追加してください。

```yaml
rest_command:
  patlite_http_control:
    url: "http://{{ ip }}/api/control?{{ command }}={{ value }}"
    method: GET
```

設定例:

```yaml
default_config:

automation: !include automations.yaml
script: !include scripts.yaml
scene: !include scenes.yaml

rest_command:
  patlite_http_control:
    url: "http://{{ ip }}/api/control?{{ command }}={{ value }}"
    method: GET
```

追加後、Home Assistantを再起動してください。

---

# インストール

Blueprint Import URL:

```text
https://raw.githubusercontent.com/bambiman/patlite-signal-tower-http-control/main/blueprints/script/bambiman/patlite_control.yaml
```

Home Assistant:

```text
設定
→ オートメーションとシーン
→ ブループリント
→ ブループリントをインポート
```

---

# 使い方

1. Blueprintをインポート
2. Blueprintからスクリプトを作成
3. 作成したスクリプトをオートメーションから呼び出す

例:

```yaml
actions:
  - action: script.patlite_signal_tower_http_control001
```

---

# 使用可能パターン

## LED

| 値 | 動作 |
|---|---|
| 0 | 消灯 |
| 1 | 点灯 |
| 2 | 点滅1 |
| 3 | 点滅2 |
| 9 | 変化なし |

## ブザー

| 値 | 動作 |
|---|---|
| 0 | 停止 |
| 1 | パターン1 |
| 2 | パターン2 |
| 3 | パターン3 |
| 4 | パターン4 |
| 9 | 変化なし |

---

# 自動動作

## ブザー自動停止

指定秒数後にブザーのみ停止し、LED状態は維持します。

使用コマンド:

```text
alert=999990
```

---

## アラーム自動解除

指定秒数後にLEDとブザーをすべて解除します。

使用コマンド:

```text
clear=1
```

---

# 使用例

- 赤点滅 + ブザー
- UPS異常通知
- Frigate人物検知
- サーバ監視通知
- ドア開放通知
- ラック温度異常
- ネットワーク障害通知

---

# 注意事項

このBlueprintはPATLITE HTTP APIを利用しています。

PATLITE側でHTTP制御を有効化してください。

---

# ライセンス

MIT License
