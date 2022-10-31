# active_admin_paranoia
This gem extends ActiveAdmin so that batch restore and batch archive actions will be available in resource index page. Also 'All' and 'Archived' scope will be available for resource index page. 'All' scope will show non archived resources and 'Archived' scope will show deleted or archived resources.

# Installation
This gem assumes that you have already configured [paranoia](https://github.com/radar/paranoia) for you desire resource. Add this line to your application's Gemfile:

```ruby
gem "active_admin_paranoia" , '~> 1.0.11'

```

And then execute:

    $ bundle

# Usages

```ruby
ActiveAdmin.register Post do
  active_admin_paranoia
end
```

# Archiving (soft delete) vs Deleting (hard delete)

The "Archive" button will call `#destroy` to soft delete the resource by setting the `deleted_at` column to the current time. 
The "Delete" button will call `#really_destroy!` to hard delete the resource (by removing the records from the database).

You can disable hard deletion by removing the `:destroy` action:

```ruby
ActiveAdmin.register Post do
  active_admin_paranoia
  actions :all, except: [:destroy]
end
```
