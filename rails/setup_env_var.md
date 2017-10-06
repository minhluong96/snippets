#### Create file `config/evironments/application_dev.rb`:
```YAML
HOST: 'localhost'
PORT: '3000'
APP_SECRET: 'EXAMPLE'
GMAIL_USERNAME: 'example@gmail.com'
GMAIL_PASSWORD: 'mypassword'
```

#### In `config/evironments/development.rb`:
```Ruby
  config.before_configuration do
    env_file = File.join(Rails.root, 'config/environments', 'application_dev.yml')
    YAML.load(File.open(env_file)).each do |key, value|
      ENV[key.to_s] = value
    end if File.exists?(env_file)
  end
```