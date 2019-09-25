1. Install XAMPP
2. Install Composer
3. Create project using command : composer create-project symfony/skeleton symphart
4. Modify httpd-vhosts.conf(path : xampp > apahce > conf > extra > httpd-vhosts.conf)
<VirtualHost *:80>
    DocumentRoot "C:/xampp/htdocs/symphart/public"
    ServerName symphart.test
</VirtualHost>
5. Add "127.0.0.1	symphart.test" into hosts file.
6. Add .htaccess on Public folder
 <IfModule mod_rewrite.c>
    RewriteEngine On

    # Determine the RewriteBase automatically and set it as environment variable.
    RewriteCond %{REQUEST_URI}::$1 ^(/.+)/(.*)::\2$
    RewriteRule ^(.*) - [E=BASE:%1]

    # If the requested filename exists, simply serve it.
    # We only want to let Apache serve files and not directories.
    RewriteCond %{REQUEST_FILENAME} -f
    RewriteRule .? - [L]

    # Rewrite all other queries to the front controller.
    RewriteRule .? %{ENV:BASE}/index.php [L]
</IfModule>
7. composer require annotations(ref.https://symfony.com/doc/current/routing.html)
8. composer require twig