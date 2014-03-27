# jquery-lazy-images

jQuery plugin for lazy-loading of images. Why have your users download what they can't see?

[![Build Status](https://travis-ci.org/singlebrook/jquery-lazy-images.png)](https://travis-ci.org/singlebrook/jquery-lazy-images)

## Installation

### Rails 3.1 or greater (with asset pipeline *enabled*)

Add to your Gemfile: `gem 'jquery-lazy-images'`. Run `bundle install`.

The jquery.lazy-images files is now added to the asset pipeline and available for you to use.

Add `require jquery.lazy-images` to app/assets/javascripts/application.js and app/assets/stylesheets/application.css, following the existing format of those files.

### Rails 3.0 or earlier (or without asset pipeline)

You're on your own here. Sorry!

## Usage

All images rendered with image_tag will automatically be lazy-loaded.

### Images in email

Lazy-loading of images in email *really* doesn't work. We haven't thought of a performant way
to automatically make these images eager-loading, so you'll need to change your image_tag's in
your email templates to eager_image_tag's.

This **dangerous** command may help you with this:

```bash
  sed -i 's/image_tag/eager_image_tag/g' app/views/*_mailer/*
```

### Precompiling the assets

If you precompile your assets, be sure that you have a line like this in your `config/environments/production.rb` (or similar) to avoid getting a 404 on the placeholder image (grey.gif).

```ruby
config.assets.precompile += %w(*.png *.jpg *.jpeg *.gif)
```

## Development

To run the specs you must have [PhantomJS](http://phantomjs.org/) [installed](http://phantomjs.org/build.html).
If you use [homebrew](http://mxcl.github.com/homebrew/) you can run `brew install phantomjs`.

## Acknowledgements

Thanks to Mika Tuupola for creating [jquery.lazyload.js](http://www.appelsiini.net/projects/lazyload)! This gem bundles that library, and he's done most of the hard work for us.

## Contributors

* @sbleon - Initial build
* @jkonowitch - Initial build
* @bobbyw - Poltergeist testing support
* @petergoldstein - Rails 4 compatibility and Travis CI integration
