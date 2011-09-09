require 'rake'
require 'rake/testtask'
require 'rbconfig'
include Config

task :clean do
  Dir['*.gem'].each{ |f| File.delete(f) }
end

namespace :gem do
  desc 'Create the win32-job gem'
  task :create do
    spec = eval(IO.read('win32-job.gemspec'))
    Gem::Builder.new(spec).build
  end

  desc 'Install the win32-job gem'
  task :install => [:gem] do
    file = Dir["*.gem"].first
    sh "gem install #{file}"
  end
end

Rake::TestTask.new do |t|
  t.verbose = true
  t.warning = true
end

task :default => :test
