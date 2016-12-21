require 'rake/clean'

JS_FILES = FileList['js/**/*.js']
POLYFILLS = FileList['polyfills/*.js']
ROLLUP_CONFIG = '.rollup.config.js'

TARGETS = %w(build/application.js build/polyfills.js)
CLEAN.concat(TARGETS)

task default: TARGETS

desc 'Install dependencies'
task :deps do
    # install deps here
end

desc 'Run tests'
task :test do
    # sh 'standard', 'js/**/*.js'
end

desc 'Builds the main bundle'
file 'build/application.js' => JS_FILES do |t|
    mkdir_p 'build'
    sh 'rollup', '-c', ROLLUP_CONFIG, '-o', t.name, 'js/application.js'
end

desc 'Builds the polyfills bundle'
file 'build/polyfills.js' => POLYFILLS do |t|
    mkdir_p 'build'
    sh 'uglifyjs', '-o', t.name, *t.prerequisites
end
