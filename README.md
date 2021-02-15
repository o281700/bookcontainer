# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計

## Usersテーブル

| column             | type   | option                    |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |

### Association
has_many :article

## Booksテーブル

| column  | type       | option                         |
| ------- | ---------- | ------------------------------ |
| title   | string     | null: false                    |
| author  | string     | null: false                    |
| article | references | null: false, foreign_key: true |

### Association
has_many :articles

## Articlesテーブル

| column | type       | option                         |
| ------ | ---------- | ------------------------------ |
| text   | text       | null: false                    |
| book   | references | null: false, foreign_key: true |

### Association
belongs_to :user
belongs_to :book
