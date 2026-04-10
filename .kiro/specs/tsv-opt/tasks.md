# Tasks: tsv-opt (Model Expansion)

`Heat3D-original` ベースのモデル拡張機能の実装タスク。

## Phase 1: 基礎構築と環境整備
- [ ] `Heat3D-original/extensions/` ディレクトリの作成
- [ ] `Heat3D-original/base/heat3d.jl` のソルバー部分をモジュールとして呼び出せるか調査・整理
- [ ] ダミーの JSON (TSV) と GDSII ファイルを用意する

## Phase 2: データローダーの実装
- [ ] `ConfigLoader.jl`: JSON から TSV 情報を読み込む構造体と関数の実装
- [ ] `GDSLoader.jl`: GDSII の矩形情報を読み込み、グリッド上に反映する関数の実装 (参照: `H2-main_TSV_Opt/src/modelA.jl`)

## Phase 3: モデルビルダーの実装
- [ ] `ModelManager.jl`: 各層の初期化、GDSII 反映、TSV 配置を統合するロジックの実装
- [ ] 座標系変換（実空間 [m] からグリッドインデックス）の整合性確保

## Phase 4: 統合とエントリポイント
- [ ] `run_expanded.jl`: 拡張機能を用いたメイン実行スクリプトの作成
- [ ] プロット機能の統合 (断面図による配置確認)

## Phase 5: 検証とクリーンアップ
- [ ] TSV 座標と太さが正しく反映されているかの視覚的確認
- [ ] `Heat3D-original` の基本性能を損なっていないかのベンチマーク
- [ ] 不要なデバッグコードの削除とドキュメント整理
