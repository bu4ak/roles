## Very simple package with roles and middleware

#### Installation:
```bash
 composer require bu4ak/roles
 php artisan vendor:publish --provider="Bu4ak\Roles\RolesServiceProvider"
 #(modify migration if you need)
 php artisan migrate 
 add 'HasRoles' trait to 'User' model
```
#### Usage example:
set `admin` (`manager` or `user`) role to user:
```php
$user = User::first();
$user->assignRole(RoleType::ADMIN);
```
and add middleware `admin` (`manager` or `user`) to route:
```php
Route::get('/', function () {
    return view('welcome');
})->middleware('admin');
```
#### Also:
You can check user's role
```php
$user->isAdmin();
$user->isManager();
$user->isUser();

```
and select all users with a specific role
```php
User::admins()->get();
User::managers()->get();
User::users()->get();
```
