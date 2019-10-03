# Set up

- Install XAMPP
- Install Composer
- Create project using command : composer create-project symfony/skeleton symphart
- Modify httpd-vhosts.conf(path : xampp > apahce > conf > extra > httpd-vhosts.conf)

    <VirtualHost *:80>
        DocumentRoot "C:/xampp/htdocs/symphart/public"
        ServerName symphart.test
    </VirtualHost>

- Add "127.0.0.1 symphart.test" into hosts file.
- Add .htaccess on Public folder
<code>
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

</code>





- composer require annotations(ref.https://symfony.com/doc/current/routing.html)
- composer require twig
