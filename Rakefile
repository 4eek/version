$: << 'lib'

require 'rake/version_task'

require 'rubygems'
require 'rake/gempackagetask'
require 'rake/rdoctask'
require 'spec/rake/spectask'

spec = Gem::Specification.new do |s|
  s.name    = 'version'
  s.version = Version.current
  s.summary = 'simple version-number encapsulation'
  
  s.author  = 'Stephen Touset'
  s.email   = 'stephen@touset.org'
  
  s.files   = Dir['[A-Z]*', 'bin/*', 'lib/**/*.rb', 'spec/**/*']
  
  s.extra_rdoc_files = Dir['*.rdoc']
  s.rdoc_options = %w{ --main README.rdoc }
  
  s.bindir      = 'bin'
  s.executables = ['version']
  
  s.add_development_dependency 'rspec'
end

Rake::GemPackageTask.new(spec) do |gem|
  gem.need_tar = true
end

Rake::RDocTask.new do |doc|
  doc.title    = "version #{Version.current}"
  doc.rdoc_dir = 'doc'
  doc.main     = 'README.rdoc'
  doc.rdoc_files.include('*.rdoc')
  doc.rdoc_files.include('lib/**/*.rb')
end

Spec::Rake::SpecTask.new(:spec) do |task|
  task.spec_files = FileList['spec/**/*_spec.rb']
end

Rake::VersionTask.new do |v|
  v.with_git_tag = true
  v.with_gemspec = spec
end

task :default => :spec
