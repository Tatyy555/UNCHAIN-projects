### 🚢 メインネットへ移行したいとき

このチュートリアルの素晴らしいところは、**デプロイコストがかからない** ところです。

無料でデプロイして、メインネットで販売することで、誰でも USDC で収入を得ることができます。

**メインネットに移行したい場合は以下を参照してみてください。（チュートリアル内では実施しません。）**

メインネットでトランザクションを受けるには、以下の 2 つの変数を更新する必要があります。

1\. `createTransaction.js` で設定した テストネットの USDC SPL トークンアドレスを以下のとおりメインネットの USDC SPL トークンアドレスに変更します。

```jsx
const usdcAddress = new PublicKey("EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v");
```

2\. `_app.js` 及び `createTransaction.js` ファイル内の `WalletAdapterNetwork` 関数内にある `network` を以下のとおり変更します。

```jsx
const network = WalletAdapterNetwork.Mainnet;
```

たったこれだけでメインネットで販売することができます!


### 🎨 Web アプリケーションをアップグレードする

これにて MVP は完成です!

さて、それでは最後にあなたの Web アプリケーションのアップグレードに挑戦してみてください!

どうアレンジするかはあなたの自由ですが、私からは 3 つヒントを示しておきます!

1\. ショップのオーナーを増やし、オーナー権限のある人が商品を追加できるようにする。

2\. 商品データ及び注文情報を Solana チェーン上に保存する。

3\. 画像を NFT 化して商品にする機能を設ける。


### 🙉 `.gitignore` を確認する

Github などにコードをアップロードする際は、秘密鍵や構成ファイル等の見られたくないファイルはアップロードしないように設定する必要があります。

前のレッスンでも触れましたが、そういった際には `dotenv` モジュールを使用します。

ただし、Github にアップロードする場合、`.gitignore` に `.env` が含まれていないと `.env` も一緒にアップロードされてしまうので注意が必要です。

`.gitignore` の中身が以下のようなっているかどうか確認しましょう。（以下のとおりとなっていなければ以下のように変更します。）

```txt
node_modules
.DS_STORE
.env
```

> ⚠️ 注意
>
> ファイルの先頭に `.` がついているファイルは、「不可視ファイル」です。
>
> `.` がついているファイルやフォルダはその名の通り見ることができないので、「隠しファイル」「隠しフォルダ」とも呼ばれます。
>
> 操作されては困るファイルなどは、このように「不可視」の属性を持たせて、一般の人が触れられないように設定しておきましょう。


### 🚀 Vercel に Web アプリケーションをデプロイする

作成した Web アプリケーションをデプロイしてみましょう。

ここでは[Vercel](https://Vercel.com)を用いてデプロイします。

Vercel はサーバレス機能のホスティングを提供するクラウドプラットフォームです。

スケーリングやサーバの監視は Vercel が行うため、開発者は Vercel へデプロイするだけでアプリケーションを公開・運用できます。

Vercel のアカウントをお持ちでない方は、上記のリンクにアクセスして、アカウントを作成してください。

まず、`solana-pay-starter-project` の最新コードを GitHub にプッシュします。

ターミナルで `solana-pay-starter-project` に移動し、以下のコマンドをそれぞれ実行しましょう。

```bash
git add .
git commit -m "upload to github"
git push
```

続いて、以下の手順で Vercel にデプロイします。

1\. Vercel のダッシュボードから、`New Project` をクリックしてください。

![new project](/public/images/303-Solana-Online-Store/section-4/4_1_1.png)

2\. `Import Git Repository` で自分の GitHub アカウントを接続したら、Web アプリケーションのリポジトリを `Import` してください。

![Import](/public/images/303-Solana-Online-Store/section-4/4_1_2.png)

3\. プロジェクトの設定では、**FRAMEWORK PRESET** に `Create React App`、**ROOT DIRECTORY** に `app` を入力してください。

4\. **Environment Variables** に環境変数 `CI = false` （ NAME: CI 、 VALUE: false ）を追加します。（警告が原因でビルドが失敗しないようになります。）

5\. **Environment Variables** に `.env` で設定した環境変数（ NAME: SOLANA_NETWORK 、 VALUE: devnet ）を直接入力してください。（ GitHub には `.env` ファイルを保存していないため、`Vercel` に直接記載する必要があります。）

![Environment Variables1](/public/images/303-Solana-Online-Store/section-4/4_1_3.png)

![Environment Variables2](/public/images/303-Solana-Online-Store/section-4/4_1_4.png)

6\. [Deploy]ボタンを押してデプロイします。（ Vercel は GitHub と連動しているので、GitHub が更新されるたびに自動でデプロイを行ってくれます。）

**Vercel へのデプロイが無事完了しました!**

ぜひデプロイされた Web アプリケーションを自分の目で確認してみてください!!


### 🙋‍♂️ 質問する

ここまでの作業で何かわからないことがある場合は、Discord の `#solana-online-store` で質問をしてください。

ヘルプをするときのフローが円滑になるので、エラーレポートには下記の 4 点を記載してください ✨

```
1. 質問が関連しているセクション番号とレッスン番号
2. 何をしようとしていたか
3. エラー文をコピー&ペースト
4. エラー画面のスクリーンショット
```


### 🎫 NFT を取得しよう!

NFT を取得する条件は、以下のようになります。

1. MVP の機能がすべて実装されている（実装 OK ）

2. Web アプリケーションで MVP の機能が問題なく実行される（テスト OK ）

3. このページの最後にリンクされている Project Completion Form に記入する

4. Discord の `🔥｜solana-post-projects` チャンネルに、あなたの Web サイトをシェアしてください 😉🎉 。Discord へ投稿する際に、追加実装した機能とその概要も教えていただけると幸いです!

プロジェクトを完成させていただいた方には、NFT をお送りします。


### 🎉 おつかれさまでした!

あなたは、独自のオンラインストアをデプロイし、Web アプリケーションを立ち上げました。

これらは、分散型 Web アプリケーションがより一般的になる社会の中で、世界を変える重要なスキルです。

UI のデザインや機能をアップグレードして、ぜひコミュニティにシェアしてください!　 😊

これからも Web3 への旅をあなたが続けてくれることを願っています 🚀
