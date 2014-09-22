#Problem with Rails 3.2 and Ruby 2.2?
Don't know if Rails 3.2 and Ruby 2.2 are intended to be compatible or not, but
if they are then I'm seeing a problem:

```
cd ruby-2.2_rails3.2
bundle install
bundle exec rake db:migrate

rails runner "Blog.exists?(1)"
```

When run on Ruby 2.1, the runner script executes happily with no results

When run on Ruby 2.2, an exception is raised:
```
undefined method `group_values=' for []:ActiveRecord::Relation (NoMethodError)
```

Full stack trace:
```
/Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/railties-3.2.19/lib/rails/commands/runner.rb:54:in `eval':
  undefined method `group_values=' for []:ActiveRecord::Relation (NoMethodError)
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/activerecord-3.2.19/lib/active_record/relation/spawn_methods.rb:88:in `block in except'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/activerecord-3.2.19/lib/active_record/relation/spawn_methods.rb:87:in `each'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/activerecord-3.2.19/lib/active_record/relation/spawn_methods.rb:87:in `except'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/activerecord-3.2.19/lib/active_record/relation/finder_methods.rb:231:in `construct_relation_for_association_find'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/activerecord-3.2.19/lib/active_record/relation/finder_methods.rb:192:in `exists?'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/activerecord-3.2.19/lib/active_record/querying.rb:5:in `exists?'
from (eval):1:in `<top (required)>'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/railties-3.2.19/lib/rails/commands/runner.rb:54:in `eval'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/railties-3.2.19/lib/rails/commands/runner.rb:54:in `<top (required)>'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/railties-3.2.19/lib/rails/commands.rb:64:in `require'
from /Users/jclark/.rbenv/versions/2.2.0-preview1/lib/ruby/gems/2.2.0/gems/railties-3.2.19/lib/rails/commands.rb:64:in `<top (required)>'
from script/rails:6:in `require'
from script/rails:6:in `<main>'
```
