[ActiveRecord::AttributeMethods::Dirtyモジュール](https://github.com/rails/rails/blob/v6.0.2.2/activerecord/lib/active_record/attribute_methods/dirty.rb)
に定義されているメソッドのたち

| method | comment |
| --- | --- |
|saved_change_to_attirbute?| 変更があればtrueを返す。 |
|saved_change_to_attribute| attributeの変化を返す。　|
|attribute_before_last_save| save前のvalueを返す。 |
|saved_changes?| 最後にsaveが呼ばれたときに変更があればtrueを返す。 |
|saved_changes| すべての変更をhashで返す。 |
|will_save_change_to_attribute?| save前の変更される予定の値があればtrueを返す。|
|attribute_change_to_be_saved| 変更がある場合に、元のvalueと新規のvalueを配列で返す。|
|attribute_in_database| saveされた元のvalueを返す。|
|has_changes_to_save?| 次にsaveが呼ばれる時に変更があればtrueを返す。|
|changes_to_save| 次にsaveが呼ばれる時に存在するすべての変更をhashで返す。|
|changed_attribute_names_to_save| 次にsaveされる予定のattributeの名前を返す。|
| attributes_in_database| db内の元のkey(attribute)とvalueをhashで返す |
  

- saved_change_to_attirbute?

```ruby
pry(main)> user.role = 'admin'
=> "admin"
pry(main)> user.saved_change_to_role?
=> false
pry(main)> user.save
=> true
pry(main)> user.saved_change_to_role?
=> true
```

- saved_change_to_attribute


```ruby
pry(main)> user.saved_change_to_role
=> ["manager", "admin"]
```

- attribute_before_last_save

```ruby
pry(main)> user.role_before_last_save
=> "manager"
```

- saved_changes?

```ruby
pry(main)> user.saved_changes?
=> true
```

- saved_changes

```ruby
pry(main)> user.saved_changes
=> {"role"=>["manager", "admin"],
 "updated_at"=>[Wed, 09 Jun 2021 03:06:29 UTC +00:00, Wed, 09 Jun 2021 14:07:54 UTC +00:00],
 "edited_at"=>[Wed, 09 Jun 2021 03:06:29 UTC +00:00, Wed, 09 Jun 2021 14:07:53 UTC +00:00]}
```


- will_save_change_to_attribute?

```ruby
pry(main)> user.will_save_change_to_role?
=> nil
pry(main)> user.role = 'manager'
=> "manager"
pry(main)> user.will_save_change_to_role?
=> true
```

- attribute_change_to_be_saved

```ruby
pry(main)> user.role_change_to_be_saved
=> ["admin", "manager"]
```

- attribute_in_database

```ruby
pry(main)> user.role_in_database
=> "manager"
```

- has_changes_to_save?

```ruby
pry(main)> user.has_changes_to_save?
=> false
pry(main)> user.role = 'admin'
=> "admin"
pry(main)> user.has_changes_to_save?
=> true
pry(main)> user.save
=> true
pry(main)> user.has_changes_to_save?
=> false
```

- changes_to_save

```ruby
pry(main)> user.role = 'manager'
=> "manager"
pry(main)> user.changes_to_save
=> {"role"=>["admin", "manager"]}
pry(main)> user.save
=> true
pry(main)> user.changes_to_save
=> {}
```

- changed_attribute_names_to_save

```ruby
pry(main)> user.role = 'admin'
=> "admin"
pry(main)> user.changed_attribute_names_to_save
=> ["role"]
pry(main)> user.save
=> true
[68] pry(main)> user.changed_attribute_names_to_save
=> []
```

- attributes_in_database

```ruby
pry(main)> user.name = 'test'
=> "test"
pry(main)> user.role = 'manager'
=> "manager"
pry(main)> user.attributes_in_database
=> {"name"=>"afriinc_manager", "role"=>"admin"}
```
