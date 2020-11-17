---
layout: default
title: DB Migration
parent: Rails
nav_order: 1
---

# Rails DB Migrations Cheatsheet

---

Column data types

```rb
# Standard
:binary
:boolean
:date
:datetime
:decimal
:float
:integer
:bigint
:primary_key
:references
:string
:text
:time
:timestamp

# Extra native data types for Postgres:
:hstore
:json / :jsonb
:array
:cidr_address
:ip_address
:mac_address

# and more
# @see http://stackoverflow.com/q/17918117
```

---

Change existing table

```rb
add_column :products, :price, :decimal, precision: 5, scale: 2
change_column :products, :quantity, :integer
# change column type from string to integer with Postgres
change_column :products, :price, 'integer USING CAST(price AS integer)'
remove_column :products, :photo, :string
rename_column :products, :image, :photo
change_column_default :advertisements, :enable, from: true, to: false
drop_table :products
```

---

Apply `bulk: true` when changing multiple columns in an existing table

```rb
# before
def up
  add_column :table, :useful_foreign_key, :integer
  add_index  :table, :useful_foreign_key
  add_column :table, :summary, :string
end

# after
def up
  change_table :table, bulk: true do |t|
    t.integer :useful_foreign_key
    t.index   :useful_foreign_key
    t.string  :summary
  end
end
```

---

Indexes

```rb
add_index :products, :category_id
add_index :users, :email, unique: true
# partial index with Postgres
add_index :users, :is_active, where: "is_active = true"

remove_index :products, :category_id
```

---

Migrate and Rollback

```sh
# Rails 3/4
rake db:migrate
rake db:rollback

# Rails 5+
rails db:migrate
rails db:rollback

# migrate/rollback a specific version
rails db:migrate VERSION=version
rails db:rollback VERSION=version

# rollback several migrations
rails db:rollback STEP=3

# rollback and rerun migrations
rails db:migrate:redo STEP=3
```

---

Reset PK sequence for Postgres:

```rb
# single table
ActiveRecord::Base.connection.reset_pk_sequence!(table_name)

# all tables
ActiveRecord::Base.connection.tables.each do |t|
  ActiveRecord::Base.connection.reset_pk_sequence!(t)
end
```
