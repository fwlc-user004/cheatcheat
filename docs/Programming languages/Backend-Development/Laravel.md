# Laravel Cheat Sheet

## 📌 Introduction
Laravel is a PHP framework designed for building modern web applications with elegant syntax.

---

## 🚀 Installation & Setup
### Install Laravel via Composer
```sh
composer create-project --prefer-dist laravel/laravel my-laravel-app
cd my-laravel-app
php artisan serve
```

### Environment Configuration
Copy `.env.example` to `.env` and update database credentials:
```sh
cp .env.example .env
php artisan key:generate
```

---

## 🏗️ Project Structure
```plaintext
my-laravel-app/
 ├── app/
 ├── bootstrap/
 ├── config/
 ├── database/
 ├── public/
 ├── resources/
 ├── routes/
 ├── storage/
 ├── tests/
 ├── .env
 ├── artisan
 ├── composer.json
```

---

## 🔹 Artisan Commands
```sh
php artisan serve       # Start development server
php artisan route:list  # Show all routes
php artisan migrate     # Run migrations
php artisan make:model Post -m  # Create a model with migration
```

---

## 🔹 Routing
Define routes in `routes/web.php`:
```php
use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    return view('welcome');
});

Route::get('/about', [AboutController::class, 'index']);
```

---

## 🔹 Controllers
### Generate Controller
```sh
php artisan make:controller PageController
```

### Define Methods
```php
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class PageController extends Controller
{
    public function about() {
        return view('about');
    }
}
```

---

## 🔹 Views (Blade Templates)
### Create a Blade Template `resources/views/layouts/app.blade.php`
```html
<!DOCTYPE html>
<html>
<head>
    <title>@yield('title')</title>
</head>
<body>
    @yield('content')
</body>
</html>
```

### Extend Layout in `resources/views/home.blade.php`
```html
@extends('layouts.app')

@section('title', 'Home')

@section('content')
    <h1>Welcome to Laravel</h1>
@endsection
```

---

## 🔹 Database & Eloquent
### Migration
```sh
php artisan make:migration create_posts_table
```
```php
Schema::create('posts', function (Blueprint $table) {
    $table->id();
    $table->string('title');
    $table->text('content');
    $table->timestamps();
});
```

### Model
```php
namespace App\Models;
use Illuminate\Database\Eloquent\Model;

class Post extends Model {
    protected $fillable = ['title', 'content'];
}
```

### Querying Data
```php
$posts = Post::all();
$singlePost = Post::find(1);
Post::create(['title' => 'Laravel', 'content' => 'Awesome!']);
```

---

## 🔹 Authentication
### Install Laravel Breeze
```sh
composer require laravel/breeze --dev
php artisan breeze:install
php artisan migrate
npm install && npm run dev
```

### Routes for Authentication
```php
use Illuminate\Support\Facades\Auth;
Route::get('/dashboard', function () {
    return view('dashboard');
})->middleware(['auth']);
Auth::routes();
```

---

## 🔹 Middleware
### Create Middleware
```sh
php artisan make:middleware CheckAge
```

### Define Middleware Logic in `app/Http/Middleware/CheckAge.php`
```php
public function handle($request, Closure $next)
{
    if ($request->age < 18) {
        return redirect('home');
    }
    return $next($request);
}
```

### Register Middleware in `Kernel.php`
```php
protected $routeMiddleware = [
    'checkAge' => \App\Http\Middleware\CheckAge::class,
];
```

### Use Middleware in Routes
```php
Route::get('/restricted', function () {
    return "Restricted Content";
})->middleware('checkAge');
```

---

## 🔹 API & JSON Responses
### API Route in `routes/api.php`
```php
use Illuminate\Http\Request;

Route::get('/posts', function () {
    return response()->json(Post::all());
});
```

---

## 🔹 Deployment
### Prepare for Deployment
```sh
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

### Set Permissions
```sh
chmod -R 775 storage bootstrap/cache
```


