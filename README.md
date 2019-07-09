# Galleries
A simple package of galleries to attach on a model

## Installation

Add to composer.json

```
  "require": {
    "unscode/galleries": "1.0.*"
  }
```

ou

```js
  composer require unscode/galleries
```

## Service Provider

Open `config/app.php` then add

`Unscode\Galleries\Providers\GalleriesServiceProvider::class`

## Facades

Open `config/app.php` then add

`'Gallery'   => Unscode\Galleries\Facades\Gallery::class`

## Publishing the files

```
$ php artisan vendor:publish --provider="Unscode\Galleries\Providers\GalleriesServiceProvider" --tag="assets"
$ php artisan vendor:publish --provider="Unscode\Galleries\Providers\GalleriesServiceProvider" --tag="config"
```

## Running migrations

```
$ composer dump-autoload
$ php artisan migrate
```

## Merge css/javascript into your gulpfile.js

```
...
.styles([
...
	'resources/assets/css/dropzonejs.css',
...
	],
	'public/assets/css/admin.css',
	'./')
...
.scripts([
...
	'resources/assets/js/dropzone.min.js',
	'resources/assets/js/jquery-ui.sortable.min.js',
...
    'resources/assets/js/galleries-start.js'
...
	],
    'public/assets/js/admin.js',
    './')
...    
```

## Attaching the gallery to your model

```
use Unscode\Galleries\GalleriableInterface;
use Unscode\Galleries\GalleriableTrait;

class Post extends Model implements GalleriableInterface
{
    use GalleriableTrait;
```

## Load the grid in your panel

```
{!! Gallery::form($post, [customGalleryName]) !!}
```

## Lists all images from a model

```
Post::first()->galleries([customGalleryName])->images();
```

## If you want to return the default gallery images

```
Post::first()->gallery->images();
```
