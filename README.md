#Laravel 4 API Tutorial

This tutorial shows how to build an API with Laravel and dingo/api package.

    The tutorial is structured in such a way, that every step is also a commit
    in this repository. Each chapter will have associated changes commited
    alogside it. I recommend browsing it using GitHub's diff feature to see
    what was changed in each step.

##Prequisites

  * Working internet connection
  * Basic knowledge of composer and laravel


##Chapter 0 - Adding packages and configuring composer

1.
First let's name our app and describe what it does.
We'll do that by filling "name", "description" and "keywords" tags in
composer.json.

2.
To build our api we're going to use the following packages:
  * dingo/api A package that simplifies the API development process.
  * fzaninotto/faker A fake data generator to give our API something to serve

Additionally, for development purposes other packages were used, listed in the
"require-dev" section. To omit the installation of those, use "--no-dev" switch
while doing either

    composer update
    #or
    composer install

It is recommended to use `install` over `update` to avoid installing newer
versions that weren't desired.

    * barryvdh/laravel-ide-helper This package automatically generates phpdoc
    that is understandable by your IDE and enables automatic completion. I also
    added commands to `scripts` section to automatically run the package on
    `composer install` and `composer update`