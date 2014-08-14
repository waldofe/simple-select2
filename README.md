simple-select2
==============

A simple select2 JS initializer

# How to use it




Using simple-form and slim:

### Slim view:

```ruby
  = simple_form_for @user do |t|
    = t.hidden_field :id, class: 'select2-user-name'

```

### Javascript:

```
  Select2.initialize({
    elem: $(".select2-user-name"),
    attribute_name: 'name',
    placeholder: "Type the user name",
    ajax_url: "/app/get_users_by_name"
  });
```

#### Make sure your controller responds to the 'attribute_name' param, your Rails controller could be something like:

```
  def get_users_by_name
    teams = Team.where('name ILIKE(?)', "%#{params[:name]}%")

    users_hash = users.map { |t| { id: t.id, name: t.name } }

    render json: users_hash
  end
```

