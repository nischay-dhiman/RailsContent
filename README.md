# RailsContent


rails new advanced_auth_app
cd advanced_auth_app




----
Creating creds

bin/rails db:encryption:init




# Add Devise to your Gemfile
gem 'devise'

# Install Devise
bundle install
rails generate devise:install
rails generate devise User
rails db:migrate

rails generate devise:views

gem 'devise-two-factor'

bundle install
rails generate devise_two_factor User
rails db:migrate


------

Add

# app/controllers/application_controller.rb

  before_action :configure_permitted_parameters, if: :devise_controller?

  # ...

  protected

  def configure_permitted_parameters
    devise_parameter_sanitizer.permit(:sign_in, keys: [:otp_attempt])
  end


-----


Add-----

When My code git stuck for creds issue:


First run this command

bin/rails db:encryption:init
This will generate the following

Add this entry to the credentials of the target environment: 

active_record_encryption:
  primary_key: Q3TJUKuOUGSZmgqaD2WZ72pQdg5Rikfn
  deterministic_key: lYew1Q7BE98tDXdqytP3iwvJcu8dYulX
  key_derivation_salt: 9REysw2kZuLybtKjtJsIZHg8cTd2DyMT
Add the following config in application.rb

config.active_record.encryption.primary_key = ENV['ACTIVE_RECORD_ENCRYPTION_PRIMARY_KEY']
config.active_record.encryption.deterministic_key = ENV['ACTIVE_RECORD_ENCRYPTION_DETERMINISTIC_KEY']
config.active_record.encryption.key_derivation_salt = ENV['ACTIVE_RECORD_ENCRYPTION_KEY_DERIVATION_SALT']


--------

Theme addition
https://matthieubertrand5.medium.com/how-to-use-a-bootstrap-theme-in-a-ruby-on-rails-project-2a24f01c6f44


