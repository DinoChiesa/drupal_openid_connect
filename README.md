# OpenID Connect for Drupal

The OpenID Connect module provides a pluggable client implementation for the
OpenID Connect protocol.

For more information please consult the documentation: https://drupal.org/node/2274339

This repo contains a forked and modified version of the module, to allow it to work better with Azure AD as an OpenID Connect provider.


## Changes

A summary of the changes I made:

* Call the userinfo endpoint conditionally.  Azure AD does not publish the userinfo endpoint, as far as I could tell.  Actually, there's likely no need for a relying party (like Drupal) to call the userinfo endpoint, if Drupal already has the user profile information in the id_token.  Which it does. So I introduced some logic in the module to forego calling the userinfo endpoint in that case.

* Don't skip the name and email mapping.  For some reason the module by default does not allow mapping the OpenID Connect claims to the corresponding Drupal user entity properties of name and mail.  That doesn't make sense to me.  So I modified the code to not skip those properties.



## Author

Dpchiesa@hotmail.com

I'm not the author of the module, but I made the few small changes described here. 
