# APPLICATION PROGRAMMER PORTFOLIO

## Zhao Shengchao

**C++ / Unreal Engine / Gameplay Systems / Console Development**

モノリスソフト
アプリケーションプログラマー応募用

- E-mail：[aleidi04@outlook.com](mailto:aleidi04@outlook.com)
- GitHub：`【https://github.com/aleidi/Portfolio.git】`
- 更新日：2026年8月

<div style="page-break-after: always;"></div>

# 1. PROFILE

## 職務概要

ゲームプレイ、クライアントシステム、入力、マルチプラットフォーム移植、音声、描画基盤、リソースパイプラインおよび開発ツールの設計・実装に携わってきました。主にC++、C#、Pythonを使用し、Unreal Engine、Unity、DirectX 11、FMOD、FBX SDKを利用した開発経験があります。

業務では、企画担当者や他セクションと要件を整理し、感覚的なゲーム体験や既存システムの振る舞いを、実装可能な技術仕様へ分解することを重視してきました。また、仕様や元システムの情報が十分でない場合にも、既存コード、実データ、実行結果から挙動を調査し、段階的に検証しながらシステムを構築してきました。

## Application Programmerとしての強み

### 他職種と連携し、企画案をゲームシステムとして具現化する

企画担当者が目指す遊びや挙動を理解し、必要なルール、状態遷移、計算方法、パラメーターを整理した上で、調整可能なゲームシステムとして設計・実装できます。さらに、企画担当者との調整やQA・開発責任者による検証を通じてフィードバックを反映し、完成品質まで高められます。

### ゲームプレイと基盤を横断して考える

キャラクター制御、カメラ、スキル、UIなどのゲームプレイ側に加え、描画、入力デバイス、音声ランタイム、リソースロードおよびデータ変換も経験しています。下位層の制約がプレイヤー体験や開発ワークフローへ与える影響を踏まえて設計できます。

### 既存システムへ安全に機能を統合する

大規模な既存コードの呼び出し関係と責務を調査し、互換レイヤーや共通状態を設けることで、変更範囲を管理しながら新しいSDK、ミドルウェア、入力方式を統合してきました。

<div style="page-break-after: always;"></div>

# 2. COMMERCIAL PROJECT 01

## 『GUNDAM EVOLUTION』エイムアシスト機能開発

| 項目 | 内容 |
| --- | --- |
| 種別 | 商用タイトル開発／製品導入済み |
| 開発環境 | Unreal Engine、C++ |

### 概要

ゲームパッドではマウスよりも細かな照準操作が難しい一方、強すぎる補正はプレイヤーの意図を妨げます。企画担当者が示した操作感の方向性を、プレイヤーの入力を尊重しながら狙いやすさを向上させる処理として実装しました。

### 担当内容

- 企画担当者との仕様協議、およびView Friction、Feet Rotation、ADS Attraction、Reticle Magnetismの四方式の技術設計
- 対象検出・選別、補正量計算、視点・照準への適用処理のC++実装
- 強度・適用範囲のパラメーター化と、実行時切り替え、デバッグ表示、プロファイリング手段の整備
- 企画担当者、開発責任者、QA担当者による実機検証と調整の支援

### 実装方針

感覚的な「狙いやすさ」を、対象までの距離、照準位置、角度差、移動方向・速度、入力および補助時間へ分解しました。画面内に複数の候補が存在する場合にも、プレイヤーが狙おうとしている対象を選べるよう、補助対象としての適否と優先順位を判定するルールへ落とし込みました。その上で、補助方式ごとに補正量を求めるモデルを設計し、強度と適用範囲をパラメーター化しました。

### 成果

- 四種類のエイムアシスト処理を完成させ、実機検証を経て製品へ導入
- 企画担当者とQA担当者の評価を、各方式の数値調整へ継続的に反映できる環境を構築
- 操作感の要件整理から実装、調整、製品導入までを一貫して担当

### 関連する公開記事

