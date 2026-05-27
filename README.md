# PATLITE Signal Tower HTTP Control

Home Assistant script blueprint for controlling PATLITE signal towers over HTTP.

PATLITE NHシリーズなどのシグナルタワーをHome AssistantからHTTP制御するためのスクリプトBlueprintです。

---

# Features / 特徴

- LED control / LED制御
- Blink patterns / 点滅パターン
- Buzzer patterns / ブザーパターン
- Auto stop buzzer / ブザー自動停止
- GUI selectors inside Home Assistant / Home Assistant GUI対応
- HTTP based / HTTPベース
- No additional integrations required / 追加Integration不要

---

# Supported Devices / 対応機種

- PATLITE NH Series

---

# Installation / インストール

Import Blueprint URL:

```text
https://raw.githubusercontent.com/bambiman/patlite-signal-tower-http-control/main/blueprints/script/patlite/patlite_control.yaml
```

Home Assistant:

```text
Settings
→ Blueprints
→ Import Blueprint
```

Home Assistant 日本語UI:

```text
設定
→ ブループリント
→ ブループリントをインポート
```

---

# Example Use Cases / 使用例

- Red flashing + buzzer
- UPS alerts
- Frigate notifications
- Server monitoring
- Door open alerts

---

# Example Patterns / パターン例

| Pattern | Description |
|---|---|
| Red flashing + buzzer | 異常通知 |
| Yellow flashing | 注意通知 |
| Green solid | 正常状態 |
| Blue solid + buzzer | Frigate人物検知 |

---

# Notes / 注意事項

This blueprint uses PATLITE HTTP API.

このBlueprintはPATLITE HTTP APIを利用しています。

PATLITE NHシリーズのHTTPコマンド制御を有効化してください。

---

# License

MIT License
