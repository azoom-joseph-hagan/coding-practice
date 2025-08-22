# D&Dキャラクタージェネレーター

友達とダンジョンズ＆ドラゴンズを遊ぶ準備はできましたが、サイコロを忘れてしまいました！仮想のサイコロを振ってキャラクター作成をシミュレートするプログラムを書きましょう。

## あなたのタスク

`src/dnd-character.ts`にある`DnDCharacter`クラスを完成させて、ランダムなD&Dキャラクターを生成してください。

### キャラクター作成のルール

1. **能力値**: 各キャラクターには6つの能力値があります（筋力、敏捷力、耐久力、知力、判断力、魅力）

   - 6面ダイスを4つ振って各能力値を生成します
   - 最も低い出目を1つ除き、残りの3つを合計します
   - 有効な能力値の範囲は3から18です

2. **能力値修正値**: 能力値を次の式で修正値に変換します: `floor((能力値 - 10) / 2)`

   - 能力値 10-11 の範囲 = +0 の修正値
   - 能力値 8-9 の範囲 = -1 の修正値
   - 能力値 12-13 の範囲 = +1 の修正値

3. **ヒットポイント**: キャラクターの初期体力 = `10 + 耐久力修正値`

### 例

筋力のために [5, 3, 1, 6] を振った場合:

- 1（最も低い）を除外
- 合計: 5 + 3 + 6 = 14 の筋力
- 修正値: floor((14 - 10) / 2) = +2

## はじめに

### 前提条件

- Node.js (バージョン18以上)
- npm または yarn

### インストール

1. このプロジェクトをクローンまたはダウンロードします
2. 依存関係をインストールします:

```bash
npm install
```

### テストの実行

全てのテストを実行するには:

```bash
npm test
```

ウォッチモードでテストを実行するには:

```bash
npm run test:watch
```

### 使用方法

```typescript
import { DnDCharacter } from "./src/dnd-character"

// 新しいランダムなキャラクターを作成
const character = new DnDCharacter()

console.log(`筋力: ${character.strength}`)
console.log(`敏捷力: ${character.dexterity}`)
console.log(`耐久力: ${character.constitution}`)
console.log(`知力: ${character.intelligence}`)
console.log(`判断力: ${character.wisdom}`)
console.log(`魅力: ${character.charisma}`)
console.log(`ヒットポイント: ${character.hitpoints}`)

// 単一の能力値を生成
const abilityScore = DnDCharacter.generateAbilityScore()
console.log(`ランダムな能力値: ${abilityScore}`)

// 特定の能力値に対する修正値を取得
const modifier = DnDCharacter.getModifierFor(15)
console.log(`15の修正値: ${modifier}`)
```

### 実装する必要があるもの

`src/dnd-character.ts`を見てください。実装が必要な2つのメソッドを持つクラスの骨組み（スケルトン）があります。

1.  **`generateAbilityScore()`** - 4つのダイスを振り、最も低い出目を除いて、上位3つの合計を返します
2.  **`getModifierFor(abilityValue)`** - 能力値を修正値に変換します

さらに、以下の実装も必要です。

-   全6つの能力値を生成し、ヒットポイントを計算するコンストラクタを追加する
-   キャラクターの能力値とヒットポイントを保存するためのプロパティを追加する

### 解答のテスト

```bash
npm test
```

テストは、あなたのキャラクタージェネレーターが正しく動作するかを検証します。実装が完了したら、すべてのテストが合格するはずです。
