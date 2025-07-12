# Common Laravel Bugs and Errors

Here is a list of common bugs and errors encountered in Laravel development, presented in a professional manner:

1.  **N+1 Query Problem:** Occurs when an application makes a separate database query for each item in a collection, leading to performance bottlenecks. Typically resolved using Eloquent's eager loading (`with()` method).

2.  **Mass Assignment Vulnerabilities:** Arises when an Eloquent model's attributes are updated en masse without proper protection, potentially allowing malicious users to modify unintended fields. Prevented by using `$fillable` or `$guarded` properties in models.

3.  **CSRF Token Mismatch:** Happens when the Cross-Site Request Forgery token is missing or invalid in a POST, PUT, PATCH, or DELETE request. Ensure the `@csrf` directive is in forms or the token is included in AJAX request headers.

4.  **`Target class [ControllerName] does not exist.`:** This error usually indicates a typo in the controller name in the route definition, a namespace issue, or that the controller file hasn't been created or correctly named.

5.  **`View [view.name] not found.`:** Laravel cannot locate the specified Blade template file. Check for typos in the view name, ensure the file exists in the `resources/views` directory with the correct path, and use dot notation correctly.

6.  **`Method [methodName] does not exist on this collection instance.`:** Attempting to call a method on a collection that is intended for a single model instance, or vice-versa. Common with query builder results.

7.  **Facade Class Not Found / `Non-static method should not be called statically` (when using Facades incorrectly):** Often due to missing `use` statements for the Facade or incorrect namespace. Ensure Facades are correctly imported.

8.  **Environment Configuration Issues (.env file):** Incorrect database credentials, mail driver settings, or app keys in the `.env` file can lead to various errors. Always ensure `.env` is correctly set up and run `php artisan config:cache` after changes (and `config:clear` during development).

9.  **Migration Errors (`Class '...' not found`, `Base table or view not found`):** Can occur if migration files are deleted after running, class names in migrations are incorrect, or foreign key constraints are violated. Running `composer dump-autoload` can sometimes help with class not found issues.

10. **Route Caching Issues:** After adding or modifying routes, if route caching is enabled (`php artisan route:cache`), changes might not reflect until the cache is cleared (`php artisan route:clear`).

11. **Session Issues (e.g., `Session store not set on request.`):** Often related to middleware configuration, file permissions in the `storage/framework/sessions` directory, or incorrect session driver settings.

12. **Composer Dependency Conflicts / Outdated Packages:** Can lead to unexpected behavior or errors. Regularly run `composer update` (with caution in production) and resolve conflicts shown by Composer.

13. **Incorrect File/Folder Permissions:** Web server needs write access to `storage` and `bootstrap/cache` directories. Incorrect permissions can cause a wide range of errors, including failures to write logs, cache, or session files.

14. **`Trying to get property '...' of non-object`:** Accessing a property or method on a variable that is `null` or not an object. Common when a database query returns no results and this isn't handled.

15. **AJAX Errors (419, 500):** 419 errors are often CSRF token mismatches in AJAX requests. 500 errors are general server errors; check Laravel logs (`storage/logs/laravel.log`) and browser console for more details.

16. **Mail Configuration and Sending Failures:** Incorrect mail driver, credentials, or issues with the mail server (e.g., Gmail blocking less secure apps) can prevent emails from being sent.

17. **Task Scheduling Not Running:** Cron job for Laravel's scheduler (`* * * * * cd /path-to-your-project && php artisan schedule:run >> /dev/null 2>&1`) is not set up correctly on the server.

18. **Queue Worker Issues:** Jobs failing silently or not being processed. Check queue worker logs, ensure the worker is running (`php artisan queue:work`), and that queue connection settings are correct.

19. **API Authentication/Authorization Errors:** Incorrect token handling, middleware setup (e.g., Passport, Sanctum), or guard configuration leading to `Unauthenticated` or `Forbidden` responses.

20. **`PDOException` / Database Connection Errors:** Issues with database credentials, server availability, incorrect database host, or firewall restrictions preventing the application from connecting to the database.
