---
title: "AdGuard使用時FaceTime不具合の対処法"
taxonomy:
  category:
    - docs
---

「Full-Tunnel」モードは、他の VPN アプリケーションとの互換性だけでなく、FaceTime との AdGuard 互換性も阻害する可能性があることが判明しております。

一部のユーザーは、iOS 用 AdGuard アプリが「Full-Tunnel」モードの場合、デバイス上で FaceTime が機能しないという問題に遭遇しています。

AdGuard が「Full-Tunnel（VPN アイコンなし）」モードになっている場合、FaceTime が動作する可能性は高いですが、１００％安定した動作は保証できません。

**AdGuard 使用時に FaceTime を使用し、ビデオ/オーディオ通話が停止しないようにするには、「Split-Tunnel」モードに切り替えてください。**

※この不具合の対処法は、「DNS 通信を保護」がオンの場合に必要です。

<img src="https://cdn.adguard.com/public/Adguard/kb/newscreenshots/Ja/iOS/tunnel-mode.png?!" style="border: 1px solid #efefef; max-width: 300px; padding: 2px;">

【「Split-Tunnel」モードに切り替える方法】

1. AdGuard アプリ内**設定**⚙ → **一般設定**
2. **高度な設定モード** のスイッチをオンにする
3. その下に現れる **詳細設定** をタップ
4. **Tunnel モード** → **Split-Tunnel** を選択してください。

完了です！これで、FaceTime の互換性に問題はないはずです。
