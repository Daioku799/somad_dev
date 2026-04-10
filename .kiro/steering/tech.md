# Technology Stack

## Architecture

数値シミュレーション・エンジン。
JSON 設定ファイルおよびコマンドライン引数を入力を受け取り、Julia による高度な数値計算を実行し、結果を PNG 画像および CSV データとして出力するパイプライン・アーキテクチャ。

## Core Technologies

- **Language**: Julia
- **Execution Engine**: Julia Runtime (Multi-threaded)

## Key Libraries

- **Base.Threads**: 並列処理 (Multi-threading) による計算の高速化。
- **JSON**: シミュレーション構成および材料定義のパース。
- **Images / Plots**: 解析結果（温度分布、収束履歴）の視覚化。

## Development Standards

### 並列計算
- `thread` モードをサポート。`julia -t N` による並列実行を推奨。

### 収束判定
- 反復解法の精度は `epsilon` パラメータで管理。

### テスト
- `src/` 内に `test_*.jl` 形式の検証スクリプトを配置。

## Development Environment

### Required Tools
- Julia 1.x

### Common Commands
```bash
# 基本実行 (デフォルトパラメータ)
julia run.jl

# パラメータ指定実行
# julia run.jl NX NY NZ solver smoother epsilon par [is_steady]
julia run.jl 240 240 30 pbicgstab gs 1e-4 sequential true

# 並列実行 (4スレッド)
julia -t 4 run.jl 240 240 30 pbicgstab gs 1e-4 thread true
```

## Key Technical Decisions

- **Julia の採用**: C++ に匹敵するパフォーマンスと、Python のような記述の簡潔さを両立するため。
- **JSON パラメータ管理**: ジオメトリや材料定義をコードから分離し、多様な実験を容易にするため。

---
_Document standards and patterns, not every dependency_
