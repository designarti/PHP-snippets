# PHP-snippets

**To create a  of the actual page URL for domains with www:**

`<?php $current_page = "http://www.$_SERVER[HTTP_HOST]$_SERVER[REQUEST_URI]"; ?>`

**To add variable to social share snippet:**

## Facebook:
`<a href="https://www.facebook.com/sharer/sharer.php?u=<?php echo "$current_page"; ?>">Share on Facebook</a>`
## Twitter:
`<a href="https://twitter.com/home?status=<?php echo "$current_page"; ?>">Share on Twitter</a>`
## Google Plus:
`<a href="https://plus.google.com/share?url=<?php echo "$current_page"; ?>">Share on Google+</a>`
