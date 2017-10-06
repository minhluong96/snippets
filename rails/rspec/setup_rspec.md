## Setup RSpec

* **Necessary gems for rspec**
```Gemfile
gem 'rspec-rails'
gem 'factory_girl_rails'
gem 'database_cleaner', '~> 1.5', '>= 1.5.3'
gem 'ffaker'
gem 'capybara'
gem 'shoulda-matchers', github: 'thoughtbot/shoulda-matchers'
```

* **Run `rails generate rspec:install`**


* **Add `config/initializers/generators.rb`**
```ruby
Rails.application.config.generators do |g|
    g.test_framework :rspec,
    fixture: true,
    controller_specs: true,
    view_specs: false,
    routing_spec: false,
    helper_specs: false
    g.stylesheets = false
    g.javascripts = false
    g.helper = false
    g.fixture_replacement :factory_girl, dir: 'spec/factories'
end
```
* **Add `spec/rails_helper.rb`**
```ruby
Shoulda::Matchers.configure do |config|
  config.integrate do |with|
    # Choose a test framework:
    with.test_framework :rspec
    with.test_framework :minitest
    with.test_framework :minitest_4
    with.test_framework :test_unit

    # Choose one or more libraries:
    with.library :active_record
    with.library :active_model
    with.library :action_controller
    # Or, choose the following (which implies all of the above):
    with.library :rails
  end
end
```