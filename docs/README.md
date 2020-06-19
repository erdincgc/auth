Installation
---

Install using composer

    composer require jasny/auth

Usage
---

`Auth` is a composition class. It takes an _authz_, _storage_, and optionally a _confirmation_ service.

```php
use Jasny\Auth\Auth;
use Jasny\Auth\Authz\Levels;

$levels = new Levels(['user' => 1, 'moderator' => 10, 'admin' => 100]);
$auth = new Auth($levels, new AuthStorage());

session_start();
$auth->initialize();

// Later...
if (!$auth->is('admin')) {
    http_response_code(403);
    echo "Access denied";
    exit();
}
```

The `Auth` service isn't usable until it's initialized. This should be done after the session is started.

```php
session_start();
$auth->initialize();
```

Documentation
---

* [Setup](docs/setup.md)
* [Authentication](docs/authentication.md)
* [Context](docs/context.md)
* [Authorization](docs/authorization.md)
* [Sessions](docs/sessions.md)
* [Middleware](docs/middleware.md) (for access control)
* [Multi-factor authentication](docs/mfa.md)
* [Confirmation](docs/confirmation.md) (eg. forgot password)
* [Logging](docs/logging.md)
