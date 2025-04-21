# Vibra Symphony

![Unity](https://img.shields.io/badge/Unity-2021.3-blue)

---

## プロジェクト概要

**Vibra Symphony** は、VR ライブ鑑賞体験を拡張するリアルタイムフィードバックシステムです。  
ライブ音源をアプリ内で FFT（高速フーリエ変換）解析し、ドラムやベースなどのビートに合わせてスマートフォンを振動させることで、**聴覚と触覚**を融合します。

---

## デモ動画

![VR ライブ空間](./docs/vr_concert.png)  
![スマホ振動マッピング](./docs/vibration_demo.gif)

---

## 主な機能

- **Android アプリ**  
  - ローカルストレージ内の MP3 ファイルを一覧表示  
  - 選択した MP3 を TCP/IP ソケットで Oculus Quest にストリーム送信  
- **VR 会場モデリング & 自由移動**  
  - **Blender** で作成した 3D ライブステージと観客席  
  - Oculus Quest のスティックで会場内を自由に歩行・移動可能  
- **リアルタイム FFT 解析 & ビート検出**  
  - Unity C# `OnAudioFilterRead` + FFT でドラム／ベースのピークを検出  
- **OSC 通信によるビート通知**  
  - ドラム／ベース検出時に OSC通信 で Android に高速通知  
- **スマホ振動制御**  
  - Android 側で OSC 受信 → `Vibrator` API による振動パターン再生  
- **360° VR ライブ鑑賞 UX**  
  - Oculus Quest で 360° 映像と空間音響を再生  
  - ビートに同期したカメラエフェクト・Haptics  
---

## 使用技術

- **VR プロジェクト**  
  - Unity
  - **モデリング**：Blender（会場・ステージ・観客席）  
  - **アニメーション**：モーションキャプチャーデータ（BVH/FBX）  
  - **移動制御**：
    - Unity Character Controller による歩行シミュレーション  
  - **音声解析**：Unity C# `OnAudioFilterRead` ＋ FFT 分析   
  - **MP3 送信**：TCP/IP
  - **振動データ送信**：UDP/IP
  - **その他通信**：TCP/IP 
  - **振動**：Android `Vibrator` API  
---
