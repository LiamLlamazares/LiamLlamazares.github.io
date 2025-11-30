source 'https://rubygems.org'

gem 'jekyll'

# Core plugins that directly affect site building
    gem 'jekyll-archives-v2'
    gem 'jekyll-email-protect'
    gem 'jekyll-feed'
    gem 'jekyll-get-json'
    
    unless Gem.win_platform?
      gem 'jekyll-imagemagick'
      gem 'jekyll-jupyter-notebook'
      gem 'jekyll-minifier'
      gem 'jekyll-terser', :git => "https://github.com/RobertoJBeltran/jekyll-terser.git"
    end

    gem 'jekyll-link-attributes'
    gem 'jekyll-paginate-v2'
    gem 'jekyll-regex-replace'
    gem 'jekyll-scholar'
    gem 'jekyll-sitemap'
    gem 'jekyll-tabs'
    gem 'jekyll-toc'
    gem 'jekyll-twitter-plugin'
    gem 'jemoji'

    gem 'classifier-reborn'  # used for content categorization during the build


# Gems for development or external data fetching (outside :jekyll_plugins)
group :other_plugins do
    gem 'css_parser'
    gem 'feedjira'
    gem 'httparty'
    gem 'observer'       # used by jekyll-scholar
    gem 'ostruct'        # used by jekyll-twitter-plugin
    # gem 'terser'         # used by jekyll-terser
    # gem 'unicode_utils' -- should be already installed by jekyll
    gem 'webrick'
    gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
    gem 'wdm', '>= 0.1.0' if Gem.win_platform?
end
