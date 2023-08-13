# メンタルヘルスアプリ

このアプリは、ユーザーが自分のメンタルステータスを追跡し、リカバリーセッションを利用して改善することを目的としています。

## 主な機能

- ユーザー登録・ログイン
- メンタルステータスの入力・表示
- リカバリーセッションとアクションの管理
- ユーザーフィードバックの提供と表示
- 提案されるリカバリーアクションの管理

## 技術スタック

- **バックエンド**: Laravel 10.0 with Laravel Sail, Swagger
- **フロントエンド**: React, Typescript, Sass
- **データベース**: MySQL (via Laravel Sail)

## セットアップ方法

### バックエンド:

1. リポジトリをクローン:

   ```bash
   git clone [リポジトリのURL]
   ```

2. Sailを使用して依存関係をインストールとコンテナを起動:

   ```bash
   ./vendor/bin/sail up
   ```

3. Sailを使用してデータベースをセットアップ:

   ```bash
   sail artisan migrate
   ```

### フロントエンド:

1. フロントエンドディレクトリに移動:

   ```bash
   cd [フロントエンドのディレクトリ]
   ```

2. 必要な依存関係をインストール:

   ```bash
   npm install
   ```

3. ローカルサーバーを立てる:

   ```bash
   npm start
   ```

## 注意事項

フロントエンドとバックエンドは完全に分離されているので、それぞれのローカルサーバーを立てる必要があります。

---


# 問題

## **背景**

現代社会におけるデジタルデバイスの普及は目覚ましく、スマートフォンやコンピュータは私たちの生活に欠かせない存在となっています。しかし、その一方で、これらのデバイスの過度な使用は、集中力の低下、睡眠障害、目の疲れ、さらには精神的ストレスなど、多くの健康上の問題を引き起こしています。特に、コンスタントな情報の流れやSNSの使用は、常に接続されている感覚を生む一方で、リアルな人間関係や現実のタスク遂行に対するモチベーションの低下をもたらすことがあります。

## **問題の詳細**

多くの人々が、デジタルデバイスを手放すことの難しさやその影響を自覚していますが、その制限方法や代替の行動を見つけることが難しいのが現状です。その結果、生産性の低下、無駄な時間の浪費、メンタルヘルスの問題などが増加しています。この問題に対する実用的な解決策が求められています。

## **ゴールの詳細**

本アプリケーションは、ユーザーが自分自身のデジタルデバイス使用パターンを意識し、それを適切に管理するためのツールを提供します。具体的には、デバイス使用時間のトラッキング、目標設定と達成のサポート、デジタルデトックスのためのリマインダーやアドバイスを提供することで、ユーザーがより健康的で充実した日常生活を送る手助けをします。

## **スコープ外の詳細**

本アプリケーションは、デジタルデバイスの物理的な使用を制限する機能やハードウェア的な介入を提供するものではありません。また、専門的なメンタルヘルスのアドバイスや治療を提供するものでもありません。あくまで、ユーザー自身の意識と行動をサポートするためのツールとしての位置付けです。

## **MVV (Mission, Vision, Values)**

- **Mission (ミッション):** ユーザーが健康的で充実した日常生活を実現するためのデジタルデトックスと目標達成のサポートを提供する。
- **Vision (ビジョン):** デジタルデバイスの適切な使用とリアルな生活の充実を追求する社会の実現。
- **Values (バリュー):**
    1. **ユーザーセンタリック:** ユーザーの実際のニーズと期待を常に考慮する。
    2. **健康重視:** メンタルとフィジカルの健康を最優先とする。
    3. **継続的な成長:** アプリケーションの機能やサービスを常に更新・向上させることで、ユーザーの成長をサポートする。
 # **ソリューション**

## 主要機能

### **MentalTracking: メンタルの状態を記録と推移の確認**

