# Lartificer News

This package is a part of the Lartificer project, based on the Laravel Framework. Only to use inside a Laravel project.

## Installation
The whole project is available as [Packagist Lartificer project](https://packagist.org/packages/lartificer/news) to use with Composer.

To use the news package in your Laravel project, first add it to the `composer.json` in your project's root directory. To enable custom install paths for your Composer packages, it is also necessary to require the [composer-custom-directory-installer](https://github.com/mnsami/composer-custom-directory-installer). To seed your dummy database, use [fzaninotto/Faker](https://github.com/fzaninotto/Faker).

## How to use?
- Your Website must contain a login functionality in order to be able to login and edit/create/delete news entries
- Multi language feature: \
As there can be seen in the `NewsController` class of the news module, change the `$languages` variable to fit your needs. Add the corresponding language files in the `src/lang` directory. The files in this directory determine the displayed texts and the routes.
- Add the link to the news overview page to a page of your choice: \
`<a href="{{ trans("news::links.overview") }}">Link to the news overview page</a>`
- After you made your changes, the files have to be published like so:\
`php artisan vendor:publish --provider="vendor/lartificer/contactform/src/Lartificer/News/NewsServiceProvider" --tag="public"`
Use accordingly for your migrations. See the the `publish` methods in the `NewsServiceProvider`.

To create your database, you can use the migrations in the `src/database/migrations` folder.


### Composer
```javascript
"require": {
		"laravel/framework": "5.0.*",
		...
        "mnsami/composer-custom-directory-installer": "1.0.*",
        "lartificer/news": "dev-master"
	},
```
Make the PSR-0 namespace fit, and add the `extra` option to install the package at a custom path.
```javascript
    "autoload": {
        ...
	    "psr-0": {
		  "Lartificer\\News": "path/to/lartificer/news/src/"
		}
	},
    "extra": {
      "installer-paths": {
        "./path/to/lartificer/news/": ["lartificer/news"]
      }
    }
```

### App.php
Now you have to register the NewsServiceProvider in your `app.php` file.

```php
'providers' => [

		...
		
		/*
		 * Lartificer
		 */ 
		'Lartificer\News\NewsServiceProvider',

	],
```

## License
Copyright (c) 2015 Paul Mohr, Fabian Henkel

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
