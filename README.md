## DBが作成済みかつデータも挿入済み状態でカラムを追加

1. maigrationでデータベース作成済み、データも1件ほど挿入済み
2. models.pyでNotNull制約のあるカラムを追加
3. makemigrationsでマイグレーションファイルを作成
4. エラーが表示される
```python
It is impossible to change a nullable field 'stock' on supplies to non-nullable without providing a default. This is because the database needs something to populate existing rows.
Please select a fix:
 1) Provide a one-off default now (will be set on all existing rows with a null value for this column)
 2) Ignore for now. Existing rows that contain NULL values will have to be handled manually, for example with a RunPython or RunSQL operation.
 3) Quit and manually define a default value in models.py.
Select an option: 3
```
5. 既存のレコードについてNotNullのカラムにデータを入れられないので、デフォルト値を設定してマイグレーションファイルを編集
```python
stock = models.IntegerField(default=0)
```
6. マイグレーションファイルを編集したら、makemigrationsでマイグレーションファイルを作成
```python
python manage.py makemigrations
```





