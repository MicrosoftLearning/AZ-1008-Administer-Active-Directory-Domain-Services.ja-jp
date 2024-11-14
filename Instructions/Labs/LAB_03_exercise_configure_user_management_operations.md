---
lab:
  title: '演習 - ユーザー管理操作を構成する '
  module: Guided Project – Administer Active Directory Domain Services
---
この演習では、ユーザー管理操作を実行します。

## 組織単位を作成する

このタスクでは、シドニー、メルボルン、ブリスベンの 3 つの OU を作成します。 このタスクを完了するには、次の手順を実行します。

1.  TAILWIND-DC1 で、サーバー管理コンソールの [ツール] メニューから [Active Directory ユーザーとコンピューター] を開きます。
2.  **tailwindtraders.internal** ドメインを右クリックします。
3.  **[新規]** を選択してから、**[組織単位]** を選択します。
4.  [新しいオブジェクト - 組織単位] ダイアログ ボックスで、名前を `Sydney` に設定し、**[OK]** をクリックします。
5.  このプロセスを繰り返して、`Melbourne` OU と `Brisbane` OU を作成します。

## ユーザーの作成

このタスクでは、ユーザーを作成し、アカウントの有効期限などのアカウント プロパティを構成します。 このタスクを完了するには、次の手順を実行します。

1.  TAILWIND-DC1 で、[Active Directory ユーザーとコンピューター] (または管理センター) を開きます。
2.  シドニー OU を右クリックします。
3.  **[新規]** を選択してから、**[ユーザー]** を選択します。
4.  [フル ネーム] フィールドと [ユーザー ログオン名] フィールドに `SydneyContractor` を入力し、**[次へ]** をクリックします。
5.  `Pa55w.rdPa55w.rd` などのパスワードを指定してから、パスワードを確認します。
6.  **[次へ]** と **[完了]** をクリックします。
7.  シドニー OU を選択します。 シドニー OU で、SydneyContractor ユーザー アカウントをダブルクリックします。
8.  [アカウント] タブの **[アカウント有効期限]** セクションで、**終了日**を選択し、日付を **2030 年 1 月 1 日**に設定します。 **OK** をクリックします。
9.  SydneyContractor ユーザーを右クリックし、**[コピー]** を選択します。
10. [フル ネーム] フィールドと [ユーザー ログオン名] フィールドに `MelbourneContractor` と入力します。 **次へ** をクリックします。
11. `Pa55w.rdPa55w.rd` などのパスワードを指定してから、パスワードを確認します。
12. **[次へ]** と **[完了]** をクリックします。
13. SydneyContractor ユーザーを右クリックし、**[コピー]** を選択します。
14. [フル ネーム] フィールドと [ユーザー ログオン名] フィールドに `BrisbaneContractor` と入力します。 **次へ** をクリックします。
15. `Pa55w.rdPa55w.rd` などのパスワードを指定してから、パスワードを確認します。
16. **[次へ]** と **[完了]** をクリックします。
17. MelbourneContractor ユーザーをメルボルン OU にドラッグします。
18. オブジェクトの移動に関する警告が表示されたら、**[はい]** をクリックします。
19. BrisbaneContractor ユーザーをブリスベン OU にドラッグします。
20. オブジェクトの移動に関する警告が表示されたら、**[はい]** をクリックします。


## シドニー管理者グループを作成する

このタスクでは、シドニー管理者という名前の新しいセキュリティ グループを作成します。 このタスクを完了するには、次の手順を実行します。

1.  TAILWIND-DC1 で、[Active Directory ユーザーとコンピューター] を開きます。
2.  シドニー OU を右クリックし、**[新規]** を選択してから、**[グループ]** を選択します。
3.  グループ名に `Sydney Administrators` と入力し、グループ スコープで **[ユニバーサル]** を選択します。 **OK** をクリックします。
4.  シドニー OU で、SydneyContractor ユーザー アカウントをダブルクリックします。
5.  [メンバー] タブで **[追加]** をクリックします。
6.  「`Sydney Administrators`」と入力します。
7.  [**名前の確認**] をクリックします。
8.  **[OK]** をクリックしてから、もう一度 **[OK]** をクリックします。

