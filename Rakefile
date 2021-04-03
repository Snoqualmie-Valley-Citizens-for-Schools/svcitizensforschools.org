require 'html-proofer'

desc "Build the site"
task build: %w[clean] do
  sh "JEKYLL_ENV=production bundle exec jekyll build --drafts"
end

desc "Clean up"
task :clean do
  sh "bundle exec jekyll clean"
end

desc "Start up the site"
task go: %w[clean] do
  sh "bundle exec jekyll serve --livereload"
end

desc "deploy to preview"
task preview_deploy: %w[build] do
  sh "netlify deploy --open"
end

desc "deploy to production"
task prod_deploy: %w[build] do
  sh "netlify deploy -p"
end

desc "Run tests"
task test: %w[build] do
  options = { :assume_extension => true, :log_level => 'error' }
  HTMLProofer.check_directory("./_site", options).run
end
