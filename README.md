# Automated testing

A presentation on automated testing.

# Use

1. Open https://mparker17.github.io/talk--software-testing-overview/ in a vaguely modern web browser.
2. Choose either "Slides" or "Speaker notes"

Note this loads [reveal.js](https://github.com/hakimel/reveal.js) on [CloudFlare's cdnjs](https://cdnjs.com/about), so you have to be connected to the internet when you load the slideshow for the first time. [Technical information is available on cdnjs's page about reveal.js](https://cdnjs.com/libraries/reveal.js).

# Develop

1. Install a [Ruby](https://www.ruby-lang.org) version mananger.

    (I installed [rbenv](https://github.com/rbenv/rbenv) with my computer's package manager).
2. Clone this repo, use your Ruby version manager to install the correct version of Ruby & Rubygems, use Rubygems to install the [Bundler package manager](https://bundler.io/), and use Bundler to install dependencies needed to compile this presentation:

        $ git clone --recursive https://github.com/mparker17/jekyll-theme--revealjs.git
        $ cd jekyll-theme--revealjs/
        $ rbenv install
        $ gem install bundler
        $ bundle install

3. Run Jekyll's local development server:

        $ bundle exec jekyll serve

