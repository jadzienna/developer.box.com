---
rank: 2
related_endpoints:
  - get_events
  - options_events
related_guides:
  - events/for-user
  - events/polling
  - events/pagination
required_guides: []
alias_paths: []
category_id: events
subcategory_id: null
is_index: false
id: events/for-enterprise
type: guide
total_steps: 5
sibling_id: events
parent_id: events
next_page_id: events/polling
previous_page_id: events/for-user
source_url: >-
  https://github.com/box/developer.box.com/blob/main/content/guides/events/for-enterprise.md
fullyTranslated: true
---
# エンタープライズイベントの取得

エンタープライズイベントを取得するには、管理者権限を持つユーザーを認証し、`stream_type`を`admin_logs`に設定して[`GET /events`](e://get_events) APIを呼び出します。

<Samples id="get_events" variant="enterprise">

</Samples>

<Message>

このAPIを使用するには、ユーザーは**新規レポートの実行および既存レポートへのアクセスを行う**のための権限を持つ、会社の管理者または共同管理者である必要があります。

</Message>

## イベントタイプによるフィルタ

エンタープライズイベントフィードでは、イベントタイプによるフィルタがサポートされています。

<Samples id="get_events" variant="enterprise_filter">

</Samples>

イベントタイプの完全なリストについては、以下を参照してください。

## 制限

管理者イベントフィードでは、Long pollingがサポートされません。イベントに対するLong pollingでは、ユーザーイベントフィードを使用します。

Boxでのイベントの保存は無期限ではありません。

ユーザーイベントは2週間から2か月間保存され、その後、保存されたユーザーイベントは削除されます。エンタープライズイベントには、APIを介した場合は1年間、Box管理コンソールのエクスポートされたレポート経由の場合は7年間アクセスできます。

このフィードでは、レイテンシよりも完全性を重視しています。つまり、Boxでは管理者イベントをユーザーフィードよりも高いレイテンシで配信することがあります。ユーザーイベントストリームとは違い、管理者イベントストリームでは、特定のイベントに対するフィルタが可能ですが、Long pollingはサポートされていません。

## イベントタイプ

エンタープライズに対して、以下のイベントがトリガーされます。

<!-- markdownlint-disable line-length -->

| イベント名                                                         | 説明                                                                                                                              |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `ACCESS_GRANTED`                                              | Boxサポートに対する自分のアカウントへのアクセス権限の付与                                                                                                  |
| `ACCESS_REVOKED`                                              | Boxサポートに付与した自分のアカウントへのアクセス権限の取り消し                                                                                               |
| `ADD_DEVICE_ASSOCIATION`                                      | デバイスの関連付けの追加                                                                                                                    |
| `ADD_LOGIN_ACTIVITY_DEVICE`                                   | 未確認のデバイスからのログイン                                                                                                                 |
| `ADMIN_LOGIN`                                                 | 管理コンソールを使用した管理対象ユーザーアカウントへのログイン                                                                                                 |
| `APPLICATION_CREATED`                                         | 開発者コンソールでの新しいアプリケーションの作成                                                                                                        |
| `APPLICATION_PUBLIC_KEY_ADDED`                                | アプリケーションへの公開キーの追加                                                                                                               |
| `APPLICATION_PUBLIC_KEY_DELETED`                              | アプリケーションからの公開キーの削除                                                                                                              |
| `CHANGE_ADMIN_ROLE`                                           | 管理者の役割の変更                                                                                                                       |
| `CHANGE_FOLDER_PERMISSION`                                    | フォルダの権限の変更                                                                                                                      |
| `COLLABORATION_ACCEPT`                                        | 招待の承諾                                                                                                                           |
| `COLLABORATION_EXPIRATION`                                    | コラボレータへの有効期限の設定                                                                                                                 |
| `COLLABORATION_INVITE`                                        | 招待                                                                                                                              |
| `COLLABORATION_REMOVE`                                        | コラボレータの削除                                                                                                                       |
| `COLLABORATION_ROLE_CHANGE`                                   | ユーザーロールの変更                                                                                                                      |
| `COLLECTION_CREATE`                                           | コレクションの作成                                                                                                                       |
| `COLLECTION_DELETE`                                           | コレクションの削除                                                                                                                       |
| `COLLECTION_UPDATE`                                           | コレクションの更新                                                                                                                       |
| `COLLECTION_ITEM_CREATE`                                      | コレクションへの項目の追加                                                                                                                   |
| `COLLECTION_ITEM_DELETE`                                      | コレクションからの項目の削除                                                                                                                  |
| `COLLECTION_ITEM_UPDATE`                                      | コレクションの項目の更新                                                                                                                    |
| `COMMENT_CREATE`                                              | ファイル上でのコメントの作成                                                                                                                  |
| `COMMENT_DELETE`                                              | ファイル上のコメントの削除                                                                                                                   |
| `CONTENT_ACCESS`                                              | 承認されたエンドユーザーまたはBoxアプリケーションでのプログラムによるファイルへのアクセス                                                                                  |
| `CONTENT_WORKFLOW_ABNORMAL_DOWNLOAD_ACTIVITY`                 | 管理コンソールで設定されたポリシーのトリガー                                                                                                          |
| `CONTENT_WORKFLOW_AUTOMATION_ADD`                             | 自動化の追加                                                                                                                          |
| `CONTENT_WORKFLOW_AUTOMATION_DELETE`                          | 自動化の削除                                                                                                                          |
| `CONTENT_WORKFLOW_POLICY_ADD`                                 | コンテンツポリシーの追加                                                                                                                    |
| `CONTENT_WORKFLOW_SHARING_POLICY_VIOLATION`                   | 共有ポリシーの違反                                                                                                                       |
| `CONTENT_WORKFLOW_UPLOAD_POLICY_VIOLATION`                    | 管理者が設定したアップロードポリシーの違反                                                                                                           |
| `COPY`                                                        | コピー                                                                                                                             |
| `DATA_RETENTION_CREATE_RETENTION`                             | リテンションの作成                                                                                                                       |
| `DATA_RETENTION_REMOVE_RETENTION`                             | リテンションの削除                                                                                                                       |
| `DELETE`                                                      | 削除                                                                                                                              |
| `DELETE_USER`                                                 | ユーザーの削除                                                                                                                         |
| `DEVICE_TRUST_CHECK_FAILED`                                   | デバイストラストチェックの失敗                                                                                                                 |
| `DOWNLOAD`                                                    | ダウンロード                                                                                                                          |
| `EDIT`                                                        | 編集                                                                                                                              |
| `EDIT_USER`                                                   | ユーザーの編集                                                                                                                         |
| `EMAIL_ALIAS_CONFIRM`                                         | ユーザーのメールエイリアスの確認                                                                                                                |
| `EMAIL_ALIAS_REMOVE`                                          | ユーザーのメールエイリアスの削除                                                                                                                |
| `ENTERPRISE_APP_AUTHORIZATION_UPDATE`                         | JWTアプリケーションの承認または再承認                                                                                                            |
| `EXTERNAL_COLLAB_SECURITY_SETTINGS`                           | 外部コラボレーション用セキュリティ設定の変更                                                                                                          |
| `FAILED_LOGIN`                                                | ログインの失敗                                                                                                                         |
| `FILE_MARKED_MALICIOUS`                                       | ファイルでのウイルスの検出。イベントは、通知を希望した企業にのみ送信されます。                                                                                         |
| `FILE_WATERMARKED_DOWNLOAD`                                   | 電子すかし付きファイルのダウンロード                                                                                                              |
| `GROUP_ADD_ITEM`                                              | グループへの項目の追加                                                                                                                     |
| `GROUP_ADD_USER`                                              | グループへのユーザーの追加                                                                                                                   |
| `GROUP_CREATION`                                              | 新規グループの作成                                                                                                                       |
| `GROUP_DELETION`                                              | グループの削除                                                                                                                         |
| `GROUP_EDITED`                                                | グループの編集                                                                                                                         |
| `GROUP_REMOVE_ITEM`                                           | 管理コンソールを使用したグループからのフォルダの削除                                                                                                      |
| `GROUP_REMOVE_USER`                                           | グループからのユーザーの削除                                                                                                                  |
| `ITEM_MODIFY`                                                 | 変更した項目                                                                                                                          |
| `ITEM_OPEN`                                                   | 開いた項目                                                                                                                           |
| `ITEM_SHARED_UPDATE`                                          | 共有リンク設定の更新                                                                                                                      |
| `ITEM_SYNC`                                                   | フォルダが同期されました。                                                                                                                   |
| `ITEM_UNSYNC`                                                 | フォルダの同期の解除                                                                                                                      |
| `LEGAL_HOLD_ASSIGNMENT_CREATE`                                | リーガルホールド割り当ての作成                                                                                                                 |
| `LEGAL_HOLD_ASSIGNMENT_DELETE`                                | リーガルホールド割り当ての削除                                                                                                                 |
| `LEGAL_HOLD_POLICY_CREATE`                                    | リーガルホールドポリシーの作成                                                                                                                 |
| `LEGAL_HOLD_POLICY_DELETE`                                    | リーガルホールドポリシーの削除                                                                                                                 |
| `LEGAL_HOLD_POLICY_UPDATE`                                    | リーガルホールドポリシーの更新                                                                                                                 |
| `LOCK`                                                        | ロック                                                                                                                             |
| `LOGIN`                                                       | ログイン                                                                                                                            |
| `METADATA_INSTANCE_CREATE`                                    | メタデータインスタンスの作成                                                                                                                  |
| `METADATA_INSTANCE_DELETE`                                    | メタデータインスタンスの削除                                                                                                                  |
| `METADATA_INSTANCE_UPDATE`                                    | メタデータインスタンスの更新                                                                                                                  |
| `METADATA_TEMPLATE_CREATE`                                    | メタデータテンプレートの作成                                                                                                                  |
| `METADATA_TEMPLATE_UPDATE`                                    | メタデータテンプレートの更新                                                                                                                  |
| `METADATA_TEMPLATE_DELETE`                                    | メタデータテンプレートの削除                                                                                                                  |
| `MOVE`                                                        | 移動                                                                                                                              |
| `NEW_USER`                                                    | ユーザーの作成                                                                                                                         |
| `OAUTH2_ACCESS_TOKEN_REVOKE`                                  | OAuth 2.0アクセストークンの取り消し                                                                                                          |
| `PREVIEW`                                                     | プレビュー                                                                                                                           |
| `REMOVE_DEVICE_ASSOCIATION`                                   | デバイスの関連付けの削除                                                                                                                    |
| `REMOVE_LOGIN_ACTIVITY_DEVICE`                                | アプリに関連付けられたユーザーセッションの無効化                                                                                                        |
| `RENAME`                                                      | ファイルまたはフォルダの名前や説明の変更                                                                                                            |
| `RETENTION_POLICY_ASSIGNMENT_ADD`                             | リテンションポリシー割り当ての追加                                                                                                               |
| `SHARE`                                                       | 共有リンクの有効化                                                                                                                       |
| `SHARE_EXPIRATION`                                            | 共有リンクへの有効期限の設定                                                                                                                  |
| `SHIELD_ALERT`                                                | 企業のShieldルールに基づいた、Shieldによる異常なダウンロード、セッション、場所、悪意のあるコンテンツの検出。詳細については、[Shieldのアラートイベント](g://events/shield-alert-events)を参照してください。 |
| `SHIELD_EXTERNAL_COLLAB_ACCESS_BLOCKED`                       | 外部コラボレーションへのアクセスのブロック                                                                                                           |
| `SHIELD_EXTERNAL_COLLAB_ACCESS_BLOCKED_MISSING_JUSTIFICATION` | 正当な理由がない場合の外部コラボレーションへのアクセスのブロック                                                                                                |
| `SHIELD_EXTERNAL_COLLAB_INVITE_BLOCKED`                       | 外部コラボレーションへの招待のブロック                                                                                                             |
| `SHIELD_EXTERNAL_COLLAB_INVITE_BLOCKED_MISSING_JUSTIFICATION` | 正当な理由がない場合の外部コラボレーションへの招待のブロック                                                                                                  |
| `SHIELD_EXTERNAL_COLLAB_INVITE_JUSTIFIED`                     | 外部コラボレーションへの招待の承認                                                                                                               |
| `SHIELD_JUSTIFICATION_APPROVAL`                               | Shieldの正当な理由の承認                                                                                                                 |
| `STORAGE_EXPIRATION`                                          | ファイルへの自動削除の設定                                                                                                                   |
| `TASK_ASSIGNMENT_UPDATE`                                      | タスク割り当ての更新                                                                                                                      |
| `TASK_ASSIGNMENT_CREATE`                                      | タスク割り当ての作成                                                                                                                      |
| `TASK_ASSIGNMENT_DELETE`                                      | タスク割り当ての削除                                                                                                                      |
| `TASK_CREATE`                                                 | タスクの作成                                                                                                                          |
| `TASK_UPDATE`                                                 | タスクのコメントの編集                                                                                                                     |
| `TERMS_OF_SERVICE_ACCEPT`                                     | 利用規約が承諾されました。                                                                                                                   |
| `TERMS_OF_SERVICE_REJECT`                                     | 利用規約の拒否                                                                                                                         |
| `UNDELETE`                                                    | 削除の取り消し                                                                                                                         |
| `UNLOCK`                                                      | ロックの解除                                                                                                                          |
| `UNSHARE`                                                     | 共有リンクの削除                                                                                                                        |
| `UPDATE_COLLABORATION_EXPIRATION`                             | コラボレータの有効期限の延長                                                                                                                  |
| `UPDATE_SHARE_EXPIRATION`                                     | 共有リンクの有効期限の延長                                                                                                                   |
| `UPLOAD`                                                      | アップロード                                                                                                                          |
| `USER_AUTHENTICATE_OAUTH2_ACCESS_TOKEN_CREATE`                | OAuth 2.0アクセストークンの作成                                                                                                            |
| `WATERMARK_LABEL_CREATE`                                      | ファイルへの電子すかしの追加                                                                                                                  |
| `WATERMARK_LABEL_DELETE`                                      | ファイルからの電子すかしの削除                                                                                                                 |

<!-- markdownlint-enable line-length -->

## 匿名ユーザー

場合によっては、イベントフィードには、IDが`2`のユーザーが表示される可能性があります。これは、匿名ユーザーを表すBoxの内部識別子です。

匿名ユーザーは、ログインしていないユーザーです。この状況は、ユーザーがコンテンツを操作し、最初にログインを求められない場合にいつでも発生する可能性があります。たとえば、ユーザーが、公開共有リンクを使用してファイルをダウンロードするときなどです。