## ユーザーを保護されたユーザーとして構成する

このタスクでは、SydneyContractor ユーザー アカウントを保護されたユーザーとして構成します。 このタスクを完了するには、次の手順を実行します。

1.  TAILWIND-DC1 で、[Active Directory ユーザーとコンピューター] (または管理センター) を開きます。
2.  シドニー OU に移動し、SydneyContractor ユーザー アカウントをダブルクリックします。
3.  [メンバー] タブで **[追加]** をクリックします。
4.  「`Protected Users`」と入力します。
5.  [**名前の確認**] をクリックします。
6.  **[OK]** をクリックしてから、もう一度 **[OK]** をクリックします。

## OU へのセキュリティ アクセス許可をセキュリティ グループに委任する

このタスクでは、パスワードをリセットし、シドニー OU のアカウントを介してパスワードの変更をシドニー管理者グループに強制する機能を委任します。 このタスクを完了するには、次の手順を実行します。

1.  TAILWIND-DC1 で、[Active Directory ユーザーとコンピューター] を開きます。
2.  シドニー OU を右クリックし、**[コントロールの委任]** をクリックします。
3.  コントロールの委任ウィザードのウェルカム ページで、**[次へ]** をクリックします。
4.  **[追加]** をクリックし、`Sydney Administrators` を入力します。
5.  [**名前の確認**] をクリックします。
6.  **[OK]** をクリックし、**[次へ]** をクリックします。
7.  [委任するタスク] ページで、**[ユーザーのパスワードをリセットして次回ログオン時にパスワードの変更を要求する]** オプションを選択します。 **[次へ]** をクリックします。
8.  **[完了]** をクリックします。

## ユーザーの市区町村属性を構成する

このタスクでは、ユーザー アカウントの市区町村属性を構成し、[検索] 属性を使用してユーザーが存在することを確認します。 このタスクを完了するには、次の手順を実行します。

1.  TAILWIND-DC1 で、[Active Directory ユーザーとコンピューター] を開きます。
2.  シドニー OU を選択し、SydneyContractor ユーザー アカウントを右クリックして、**[プロパティ]** をクリックします。
3.  シドニー請負業者のプロパティの [住所] タブで、[市区町村] フィールドを `Sydney` に設定し、**[OK]** をクリックします。
4.  [Active Directory ユーザーとコンピューター] で、Tailwindtrader.internal を右クリックし、**[検索]** をクリックします。
5.  [ユーザー、連絡先、グループの検索] ダイアログ ボックスの [詳細設定] タブで、**[フィールド]**、**[ユーザー]**、**[市区町村]** の順に選択します。 条件を **である (正確に)** に設定します。 値を **シドニー** に設定します。 **[Find Now]** をクリックします。
6.  [ディレクトリ内の検索] ポップアップで **[はい]** をクリックします。
7.  **検索結果**にユーザー SydneyContractor が表示されていることを確認します。
8.  [ユーザー、連絡先、グループの検索] ダイアログ ボックスを閉じます。

## メルボルン契約社員ユーザーを無効にする

このタスクでは、メルボルン請負業者ユーザーを無効にします。 このタスクを完了するには、次の手順を実行します。

1.  TAILWIND-DC1 で、[Active Directory ユーザーとコンピューター] を開いてから、メルボルン OU を開きます。
2.  メルボルン OU で、**MelbourneContractor** を右クリックし、**[アカウントの無効化]** をクリックします。
3.  **OK** をクリックします。

## ブリスベン契約社員ユーザーのパスワードをリセットする

このタスクでは、BrisbaneContractor ユーザーのパスワードをリセットします。 このタスクを完了するには、次の手順を実行します。

1.  TAILWIND-DC1 で、[Active Directory ユーザーとコンピューター] を開いてから、ブリスベン OU を開きます。
2.  BrisbaneContractor ユーザーを右クリックし、**[パスワードのリセット]** を選択します。
3.  [パスワードのリセット] ダイアログ ボックスで、パスワード `Pa66w.rdPa66w.rd` を 2 回入力し、**[OK]** を選択します。 パスワードが変更されたことを通知したダイアログで、もう一度 **[OK]** をクリックします。