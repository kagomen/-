- サブドメインを作成したい場合

  - CNAME レコードを追加し、name にサブドメイン名、target にドメインを設定する
    - 例
      - Type: CNAME
      - Name: blog
      - Target: kagome.dev
      - TTL: auto
      - 上記の登録で、blog.kagome.dev が公開される

- DMARC をサブドメインに設定したい場合

  ```
  DMARCレコードを設定する際、example.comのサブドメインmail.example.comに対して設定する場合でも、基本的な設定の原則は同じです。ただし、DMARCレコードの名前は少し違います。

  手順: DMARCレコードの設定
  example.comの場合
  ドメイン全体に対してDMARCレコードを設定する場合、次のようにします。

  Type: TXT
  Name: _dmarc
  Content: v=DMARC1; p=none;
  mail.example.comの場合
  サブドメインに対してDMARCレコードを設定する場合、名前フィールドにサブドメインを含めます。

  Type: TXT
  Name: _dmarc.mail
  Content: v=DMARC1; p=none;
  ```