共同開発した企画担当者が、代表的な方式と設計上の考え方を[Aim Assist Types](https://medium.com/@hyang0451/aim-assist-types-6c5993d47a10)で公開しています。この記事は企画担当者本人の著作物であり、私の成果物ではありません。

**詳細資料**：[AimAssist/AimAssist_プロジェクト説明資料.md](AimAssist/AimAssist_プロジェクト説明資料.md)

# 3. COMMERCIAL PROJECT 02

## 『Starsand Island』Nintendo Switch 2版マウス操作の開発

| 項目 | 内容 |
| --- | --- |
| 種別 | 商用タイトル開発／マルチプラットフォーム対応 |
| 開発環境 | Unity、C#、Nintendo Switch 2 SDK |

### 概要

Joy-Con 2によるマウス操作を、既存の物体配置・編集、地形編集、カメラ、メニューおよび操作案内へ統合しました。同じJoy-Con 2をゲームパッドとマウスの両方として使用できるため、接続機器の種類だけでは現在の操作方法を判断できない点が課題でした。

### 担当内容

- Nintendo Switch 2 SDKからのポインター座標、ボタン状態、使用姿勢の取得
- 仮想カーソル、毎フレーム更新、デバイス変更監視を含む入力基盤の実装
- ユーザー設定、デバイス状態、ゲーム状態に基づく入力モード管理
- 物体・地形編集、カメラ、メニュー、操作案内への統合と、切り替え時の操作状態の引き継ぎ
- デバッグ手段、社内向けサンプル、CEDEC共同講演資料の整備

### 実装方針

SDK依存の入力取得とゲーム側のモード判定を分離し、各機能が共通の入力状態へ追従する構成としました。切り替え時には進行中の操作状態を引き継ぎ、操作と表示の不一致や二重入力を防ぎました。

### 成果

- Joy-Con 2のマウス操作を既存の編集、カメラ、メニュー、操作案内へ一貫して統合
- ゲームパッド／マウス切り替え時にも、操作状態と画面表示を維持できる入力基盤を構築
- デバイス認識からゲーム内操作までを段階的に検証できる環境を整備
- 実装知見をサンプルと講演資料へ整理し、クライアントの映像使用許諾のもと、[CEDEC 2026「Nintendo Switch 2への移植：マウス対応とUnity / Unreal Engine 5におけるパフォーマンスの最適化」](https://cedec.cesa.or.jp/2026/timetable/detail/s69f2f05d355d5/)で共同講演者として共有

**詳細資料**：[Switch2マウス開発/Switch2マウス開発_プロジェクト説明資料.md](Switch2マウス開発/Switch2マウス開発_プロジェクト説明資料.md)

# 4. COMMERCIAL PROJECT 03

## マルチプラットフォーム向け音声基盤移植

| 項目 | 内容 |
| --- | --- |
| 種別 | 商用タイトル移植／音声基盤 |
| 開発環境 | C++、CMake、FMOD Studio API／Core API |
| 対象 | Windows、PlayStation 5、Xbox Series、Nintendo Switch |

### 概要

PlayStation 3固有の音声基盤をFMODへ置き換え、Windows、PlayStation 5、Xbox Series、Nintendo Switchへ移植しました。ゲーム側の多数の処理が既存APIと制御IDを利用していたため、既存の呼び出しを維持しながら新しい音声基盤へ接続する必要がありました。

### 担当内容

- 既存音声API、制御ID、呼び出し関係、およびプラットフォーム固有処理の調査
- 既存ゲーム側APIとFMODを接続する互換レイヤーおよび音声モジュールの設計・実装
- 再生、停止、時間軸、音量、Pitch、Filter、Envelope、Dry／Wet、Reverbの意味変換
- SE、BGM、ボイス、カットシーン向けBank／Event管理とロード処理の実装
- 四つの対象プラットフォームへの初期化、ビルド、実行対応

### 実装方針

既存のゲーム側APIと制御IDを維持し、互換レイヤーで要求の意味をFMODへ変換することで、ゲームロジック側の変更範囲を抑えました。

### 成果

- ゲームロジック側の主要な音声制御フローを維持
- FMOD共通処理とプラットフォーム固有初期化を分離
- 四つの対象プラットフォームを同一モジュールで管理できる構成を構築

**詳細資料**：[音声基盤移植/音声基盤移植_プロジェクト説明資料.md](音声基盤移植/音声基盤移植_プロジェクト説明資料.md)

# 5. COMMERCIAL PROJECT 04

## 独自形式モデルデータ変換ツール

| 項目 | 内容 |
| --- | --- |
| 種別 | 商用タイトル開発／Editor・リソースパイプライン |
| 開発環境 | Unreal Engine、C++、FBX SDK、Perforce |

### 概要

独自形式を生成した元システムのソースコードと十分な正式仕様がなく、さらに複数versionでデータ構造が異なっていました。実ファイルから変換に必要な構造を調査し、Unreal Engineで利用可能なモデルへ復元する必要がありました。

### 担当内容

- 実ファイル、公開情報、既知のモデル情報を用いたバイナリ構造とversion差分の調査
- version分岐を扱うBinary Readerとモデル中間データの設計・実装
- 頂点、法線、UV、頂点カラー、インデックス、Material、Transformの属性変換
- FBX SDKによるScene、Node、Mesh、Material生成とFBX出力
- Unreal Engineへのインポート経路の接続、およびクライアントの実データを用いた検証

### 実装方針

独自形式の解析とUnreal Engineへの取り込みを分離するため、モデル中間データとFBXを採用しました。これにより、解析と属性変換に集中しながら、Unreal Engineの既存Importerとチーム内のFBX拡張を再利用しました。

### 成果

- 不完全な情報から変換に必要なバイナリ構造を特定
- 複数versionの独自形式をFBXへ変換し、Unreal Engineへ取り込む経路を構築
- 解析、属性変換、FBX生成を個別に検証できる構成を整備
- クライアントの実運用と開発側のサンプル確認を通じて変換結果を検証

**詳細資料**：[モデルデータ変換ツール_プロジェクト説明資料.md](モデルデータ変換ツール/モデルデータ変換ツール_プロジェクト説明資料.md)

<div style="page-break-after: always;"></div>

# 6. COMMERCIAL PROJECT 05

## 独自スクリプト言語からLuaへの変換ツール

| 項目 | 内容 |
| --- | --- |
| 種別 | 商用タイトル開発／スクリプト移行ツール |
| 開発環境 | Python、PLY、Perforce |

### 概要

業務プロジェクトで使用されていた大量の独自スクリプトをLua環境へ移行するため、一括変換ツールを開発しました。正式な言語仕様と元処理系のソースコードがない状態から、実際のスクリプトを調査して変換に必要な文法と実行上の意味を整理しました。

### 担当内容

- 既存スクリプトからの言語仕様調査と、Token・文法規則の整理
- PLYを用いたLexer／Parser、AST、意味変換、Luaコード生成の設計・実装
- 型、スコープ、親子関係、コメントを保持するAST中間表現の設計
- 複数ファイルの関数シグネチャを収集する事前解析と、ファイル間の呼び出しを考慮した変換
- コメントおよびLua向け型注釈を含む、保守可能なコード出力

### 実装方針

構文解析、意味変換、コード生成をASTによって分離し、調査で判明した変換規則をノード単位で追加できる構成としました。型、制御構造、評価順序の違いを考慮し、文字列連結、`for`文、前置／後置インクリメント、参照引数などを、元の意味を維持するLua表現へ変換しました。

### 成果

- 対象スクリプトを一括変換し、後続システムへ組み込めるLuaコードとして出力
- 元コードのコメントと型情報を引き継ぎ、移行後も保守しやすい成果物を生成

**詳細資料**：[言語変換ツール_プロジェクト説明資料.md](言語変換ツール/言語変換ツール_プロジェクト説明資料.md)

<div style="page-break-after: always;"></div>

# 7. PUBLIC CODE SAMPLE

## MW リアルタイムバトルRPG向け技術プロトタイプ

| 項目 | 内容 |
| --- | --- |
| 種別 | 業務外の個人開発／開発中の技術プロトタイプ |
| 開発環境 | Unreal Engine 5、C++、Python、Blender |
| 主な技術 | Gameplay Ability System、Enhanced Input、Primary Asset、Asset Manager、MVVM |
| 本人担当 | 企画、設計、実装、データ／リソース管理、Editor・DCCスクリプト |

> 本プロジェクトは完成したゲームではありません。現在は、リアルタイムバトルRPGを想定した中核システムの基礎実装と技術検証を進めています。本資料では実装済みの範囲と未完成の範囲を区別します。

## 現在の主要な実装

- InputTagによる通常スキル／チャージスキル／その他Ability入力の振り分け
- プレイヤー入力とAI SkillIdを`FMWSkillCastCommand`へ変換する共通形式
- Gameplay EventからGAS Abilityを起動する共通経路
- Abilityの検証、Commit、使用回数消費、Montage再生、終了処理
- 対象との距離に基づく同一Montage内の`Close`／`Far` Section選択
- Charge InputTagごとの蓄積、途中解放、減衰、再入力、満蓄力発動
- DataTable、Primary Asset、Asset Bundleによるキャラクターリソース管理
- UIレイヤー、Widgetキャッシュ、一部の戦闘ViewModel

## スキル実行の責務分割

```text
プレイヤー InputTag ─┐
                      ├→ SkillComponent → SkillCastCommand → Gameplay Event
AI SkillId ──────────┘                                      ↓
                                                          GAS Ability
                                                             ↓
                                    距離／チャージ形態 → Commit → Montage
```

入力元とスキル実行を分離し、プレイヤーとAIが下流のAbility処理を共用できる構成としました。Ability側は要求元のデバイスやAI判断を意識せず、検証、コスト、リソース解決、アニメーションライフサイクルを処理します。

<div style="page-break-after: always;"></div>

## 距離適応型スキル

同じスキルでも、対象との距離に応じて近距離形態または遠距離形態を選択します。形態ごとに別Abilityを作らず、同一の発動経路とMontageを利用し、`Close`／`Far` Sectionを選択します。

```text
SkillCastCommand
    ↓
Charge Variantか？ ─ Yes → Charge Sectionを維持
    ↓ No
Range Adaptive設定を取得
    ↓
対象を検索し距離を判定
    ├─ Near → Close Section
    ├─ Far  → Far Section
    └─ No Target → 設定によりFail / Close / Far
```

## 蓄力入力

Charge InputTagごとに独立した状態を保持します。最大値に達する前に入力を解放した場合は即座にゼロへ戻さず、徐々に減衰します。減衰中に再入力すると残量から蓄力を再開できます。

```text
Pressed → Delay → Charging → Full
                       ↓ Release before Full
                     Decaying
                       ↓ Pressed again
                     Charging
```

この設計により、移動や状況判断を挟みながらスキルを分割して準備する操作を検証しています。

## 推奨コードレビュー入口

| 順序 | シンボル | 確認できる内容 |
| --- | --- | --- |
| 1 | `AMWPlayerController::Input_AbilityInputTagPressed` | 通常、チャージ、非スキルAbilityの入力ルーティング |
| 2 | `UMWSkillComponent::TryBuildCastCommandFromInputTag` | InputTag、Slot、SkillId、Variantの変換 |
| 3 | `UMWSkillComponent::RequestCastBySkillId` | AI要求を共通コマンドへ接続する入口 |
| 4 | `UMWSkillBase::TryCommitAndPlayFromCommand` | 表示解決、実行可否、Commit、Montage再生 |
| 5 | `UMWRangeAdaptiveSkill::ActivateAbility` | Chargeの優先、対象距離、Close／Far形態選択 |
| 6 | `UMWChargeInputProcessor` | 蓄積、途中解放、減衰、再入力、満蓄力判定 |

## 公開サンプルの範囲

本サンプルでは、入力要求からGAS Abilityの起動、距離・蓄力形態の選択、Montageの完了までを確認できます。敵味方を考慮した対象選択、AI意思決定、ダメージ処理、スキルリソースの完全なライフサイクル、および戦闘全体のゲームループは公開範囲に含めていません。

**詳細資料**：[MW_プロジェクト説明資料.md](MW/MW_プロジェクト説明資料.md)
**コード／動画**：[GitHub - MWProject / Demoブランチ](https://github.com/aleidi/MWProject/tree/Demo) / [MW_Demo.mp4](MW/MW_Demo.mp4)

<div style="page-break-after: always;"></div>

# 8. EARLY COMPLETE PROJECT

## 3D Tank Box ― C++／DirectX 11による3D戦車ゲーム

| 項目 | 内容 |
| --- | --- |
| 種別 | 入社時技術研修／4名のチーム制作 |
| 開発期間 | 2020年5月～7月、約1.5か月 |
| 開発環境 | C++、HLSL、Win32、DirectX 11、DirectInput、FreeType |
| 本人担当 | 基盤、描画、全Shader、文字、3C、Gameplay、Particle、Cutscene、レベル統合 |
| 成果 | タイトルから戦闘、ボス戦、ゲーム終了までプレイ可能なゲームを完成 |

## 担当した主な領域

- Win32アプリケーションとゲームメインループ
- `GameObject`、`Component`、`Transform`、`SceneManager`
- DirectX 11 Device、SwapChain、Render Target、Depth Buffer
- `Drawable`／`Bindable`による描画リソースとPipeline Stateの構成
- Vertex／Pixel／Geometry Shader、UI、Skybox、VFX、Particle
- 戦車移動、砲塔、カメラ、ADS、照準、射撃
- Raycastによるカメラ衝突と照準点／砲口間の射撃方向処理
- CSVキーフレームによる簡易カットシーン
- 敵配置、イベント、UI、Sound、VFXを含む1ステージの統合

## Application Programmerとして得た基礎

入力、Camera、Tank、Projectile、VFX、Sound、UIを一連のプレイ体験として接続しました。また、共通基盤を他メンバーへ提供し、AI担当者の実装をステージ進行やボス戦へ統合しました。これにより、基盤APIの設計がチームのコンテンツ実装と最終的なゲーム体験へ与える影響を理解しました。

- **デモ動画**：[3DTank/実機動作デモ動画.mp4](3DTank/実機動作デモ動画.mp4)
- **詳細資料**：[3DTank_プロジェクト説明資料.md](3DTank/3DTank_プロジェクト説明資料.md)
- **PDF**：[3DTank_プロジェクト説明資料.pdf](3DTank/3DTank_プロジェクト説明資料.pdf)

<div style="page-break-after: always;"></div>

# 9. REVIEW GUIDE

## 公開成果物を中心とした確認順序

1. **3D Tank Box（デモ動画・プロジェクト説明資料）**
   初期キャリアの作品として、C++／DirectX 11の基盤から3C、戦闘、演出、ステージ進行までを統合し、プレイ可能なゲームを完成させた経験。

2. **GUNDAM EVOLUTION / Aim Assist（詳細資料・関連公開記事）**
   感覚的な操作要件と対象選択を調整可能なルールへ分解し、企画・QAと連携して製品へ導入した商用開発経験。

3. **Starsand Island / Nintendo Switch 2 Mouse Operation（CEDEC公式セッション・詳細資料）**
   新しいデバイス入力を大規模な既存機能へ統合し、操作状態と画面表示の一貫性を保った商用開発経験。

4. **MW Skill System（個人制作のプロトタイプ）**
   現在の実装例として、Unreal Engine 5／C++で入力元、スキルルール、GAS Ability、Montage、データを分離したコード設計。

## 提出物

| 資料 | 目的 | 状態 |
| --- | --- | --- |
| 本Portfolio | 経験全体と職種適合性を短時間で確認 | 完成 |
| 3D Tank動画 | 完成した3Dアクションゲームを確認 | 既存動画あり |
| 3D Tank設計資料 | 基盤、描画、3C、ゲーム進行の担当範囲を確認 | 既存資料あり |
| MWコード／レビューガイド | 現在のUE5／C++設計と処理経路を確認 | `【公開用に整備】` |
| MW技能システム動画 | 距離形態、蓄力、Abilityライフサイクルを確認 | `【録画予定】` |
| プロジェクト別詳細資料 | 設計判断、処理構成、実装、制限を確認 | 既存資料あり |

## 公開範囲と成果の帰属

- 業務プロジェクトのソースコード、内部資料および未公開映像は提出しません。
- 業務経験は、公開可能な技術概要、本人担当、設計判断および結果に限定して説明しています。
- チーム成果と個人成果を区別し、第三者が担当した素材・基盤を本人の成果に含めません。
- MWは個人開発ですが、参考実装と第三者素材を本人の成果から区別します。
- Aim Assistの関連記事は共同開発した企画担当者の著作物です。

## Contact

- 氏名：Zhao Shengchao
- E-mail：[aleidi04@outlook.com](mailto:aleidi04@outlook.com)
- GitHub：`【https://github.com/aleidi/Portfolio.git】`

---

**ゲーム体験の意図を理解し、技術仕様へ分解し、他セクションと協力しながら完成形へつなげるApplication Programmerを目指しています。**
