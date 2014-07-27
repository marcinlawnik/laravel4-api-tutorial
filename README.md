#Laravel 4 API Tutorial

Tutorial to show how to build an OAuth API with Laravel and dingo/api package.

    `Copypasta` sections are present after each step to speed things up

##Prequisites

  * Working internet connection
  * Basic knowledge of composer and laravel
  * [Postman](http://www.getpostman.com/) installed


##Chapter 0 - Adding packages/composer stuff

- First let's name our app and describe what it does.
We'll do that by filling "name", "description" and "keywords" tags in
composer.json.

#####Copypasta

    //DIY or leave "as is" if you're lazy,
    //but just do it for the sake of future self



- To build our api we're going to use the following packages:


    dingo/api A package that simplifies the API development process.
    fzaninotto/faker A fake data generator to give our API something to serve
    lucadegasperi/oauth2-server-laravel OAuth stuff

Additionally, for development purposes other packages were used, listed in the
"require-dev" section. To omit the installation of those, use "--no-dev" switch
while doing either

    composer update
    //or
    composer install

It is recommended to use `install` over `update` to avoid installing newer
versions that weren't desired.

    barryvdh/laravel-ide-helper This package automatically generates phpdoc
    that is understandable by your IDE and enables automatic completion. I also
    added commands to `scripts` section to automatically run the package on
    `composer install` and `composer update`

- Add required service providers and aliases to `app/config/app.php`

#####Copypasta

    //Providers
    [
        'Dingo\Api\ApiServiceProvider',
        'LucaDegasperi\OAuth2Server\OAuth2ServerServiceProvider',
        //Remove following if you're not using the ide-helper
        'Barryvdh\LaravelIdeHelper\IdeHelperServiceProvider',
    ]
    //Aliases
    [
        'API' => 'Dingo\Api\Facades\API',
        'Controller' => 'Dingo\Api\Routing\Controller',
        'AuthorizationServer' => 'LucaDegasperi\OAuth2Server\Facades\AuthorizationServerFacade',
        'ResourceServer' => 'LucaDegasperi\OAuth2Server\Facades\ResourceServerFacade',
    ]
    //Comment out the `Controller` alias provided by Laravel as such:
    [
    	//'Controller'        => 'Illuminate\Routing\Controller',
    ]



- Configure your database in `app/config/database.php`

#####Copypasta

    //DIY or be lazy like me

    [
    'default' => 'sqlite',
    ]



- Run `composer install` to download the dependencies. A `composer.lock` file
is created that limits installation to specific versions of our packages.

#####Copypasta

    composer install



- Publish configuration files for packages.

#####Copypasta

    php artisan config:publish dingo/api
    php artisan config:publish lucadegasperi/oauth2-server-laravel



- Configure the `vendor` of API in `app/config/packages/dingo/api/config.php`

#####Copypasta

    [
        'vendor' => 'DIY',
    ]



- Run migrations for packages

#####Copypasta

    php artisan migrate --package="lucadegasperi/oauth2-server-laravel"