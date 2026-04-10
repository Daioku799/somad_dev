# Project Structure

## Organization Philosophy

モジュール形式の数値計算ライブラリ構成。
共通のソルバー (`src/`) を持ちつつ、特定の解析プロジェクト (`H2-main_TSV_Opt/`) や実験データ、比較用コード (`Heat3D-original/`) が共存する構造。

## Directory Patterns

### Core Source
**Location**: `/src/`  
**Purpose**: 熱伝導方程式のソルバー、境界条件、物理定数、収束判定などのコアロジック。  
**Example**: `heat3ds.jl`, `boundary_conditions.jl`

### Optimization Project
**Location**: `/H2-main_TSV_Opt/`  
**Purpose**: TSV の最適化を目的としたメインの開発および実験ディレクトリ。設定、実行スクリプト、出力結果を含む。  
**Example**: `config.json`, `run.jl`

### Legacy/Original Reference
**Location**: `/Heat3D-original/`  
**Purpose**: オリジナル版のコードベース。新しい実装の正当性検証や比較のための参照。

## Naming Conventions

- **Files**: 原則として `snake_case.jl` (一部 `PascalCase.jl` が存在するが、新規ファイルは Julia の標準的な慣習に準ずる)
- **Functions**: `snake_case` (Julia の標準的な慣習)

## Import Organization

Julia の `LOAD_PATH` に `src/` を追加することで、モジュールを動的にインクルードする。

```julia
# 実行スクリプトでのインポート例
push!(LOAD_PATH, joinpath(@__DIR__, "src"))
include("src/heat3ds.jl")
```

## Code Organization Principles

- **疎結合なソルバー**: 計算アルゴリズム (`RHS.jl`) と境界条件 (`boundary_conditions.jl`) を分離し、多様な物理モデルに対応可能にする。
- **データ駆動型設計**: ジオメトリや材料は `config.json` から読み込み、計算エンジン自体は汎用性を保つ。

---
_Document patterns, not file trees. New files following patterns shouldn't require updates_
