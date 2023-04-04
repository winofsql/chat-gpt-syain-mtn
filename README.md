# chat-gpt-syain-mtn

![image](https://user-images.githubusercontent.com/1501327/229726709-cffee7e6-d609-4df3-99d4-ef8cb3493bbd.png)

以下は、社員マスタ テーブルを編集するための基本的な HTML フォームです。このフォームには、社員情報を入力するためのテキストフィールドや、送信ボタンが含まれています。このフォームを PHP プログラムで処理し、データベースに情報を格納することで、マスタメンテを実現できます。

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>社員マスタ</title>
</head>
<body>
  <h1>社員マスタ</h1>
  <form action="insert.php" method="POST">
    <label for="code">社員コード:</label>
    <input type="text" id="code" name="code" maxlength="4"><br>

    <label for="name">氏名:</label>
    <input type="text" id="name" name="name" maxlength="50"><br>

    <label for="furigana">フリガナ:</label>
    <input type="text" id="furigana" name="furigana" maxlength="50"><br>

    <label for="department">所属:</label>
    <input type="text" id="department" name="department" maxlength="4"><br>

    <label for="gender">性別:</label>
    <input type="radio" id="gender" name="gender" value="1">男性
    <input type="radio" id="gender" name="gender" value="2">女性<br>

    <label for="birthdate">生年月日:</label>
    <input type="date" id="birthdate" name="birthdate"><br>

    <label for="salary">給与:</label>
    <input type="number" id="salary" name="salary"><br>

    <label for="allowance">手当:</label>
    <input type="number" id="allowance" name="allowance"><br>

    <label for="manager">管理者:</label>
    <input type="text" id="manager" name="manager" maxlength="4"><br>

    <input type="submit" value="登録">
  </form>
</body>
</html>
```
![image](https://user-images.githubusercontent.com/1501327/229726891-990ae7a8-bd6b-497a-b04b-e681d7758c39.png)

