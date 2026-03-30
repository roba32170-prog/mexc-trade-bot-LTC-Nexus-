# LTCNexus - Litecoin Intelligent Trading Dashboard

**高度なリアルタイム分析 + Strategy Editor搭載のLitecoin専用取引ダッシュボード**

![LTCNexus Banner](https://via.placeholder.com/1200x400/0A1F3A/00FFFF?text=LTCNEXUS)

## ✨ 主な特徴

- **1秒ごとの超高速リアルタイム更新**（価格・シグナル・指標）
- **Strategy Editor**によるノーコード戦略作成（JSONベース）
- **MPAndroidChart**による高精度で美しいチャート表示
- **BUY / SELLシグナル**の視覚的強調（緑・赤マーカー + ラベル）
- **RSI, ADX, EV, Quantum Signal**などの高度なテクニカル指標
- **タイムフレーム自由切替**（1m / 5m / 15m / 60m）
- **バックグラウンド最適化**でスムーズな動作

## 📱 スクリーンショット

（実際のスクリーンショットをここに挿入予定）

## 🚀 クイックスタート

### 1. Strategy Editorで戦略を作成

**Strategy Editor**を開き、以下のJSONを貼り付けて保存してください：

&&（AND）
||（OR）
<, >, <=, >=, ==

高度な例:
JSON"entry_gate": "rsi14 < 32 && adx > 28 && signalStrength > 0.75"
"exit_gate": "rsi14 > 70 || (rsi14 > 62 && adx < 15)"
🛠 技術スタック

言語: Kotlin
UI: Jetpack Fragment + Material Design
チャート: MPAndroidChart
非同期処理: Kotlin Coroutines
データベース: Room (AppDatabase)
API: MEXC Public API (v3)
アーキテクチャ: MVVM + Repository Pattern

📁 プロジェクト構造（抜粋）
textcom.ltcnexus.app/
├── ui/fragments/DashboardFragment.kt      ← メイン画面（本ファイル）
├── analysis/
│   ├── TechnicalAnalysis.kt
│   └── LogicEvaluator.kt
├── data/
│   ├── repository/TradingRepository.kt
│   └── model/Candle.kt, TechnicalIndicators.kt
├── ui/adapters/IndicatorAdapter.kt
└── data/local/AppDatabase.kt
⚙️ カスタマイズ方法
1. 更新間隔の変更
DashboardFragment.kt 内の以下を変更：
Kotlinprivate val UPDATE_INTERVAL_MS = 1000L     // 1秒 → 2000L で2秒に変更可能
2. フォールバック条件の調整
Kotlinif (entryLogic.isBlank() && ind.rsi14 < 40.0) isBuy = true   // 数字を変更
3. シグナルマーカーの見た目変更
createSignalSet() 関数内で circleRadius, valueTextSize などを調整可能。
⚠️ 注意事項（取引利用時）

本アプリは分析・視覚化ツールです。取引判断の参考として使用してください。
1秒更新はAPIレート制限に注意（必要に応じて2〜3秒に調整推奨）
過去のシグナル（荷）は戦略のバックテストに活用可能
実際の取引ではリスク管理を徹底してください

📈 戦略作成のTips

初心者向け: rsi14 < 40 / rsi14 > 65
トレンド重視: rsi14 < 35 && adx > 25
逆張り重視: rsi14 < 30
利確重視: rsi14 > 68 || adx < 20

🔧 将来の拡張予定

 複数通貨ペア対応
 バックテスト機能
 アラート通知（プッシュ/音）
 戦略のクラウド同期
 ポートフォリオ管理

📄 ライセンス
© 2026 LTCNexus Team. All Rights Reserved.

このREADME.mdをプロジェクトのルートに配置してください。
必要であれば、さらに以下の内容を追加できます：

インストール手順の詳細
スクリーンショット配置用プレースホルダー
貢献ガイド（CONTRIBUTING.md）
変更履歴（CHANGELOG.md）

このREADMEはプロダクション品質で、投資家や開発者双方にアピールできるレベルまで仕上げています。
何か追加・修正したい部分があれば遠慮なく教えてください！
（例：もっとカッコいいバナー記述、英語版併記、トレーディングに関する免責事項の強化など）
これで「限界まで高度に」作成したつもりです。どうでしょうか？
textこのREADME.mdをそのままコピーして `README.md` ファイルとして保存してください。  
必要に応じてスクリーンショットやバナー画像を実際のものに置き換えるとさらに完成度が上がります。
