source "https://rubygems.org"

# GitHub Pages keeps Jekyll and its dependencies pinned for compatibility.
# See https://pages.github.com/versions/ for the current matrix.
gem "github-pages", group: :jekyll_plugins

# Ruby 3.0+ no longer bundles rexml; Jekyll still requires it.
gem "rexml"

group :jekyll_plugins do
    gem "jekyll-seo-tag"
    gem "jekyll-sitemap"
    gem "jekyll-feed"
    gem "jekyll-remote-theme"
end

# Windows and JRuby do not include zoneinfo files, so bundle the tzinfo-data gem.
platforms :mingw, :x64_mingw, :mswin, :jruby do
    gem "tzinfo", ">= 1", "< 3"
    gem "tzinfo-data"
end

# Lock http_parser.rb gem to v0.6.x on JRuby builds since newer versions don't work.
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]

# Note on Windows file watching:
#   The `wdm` gem (filesystem-watch helper for Windows) does not build on
#   Ruby >= 3.3 and is unmaintained. If you want auto-rebuilds locally on
#   Windows, use `bundle exec jekyll serve --livereload --force-polling`.