1. **メンタルステータスの入力**:
    - **日次記録**: ユーザーは日常のメンタルの状態を数値、テキスト、絵文字などの形式で入力します。例えば、スライダーを使用して1〜10の範囲で気分を評価する、または「良好」「普通」「悪い」などのテキストベースの選択肢を提供するなど。
    - **詳細メモの追加**: さらに、ユーザーはその日に感じたこと、起こった出来事、特定のストレス要因などの詳細なメモや記述を付け加えることができます。
2. **メンタルの推移の確認**:
    - **視覚的な表示**: 入力されたデータはグラフやカレンダー形式で視覚的に表示されます。例えば、月間の気分の推移を示すライングラフや、日々の気分をカラーコードで示すカレンダーなど。
    - **パターンの識別**: 長期的なデータのトレンドや繁忙期、休日などの特定の日に関連するメンタルの変動などのパターンを見つけ出すための分析ツールやヒントを提供します。
3. **フィードバックとリマインダー**:
    - **リマインダー機能**: ユーザーが毎日の記録を忘れないように、リマインダーや通知を設定することができます。
    - **アクティブなフィードバック**: 例えば、連続した好調な日々や、連続してメンタルが低下している日々など、特定のトレンドが見られる場合、アプリからユーザーへのフィードバックやアドバイスを提供します。
  
---
# 設計
## クラス図

### 1. Class: User

- **Properties**:
    - user_id: Int
    - username: String
    - email: String
    - password: String
- **Methods**:
    - createUser(): User
    - loginUser(email: String, password: String): User
    - logoutUser(): Void
    - updateUserDetails(): User
    - deleteUser(): Void
- **Relationships**:
    - One to Many: MentalStatusInput
    - One to Many: UserFeedback

### 2. Class: MentalStatusInput

- **Properties**:
    - input_id: Int
    - user: User
    - mental_status: Int
    - input_date: DateTime
- **Methods**:
    - addInput(): MentalStatusInput
    - getPreviousStatuses(user: User): List<MentalStatusInput>
    - updateInput(): MentalStatusInput
    - deleteInput(): Void
- **Relationships**:
    - Many to One: User

### 3. Class: RecoverySession

- **Properties**:
    - session_id: Int
    - session_name: String
- **Methods**:
    - createSession(): RecoverySession
    - getAllSessions(): List<RecoverySession>
    - getSessionDetails(session_id: Int): RecoverySession
    - updateSession(): RecoverySession
    - deleteSession(): Void
- **Relationships**:
    - One to Many: RecoveryAction
    - One to Many: UserFeedback

### 4. Class: RecoveryAction

- **Properties**:
    - action_id: Int
    - session: RecoverySession
    - action_name: String
    - duration: Int
    - order: Int
- **Methods**:
    - addActionToSession(): RecoveryAction
    - getActionsInSession(session: RecoverySession): List<RecoveryAction>
    - updateAction(): RecoveryAction
    - removeActionFromSession(): Void
- **Relationships**:
    - Many to One: RecoverySession

### 5. Class: UserFeedback

- **Properties**:
    - feedback_id: Int
    - user: User
    - session: RecoverySession
    - effect: String
    - impression: String
- **Methods**:
    - provideFeedback(): UserFeedback
    - getUserFeedbacks(user: User): List<UserFeedback>
    - updateFeedback(): UserFeedback
    - deleteFeedback(): Void
- **Relationships**:
    - Many to One: User
    - Many to One: RecoverySession

### 6. Class: SuggestedRecoveryAction

- **Properties**:
    - action_id: Int
    - action_name: String
    - duration: Int
- **Methods**:
    - getAllSuggestedActions(): List<SuggestedRecoveryAction>
    - addSuggestedAction(): SuggestedRecoveryAction
    - updateSuggestedAction(): SuggestedRecoveryAction
    - deleteSuggestedAction(): Void
- **Relationships**:
    - No direct relationships with other classes, but indirectly associated with RecoveryAction

