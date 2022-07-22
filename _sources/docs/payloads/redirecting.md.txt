# Redirecting

Server-side scripting with PHP `header()`:
 
    header('HTTP/1.1 302 Moved Temporary');
    header('Location: http://www.somedomain.com/');
    exit;

Apache HTTP Server `mod_alias`:

    Redirect temporary /oldlocation.html http://www.example.com/newlocation.html
    Redirect 302 /oldlocation.html http://www.example.com/newlocation.html

Apache HTTP Server `mod_rewrite` (redirecting requests to a canonical domain name):

    RewriteEngine on
    RewriteCond %{HTTP_HOST} ^([^.:]+\.)*oldlocation\.example\.com\.?(:[0-9]*)?$ [NC]
    RewriteRule ^(.*)$ http://newlocation.example.org/$1 [R=302,L]

Nginx rewrite

    rewrite ^/oldlocation$ http://www.newexample.com/newlocation redirect;

Refresh Meta tag in document (add anchor in the “body” section for users whose browsers do not support this feature):

    <!DOCTYPE html>
    <html>
       <head>
          <title>HTML Meta Tag</title>
          <meta http-equiv = "refresh" content="0"; url = https://www.newexample.com" />
       </head>
       <body>
          <p>Please follow <a href="http://www.newexample.com/">this link</a></p>
       </body>
    </html>

HTTP refresh header in a perl or python script:

    print "Refresh: 0; url=http://www.newexample.com/\r\n";
    print "Content-Type: text/html\r\n";
    print "\r\n";
    print "Please follow <a href=\"http://www.newexample.com/\">this link</a>!"

JavaScript:

    <body onload="document.location='http://www.newexample.com/'">