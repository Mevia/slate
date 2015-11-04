require 'middleman-gh-pages'
require 'rake/clean'

CLOBBER.include('build')

task :default => [:build]

namespace :assets do
  task :precompile do
    sh 'middleman build'
  end
end
