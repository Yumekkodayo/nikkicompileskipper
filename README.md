# nikkicompileskipper

Allow you to skip the compile of InfinityNikki

インフィニティニキのシェーダーコンパイルをスキップできるツール

## 【やったこと】
Engine.ini設定で以下を強制有効化：

1️⃣ Bundled PSOキャッシュ機能を活性化

2️⃣ ディスクキャッシュの読み書きを許可

3️⃣ ランタイムコンパイルの最適化

## 【効果】

✅ 起動時のシェーダーコンパイルが完全スキップ

✅ ゲームプレイ中のカクつき現象解消

✅ 設定変更後のテストがスムーズに

※ PSOプリキャッシュは潜在的なバグを懸念し敢えて未使用
※ UE5公式ドキュメントとソースコードを参考に実装

## 【使い方】

1. **ゲームファイルパスの**  
   `X6Game\Saved\Config\Windows\Engine.ini` を開く
   なければつくる

2. **設定追記**（メモ帳等で編集）
   Engine.iniの内容を入れる

## 【説明】（Unreal Engine 5.3 Documentationより）

1️⃣ ShaderPipelineCacheシステム（Shader Cache Documentation）

「シェーダーコンパイルの待機時間を削減するため、事前計算済みパイプライン状態オブジェクト(PSO)をディスクキャッシュとして保存します。r.ShaderPipelineCache.Enabled=1は公式推奨設定です」

公式推奨事項：

起動時間改善のためPreOptimizeEnabledを有効化

ユーザーキャッシュ保存にSaveUserCache=1を設定

開発時以外はReportPSO=0が望ましい

2️⃣ D3D12 PSOキャッシュ（D3D12 RHI Documentation）

「ドライバー最適化キャッシュD3D12.PSO.DriverOptimizedDiskCache=1は、DirectX 12ランタイムとの統合を強化し、GPUドライバー固有の最適化を可能にします」

安全保証：

キャッシュファイルはSaved/ShaderCache/に隔離保存

ゲーム実行ファイル自体を改変しない安全な仕様

Epic Games公式プラグインと同じ仕組み

3️⃣ ユーザー設定の合法性（Engine Configuration Files）

「Engine.iniによるパラメータ調整は、Unreal Engineの標準機能です。[/Script/Engine.RendererOverrideSettings]セクションは、公式に提供されている設定オーバーライド機構です」

# 【免責声明】

**Unreal Engineに基づいたゲームの標準機能ではありますが、導入は自己責任でお願いします

**📌 ゲームファイル改変に関する禁止規定（インフィニティニキ利用規約より抜粋）**

**1. 直接的な禁止条項（第7.4条）**
✅ 以下の行為が明確に禁止されています：
- リバースエンジニアリング、逆コンパイル（7.4(2)）
- ゲームデータの改変・追加・削除（7.4(4)）
- 非公式ツール/プラグインの使用（7.4(6)）
- 設定ファイルを含むシステムデータの変更（7.4(4)）

**2. 間接的な禁止範囲（第5.3条）**
⚠️ 公式ライセンスの範囲外使用禁止：
> 「ユーザーは1台の端末でのみ非商業目的で使用可能」
> 「明示的に許可されていない権利はすべて留保」

**3. 技術的介入の禁止（第7.5条）**
🔒 特に禁止される行為例：
- ゲームデータの異常パフォーマンス（7.5(3)e）
- ハードウェアシンクロナイザー使用（7.5(5)）
- サードパーティ製ツール利用（7.5(4)）

**4. 処罰規定（第7.5条）**
⚖️ 違反時の対応措置：
- アカウント停止/データ削除（7.5a-h）
- 民事訴訟の提起可能性（7.5k）
- 端末レベルでの利用禁止（7.5i）

**5. 免責条項（第12.4条）**
🚫 ユーザーによる改変時の責任：
> 「データ異常がユーザーの違法行為に起因する場合、復元措置を講じうる」
> 「当社は一切の責任を負わない」

**💡 重要な解釈ポイント**
- 「Engine.ini」の書き換えは「システムデータの変更」に該当
- 読み取り専用設定は「正常なアップデートプロセスの妨害」と解釈されうる
- パフォーマンス向上目的でも技術的介入とみなされる可能性

**⚠️ ユーザーへのリスク**
- アカウント停止（3.6.3条）
- ゲームデータ削除（7.5e）
- 民事責任追及（7.5k）
- オンラインサービス利用禁止（7.5i）

上記の規約に抵触するおそれがあり、公式サポートへの問い合わせを強くおすすめします。
