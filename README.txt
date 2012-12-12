This drupal module depends on Node.js certifier for generating the certificates
https://github.com/mozilla/browserid-certifier

NB: Some prerequisites need to be in place before any of this will work:
 1. You will need the above certifier running and accessible to the site implementing this module. Sounds more simple than it probably is.
 2. You will need to use the certifier to generate a .well-known/browserid file. This will need to be served from the site implementing this module.
 3. The browserid file generated in the step above will need to be edited to use the endpoints provided by this module. By default these are:
   - browserid/provision
   - browserid/signin

 4. You will need to set the following variables - probably easiest if these are in your site's settings.php:

  $conf['bv_browserid_js'] = 'http://localhost'; // The URL of this server
  $conf['browserid_nodejs_certifier'] = 'http://localhost:8080/cert_key'; // The URL of the certifier
  $conf['bvp_browserid_domain'] = 'mydex.dev'; // The domain for which the user is being certified
  $conf['bv_browser_idp'] = 'adsfad03432XYZPASFA'; // Hashing salt for IDP

Hope this makes sense!
