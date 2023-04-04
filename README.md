# chat-gpt-syain-mtn

![image](https://user-images.githubusercontent.com/1501327/229726709-cffee7e6-d609-4df3-99d4-ef8cb3493bbd.png)

以下は、社員マスタ テーブルを編集するための基本的な HTML フォームです。\
このフォームには、社員情報を入力するためのテキストフィールドや、送信ボタンが含まれています。\
このフォームを PHP プログラムで処理し、データベースに情報を格納することで、マスタメンテを実現できます。

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

このフォームを送信すると、insert.php ファイルにデータが送信されます。以下は、insert.php ファイルの例です。このファイルでは、POST パラメータからフォームに入力されたデータを取得し、社員マスタ テーブルに挿入します。

```php
<?php
// データベースに接続するための情報
$host = 'localhost';
$dbname = 'mydatabase';
$user = 'myuser';
$password = 'mypassword';

// データベースに接続
$dbh = new PDO("mysql:host=$host;dbname=$dbname", $user, $password);

// 文字コードを設定
$dbh->query('SET NAMES utf8');

// フォームから送信されたデータ
// フォームから送信されたデータを取得
$code = $_POST['code'];
$name = $_POST['name'];
$furigana = $_POST['furigana'];
$department = $_POST['department'];
$gender = $_POST['gender'];
$birthdate = $_POST['birthdate'];
$salary = $_POST['salary'];
$allowance = $_POST['allowance'];
$manager = $_POST['manager'];

// SQL文を作成して実行
$sql = "INSERT INTO `社員マスタ` (`社員コード`, `氏名`, `フリガナ`, `所属`, `性別`, `作成日`, `更新日`, `給与`, `手当`, `管理者`, `生年月日`) VALUES (?, ?, ?, ?, ?, NOW(), NOW(), ?, ?, ?, ?)";
$stmt = $dbh->prepare($sql);
$stmt->bindValue(1, $code, PDO::PARAM_STR);
$stmt->bindValue(2, $name, PDO::PARAM_STR);
$stmt->bindValue(3, $furigana, PDO::PARAM_STR);
$stmt->bindValue(4, $department, PDO::PARAM_STR);
$stmt->bindValue(5, $gender, PDO::PARAM_INT);
$stmt->bindValue(6, $salary, PDO::PARAM_INT);
$stmt->bindValue(7, $allowance, PDO::PARAM_INT);
$stmt->bindValue(8, $manager, PDO::PARAM_STR);
$stmt->bindValue(9, $birthdate, PDO::PARAM_STR);
$stmt->execute();

// データベースから切断
$dbh = null;

// 完了メッセージを表示
echo "データの登録が完了しました。";
```

![image](https://user-images.githubusercontent.com/1501327/229727432-dd20ab1e-d56a-4a75-9d19-a2f656fa0b56.png)
