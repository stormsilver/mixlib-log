require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "mixlib-log"
    gem.summary = "A gem that provides a simple mixin for log functionality"
    gem.email = "info@opscode.com"
    gem.homepage = "http://www.opscode.com"
    gem.authors = ["Opscode, Inc."]

    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
    gem.files = [
      "LICENSE",
      "NOTICE",
      "Rakefile",
      "README.rdoc",
      "VERSION.yml"
    ]
    gem.files.include %w{ features/**/* lib/**/* spec/**/* }
  end
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install gemcutter jeweler (installs jeweler from gemcutter)"
end

require 'spec/rake/spectask'
Spec::Rake::SpecTask.new(:spec) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.spec_opts = ['--options', "\"#{File.dirname(__FILE__)}/spec/spec.opts\""]
  spec.spec_files = FileList['spec/**/*_spec.rb']
end

Spec::Rake::SpecTask.new(:rcov) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

begin
  require 'cucumber/rake/task'
  Cucumber::Rake::Task.new(:features)
rescue LoadError
  task :features do
    abort "Cucumber is not available. In order to run features, you must: sudo gem install cucumber"
  end
end

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION.yml')
    config = YAML.load(File.read('VERSION.yml'))
    version = "#{config[:major]}.#{config[:minor]}.#{config[:patch]}"
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "mixlib-log #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

