Heroku buildpack: Vendor Binaries
=================================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for vendoring binaries into your project. It doesn't do anything else, so to actually compile your app you should use [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) to combine it with a real buildpack.

Usage
-----

    $ ls
    .vendor_binaries
    .buildpacks

    $ heroku create --stack cedar --buildpack http://github.com/dollar/heroku-buildpack-multi.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    -----> Found a .vendor_urls file
           Vendoring https://s3.amazonaws.com/my-bucket/foo.tar.gz
    ...

The buildpack will detect that your app has a `.vendor_binaries` in the root. Each line in this file will be treated as a URL pointing at a tarball to fetch and extract into your application's root directory.

