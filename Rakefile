require 'rubygems'

task :default => :build

desc "Run in developer mode"
task :dev => :check do
  system "bundle exec awestruct --dev"
end

desc "Build the site with the development profile"
task :build => :check do
  system "bundle exec awestruct -P development --force"
end

desc "Build the site and publish to github"
task :github => :check do
  system "bundle exec awestruct --deploy -P github --force"
end

desc "Build the site and publish to staging"
task :staging => :check do
  system "bundle exec awestruct --deploy -P staging --force"
end

desc "Setup or update the environment to run Awestruct"
task :setup do
  system "bundle update"
end

task :check do
  begin
    require 'bundler'
    Bundler.setup
  rescue StandardError => e
    puts "\e[31m#{e.message}\e[0m"
    puts "\e[33mRun `rake setup` to install required gems.\e[0m"
    next
  end
  Dir.mkdir('_tmp') unless Dir.exist?('_tmp')
end
