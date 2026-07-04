source "https://rubygems.org"

# Match the Jekyll version GitHub Pages runs (see https://pages.github.com/versions/).
# We pin gems directly instead of using the github-pages meta-gem so CI resolves
# a modern Jekyll on Ruby 3.3 without stale transitive dependencies.
gem "jekyll", "~> 3.10"
gem "kramdown-parser-gfm"

group :jekyll_plugins do
    gem "jekyll-seo-tag"
    gem "jekyll-sitemap"
    gem "jekyll-feed"
    gem "jekyll-remote-theme"
end

# Ruby 3.0+ no longer bundles these stdlib gems; Jekyll still needs them.
gem "rexml"
gem "webrick"
gem "base64"
gem "bigdecimal"
gem "csv"

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
