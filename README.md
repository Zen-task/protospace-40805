# ProtoSpaceのER図

## usersテーブル
| カラム名              | 型       | 制約                                |
|-----------------------|----------|-------------------------------------|
| email                 | string   | NOT NULL, ユニーク制約              |
| encrypted_password    | string   | NOT NULL                           |
| name                  | string   | NOT NULL                           |
| profile               | text     | NOT NULL                           |
| occupation            | text     | NOT NULL                           |
| position              | text     | NOT NULL                           |

## prototypesテーブル
| カラム名              | 型         | 制約                                |
|-----------------------|------------|-------------------------------------|
| title                 | string     | NOT NULL                           |
| catch_copy            | text       | NOT NULL                           |
| concept               | text       | NOT NULL                           |
| user                  | references | NOT NULL, 外部キー                 |

**備考**: `image` は ActiveStorage で実装するため、テーブル設計には含めません。

## commentsテーブル
| カラム名              | 型         | 制約                                |
|-----------------------|------------|-------------------------------------|
| content               | text       | NOT NULL                           |
| prototype             | references | NOT NULL, 外部キー                 |
| user                  | references | NOT NULL, 外部キー                 |

## テーブル間の関係
- **usersテーブル** と **prototypesテーブル** は1対多の関係です。
- **prototypesテーブル** と **commentsテーブル** も1対多の関係です。
- **usersテーブル** と **commentsテーブル** は1対多の関係です。
