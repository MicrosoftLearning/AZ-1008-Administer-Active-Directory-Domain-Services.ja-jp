---
lab:
  title: 演習 - セキュリティ設定を構成する
  module: Guided Project – Administer Active Directory Domain Services
---
この演習では、ドメイン アカウントに対する NTLM 認証の無効化、アカウント管理アクティビティの監査、セキュリティ グループのメンバーに対するサービスとしてのログオンの拒否など、セキュリティに関連する設定を構成します。

## NTLM 認証を制限する

このタスクでは、NTLM 認証を制限します。 このタスクを完了するには、TAILWIND-DC1 で次の手順を実行します。

1.  サーバー マネージャーの [ツール] メニューで、[グループ ポリシー管理コンソール] を開きます。
2.  [グループ ポリシー管理コンソール] で、tailwindtraders.internal フォレスト、Domains フォルダー、tailwindtraders.internal ドメインを展開します。 次に、グループ ポリシー オブジェクトを展開します。
3.  **[既定のドメイン コントローラー ポリシー]** を右クリックし、**[編集]** をクリックします。
4.  [コンピューターの構成]\\[ポリシー]\\[Windows の設定]\\[セキュリティ設定]\\[ローカル ポリシー]\\[セキュリティ オプション] に移動します。
5.  **[ネットワーク セキュリティ]: [NTLM を制限]: [このドメイン内の NTLM 認証]** を選択してダブルクリックします。
6.  **[これらのポリシー設定を定義する]** チェック ボックスをクリックします。
7.  値 **[すべて拒否]** を選択し、**[OK]** をクリックします。
8.  [設定変更の確認] ダイアログ ボックスで、**[はい]** を選択します。
9.  グループ ポリシー管理エディターを閉じます。

## シドニーでのユーザー アカウント管理を監査する

このタスクでは、シドニー OU でユーザー アカウント管理の監査を有効にします。 このタスクを完了するには、TAILWIND-DC1 で次の手順を実行します。

1.  サーバー マネージャー コンソールの [ツール] メニューから、[グループ ポリシー管理コンソール] を選択します。
2.  [グループ ポリシー管理コンソール] で、Tailwindtraders.internal ドメインを展開します。
3.  シドニー OU に移動し、**[このドメインに GPO を作成し、ここにリンクする]** を右クリックして選択します。
4.  新しい GPO の名前を付けます`SydneyOUPolicy`。
5.  **[OK]**
6.  SydneyOUPolicy を右クリックし、**[編集]** を選択します。
7.  [コンピューターの構成]\\[ポリシー]\\[Windows 設定]\\[セキュリティ設定]\\[高度な監査ポリシーの構成]\\[監査ポリシー]\\[アカウント管理] の順に移動します。
8.  **[監査ユーザー アカウント管理]** を選択してダブルクリックします。
9.  **[次の監査イベントを構成する]** チェック ボックスをクリックします。
10.  **[成功]** 値と **[失敗]** 値を選択し、**[OK]** をクリックします。
11.  グループ ポリシー管理エディターを閉じる

## サービスとしてのログオンを拒否する

このタスクでは、[サービスとしてのログオンを拒否する] セキュリティ オプションを構成します。 このタスクを完了するには、TAILWIND-DC1 で次の手順を実行します。

1.  サーバー マネージャーの [ツール] メニューで、[グループ ポリシー管理コンソール] を開きます。
2.  Tailwindtraders.internal ドメインを展開します。
3.  シドニー OU に移動し、SydneyOUPolicy を右クリックします。 **編集**を選択します。
4.  [コンピューターの構成]\\[ポリシー]\\[Windows の設定]\\[セキュリティ設定]\\[ローカル ポリシー]\\[ユーザー権利の割り当て] に移動します。
5.  **[サービスとしてのログオンを拒否する]** ポリシーを選択してダブルクリックします。
6.  **[このポリシーを定義する]** 設定を選択します。
7.  **[ユーザーまたはグループの追加]** をクリックします。
8.  **[参照]** をクリックし、**[詳細]** をクリックしてから、**[今すぐ検索]** をクリックします。
9.  **シドニー管理者**グループを選択します。
10. ダイアログ ボックスが閉じるまで **[OK]** をクリックします (4 つまたは 5 つの受信確認が必要な場合があります)。