# simonwoodside.com

## Test

    bundle exec jekyll serve --incremental --watch

## Build for deployment

    bundle exec jekyll build --incremental

## Sync to server

    rsync --verbose --itemize-changes --archive --partial --progress --delete-during _site/ simon@shrub.ca:/data/sites/swc-jekyll/

## Files

- simonwoodside.com.conf // Apache configuration file that lives in /etc/apache2/sites-enabled/
