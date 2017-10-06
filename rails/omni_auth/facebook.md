# Rails 5 with Facebook
1. **Setup**

    a. Gemfile
    ```ruby
    gem 'devise'
    gem 'omniauth-facebook'
    gem 'koala'
    ```

    b. Generate basic Model
    ```
    rails g model User name:string uid:string token:string
    ```

    c. Config devise `config/initializers/devise.rb`
    ```ruby
      config.omniauth :facebook, ENV['FB_APP_ID'], ENV['FB_APP_SECRET'], scope: 'email,user_likes', info_fields: 'email,name'
    ```

    d. Config devise model to use omniauth-facebook
    ```ruby
      devise :omniauthable, :omniauth_providers => [:facebook]
    ```

    e. Add facebook callback to controller `config/routes.rb`
    ```ruby
    devise_for :users, controllers: { omniauth_callbacks: 'auth/callbacks' }
    ```

    f. Config devise `config/initializers/devise.rb`
    ```ruby
    Koala.configure do |config|
      config.app_access_token = ENV['FB_APP_ACCESS_TOKEN']
      config.app_id = ENV['FB_APP_ID']
      config.app_secret = ENV['FB_APP_SECRET']
    end
    ```
