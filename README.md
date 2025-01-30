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

# Unreal Engineに基づいたゲームの標準機能ではありますが、導入は自己責任でお願いします


