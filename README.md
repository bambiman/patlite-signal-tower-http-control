# PATLITE Signal Tower HTTP Control

Home Assistant script blueprint for controlling PATLITE signal towers over HTTP.

PATLITE NHシリーズなどのシグナルタワーをHome AssistantからHTTP制御するためのスクリプトBlueprintです。

---

# Features / 特徴

- LED control / LED制御
- Blink patterns / 点滅パターン
- Buzzer patterns / ブザーパターン
- Automatic buzzer stop / ブザー自動停止
- Automatic alarm clear / 自動アラーム解除
- GUI selectors inside Home Assistant / Home Assistant GUI対応
- HTTP based / HTTPベース
- No additional integrations required / 追加Integration不要

---

# Supported Devices / 対応機種

- PATLITE NH Series

---

# Required Configuration / 必要な設定

Add the following to your `configuration.yaml`.

以下を `configuration.yaml` に追加してください。

```yaml
rest_command:
  patlite_http_control:
    url: "http://{{ ip }}/api/control?{{ command }}={{ value }}"
    method: GET
```

Example:

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

After adding it, restart Home Assistant.

追加後、Home Assistantを再起動してください。

---

# Installation / インストール

Import Blueprint URL:

```text
https://raw.githubusercontent.com/bambiman/patlite-signal-tower-http-control/main/blueprints/script/bambiman/patlite_control.yaml
```

Home Assistant:

```text
Settings
→ Automations & Scenes
→ Blueprints
→ Import Blueprint
```

Home Assistant 日本語UI:

```text
設定
→ オートメーションとシーン
→ ブループリント
→ ブループリントをインポート
```

---

# Usage / 使い方

1. Import the blueprint
2. Create a script from the blueprint
3. Use the created script inside your automations

1. Blueprintをインポート
2. Blueprintからスクリプトを作成
3. 作成したスクリプトをオートメーションから呼び出します

Example:

```yaml
actions:
  - action: script.patlite_signal_tower_http_control001
```

---

# Available Patterns / 使用可能パターン

## LED

| Value | Description |
|---|---|
| 0 | Off |
| 1 | Solid |
| 2 | Blink 1 |
| 3 | Blink 2 |
| 9 | No Change |

## Buzzer

| Value | Description |
|---|---|
| 0 | Off |
| 1 | Pattern 1 |
| 2 | Pattern 2 |
| 3 | Pattern 3 |
| 4 | Pattern 4 |
| 9 | No Change |

---

# Automatic Actions / 自動動作

## Automatic Buzzer Stop / ブザー自動停止

Stops only the buzzer after the specified seconds while keeping LED states unchanged.

指定秒数後にブザーのみ停止し、LED状態は維持します。

Uses:

```text
alert=999990
```

---

## Automatic Alarm Clear / 自動アラーム解除

Clears all LEDs and buzzer after the specified seconds.

指定秒数後にLEDとブザーをすべて解除します。

Uses:

```text
clear=1
```

---

# Example Use Cases / 使用例

- Red flashing + buzzer
- UPS alerts
- Frigate notifications
- Server monitoring
- Door open alerts
- Rack temperature alerts
- Network outage alerts

---

# Notes / 注意事項

This blueprint uses the PATLITE HTTP API.

このBlueprintはPATLITE HTTP APIを利用しています。

PATLITE側でHTTP制御を有効化してください。

---

# License

MIT License
