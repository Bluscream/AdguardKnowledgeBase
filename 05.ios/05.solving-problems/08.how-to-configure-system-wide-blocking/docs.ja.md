---
title: "iOS版AdGuardでSafari外の広告ブロックを設定する方法（システムワイドブロック）"
taxonomy:
  category:
    - docs
---

- [システムワイドブロックについて](#system-wide)
- [【方法 ①】AdGuard DNS サーバーを有効にする](#server)
- [【方法 ②】DNS フィルタ/ホストファイルを追加する方法](#filters)

<a name="system-wide"></a>

iOS でのシステムワイドブロックとは、Safari ブラウザ以外、つまり他のアプリやブラウザで、ネットワークレベルで広告やトラッカー（個人情報追跡ソフト）をブロックすることです。

ほとんどの広告ブロッカーはこれをできませんが、AdGuard はできます。ただし、少し設定が必要です。

この記事では、お使いの iOS デバイスでこの機能を設定する方法をご紹介します。

<img src="https://cdn.adguard.com/public/Adguard/kb/DNS_filtering/how_dns_filtering_works_ja.png" style="border: 1px solid #efefef; max-height: 700px; max-width: 650px; padding: 2px;">
<p align="center"><i>AdGuardがDNSフィルタリングを使って広告をブロックする流れ</i></p>
    
AdGuardを使ってシステムワイドブロックを行うには2つの方法があります。

方法 ① 　 AdGuard DNS を有効にする（**設定 ⚙**→**DNS 通信を保護**→**DNS サーバー**→**AdGuard DNS**）

方法 ② 　 DNS フィルタを使う（例えば「AdGuard DNS フィルタ」）

両方とも効果は近いですが、DNS フィルタを有効にする**方法 ②**には、メリットがあります:

- DNS サーバーは任意のものにすることが可能（もしくは接続しない）
- DNS ホワイトリストを使用可能
- 複数の DNS フィルタやホストファイルを同時に使える

<a name="server"></a>

### 【方法 ①】AdGuard DNS サーバーを有効にする

システムワイドブロックを可能にする機能は AdGuard アプリ内の「DNS 通信を保護」です。

1. **設定**⚙→**DNS 通信を保護**→ スイッチを**オン**
2. **DNS サーバー**→**AdGuard DNS**

これで Safari 外で広告（※DNS レベルでブロック可能な広告）をブロックする AdGuard DNS サーバー設定完了です。

<img src="https://cdn.adguard.com/public/Adguard/Blog/ios_dns_protection_ja.PNG" style="border: 1px solid #efefef; max-height: 700px; max-width: 350px; padding: 2px;">
    
<a name="filters"></a>  
### 【方法②】DNSフィルタ/ホストファイルを追加する方法
    
高度な設定モードは基本的に詳しいユーザー向けの設定を表示するモードですが、Safari以外のアプリで広告等をブロックするDNSフィルタを追加するには、オンにする必要があります。
    
1. AdGuard iOSアプリ→設定⚙→一般
2. 高度な設定モード→オン

そうすると、「詳細設定」という項目が現れます。

<div style="display:flex">
     <div style="flex:1;padding-right:5px;">
          <img src="https://cdn.adguard.com/public/Adguard/Release_notes/iOS/v4.0/advanced_mode_ja.jpg" style="border: 1px solid #efefef; max-width: 350px; padding: 2px;">
     </div>
     <div style="flex:1;padding-left:5px;">
          <img src="https://cdn.adguard.com/public/Adguard/Blog/ios_advanced_settings_ja.PNG" style="border: 1px solid #efefef; max-width: 350px; padding: 2px;">
     </div>
</div>

> 注意：「詳細設定」タブにある設定をそのままオンにすることはお勧めできません（特に「ローレベル設定」）。中には、インターネット接続が切断されたり、プライバシーやセキュリティが損なわれたりするものもありますので、注意が必要です。

4. このリンクをコピーする: `https://adguardteam.github.io/AdGuardSDNSFilter/Filters/filter.txt`
5. AdGuard 設定 → DNS 通信を保護 → DNS フィルタリング (「高度な設定」モードのオンが必須) → DNS フィルタ
6. 「フィルタを追加する」→ フィルタの URL 欄に「４.」のリンクを貼り付ける → 次へ

<img src="https://cdn.adguard.com/public/Adguard/Blog/ios_adding_a_filter_ja.PNG" style="border: 1px solid #efefef; max-height: 700px; max-width: 350px; padding: 2px;">

完了です。36,000 本以上のフィルタリングルールが有効になり、Safari 外の広告もブロックされます（※DNS レベルでブロック可能なもの）。

**AdGuard DNS フィルタ**は、他の複数のフィルター（AdGuard のベースフィルター、SNS フィルター、追跡防止フィルター、モバイル広告フィルター、EasyList、EasyPrivacy など）から構成されています。
DNS レベルの広告ブロックとの互換性を高めるために特別に簡素化されています。DNS フィルタリングについて詳しくは、[この記事](https://kb.adguard.com/ja/general/dns-filtering)をご参照ください。

> **同じように、他にお好みの DNS フィルタリストも URL で追加できます。リストを探しの場合は、例えば[こちら](https://filterlists.com)で確認することができます。**

> AdGuard DNS や AdGuard DNS ファミリーサーバーを既に利用していて、特に問題が発生していない場合は、AdGuard DNS フィルタはそのサーバーに組み込まれているので追加しなくても結構です。

### DNS 通信を保護するメリット

高度な設定モードを有効にし、「DNS 通信を保護」を設定し、AdGuard DNS フィルタを追加することは、間違いなく価値があります。簡単に設定できて、全体的な保護レベルを新たなレベルへと導きます。AdGuard はトラフィックをローカルにフィルタリングし、好きな DNS サーバーを使用できるようになります。

**AdGuard の DNS フィルタ**には広告ドメインの幅広いリストが含まれており、これを有効にすると、Safari だけでなく、他のブラウザやサードパーティのアプリでも、あらゆる場所で広告ドメインがブロックされます。さらに、システムワイド保護により、Google、Facebook、その他のウェブ解析会社の悪名高い個人情報追跡からあなたを守ります。
