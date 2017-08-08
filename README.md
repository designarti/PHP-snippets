# PHP-snippets

## A simple include

~~~~
<?php include_once $_SERVER['DOCUMENT_ROOT'] . ("/include-folder-name/include-file-name.php"); ?>
~~~~

## This is to render page specific variables:

~~~~
<?php
    // Insert meta title here
    $title = "Your Page Meta Title";
    // End meta title

    // Insert meta description here
    $description = "Your Page Meta Description";
    // End meta description

    // This is the variable for URL, even if it has httpS instead of http
    $url = (isset($_SERVER['HTTPS']) && $_SERVER['HTTPS'] && !in_array(strtolower($_SERVER['HTTPS']),array('off','no'))) ? 'https' : 'http';
    $url .= '://'.$_SERVER['HTTP_HOST'];
    $url .= $_SERVER['REQUEST_URI'];
    if (!empty($_SERVER['PATH_INFO'])) $url .= $_SERVER['PATH_INFO'];
    if (!empty($_SERVER['QUERY_STRING'])) $url .= '?'.ltrim($_SERVER['REQUEST_URI'],'?');
    // End URL variable

    // Insert image path here - we do not use the slash (/); instead of "/images/image.jpg", we use "image/image.jpg", without slash
    $image = "your-image-folder/your-image-file-name.jpg";
    // End image variable
    
    // Insert alt for the above image
    $alt = "Your alt text";
    // End image alt variable

    // This is image variable URL absolute path
    $image_url = $url . $image;
    // End image URL variable
?>
~~~~

## To echo metas in the head section:

~~~~
<meta name="title" content="<?php echo $title; ?>">
<meta name="description" content="<?php echo $description; ?>">
~~~~

**According to [Facebook Developers Guide](https://developers.facebook.com/docs/sharing/webmasters "Facebook for Developers") we should have og:data. This is how we insert the variables for FB, using the above codes:**

~~~~
<meta property="og:url" content="<?php echo $url; ?>">
<meta property="og:type" content="article">
<meta property="og:title" content="<?php echo $title; ?>">
<meta property="og:description" content="<?php echo $description; ?>">
<meta property="og:image" content="<?php echo $image_url; ?>">
~~~~

**To add variable to social share snippet:**

## Facebook:
`<a href="https://www.facebook.com/sharer/sharer.php?u=<?php echo "$url"; ?>">Share on Facebook</a>`
## Twitter:
`<a href="https://twitter.com/home?status=<?php echo "$url"; ?>">Share on Twitter</a>`
## Google Plus:
`<a href="https://plus.google.com/share?url=<?php echo "$url"; ?>">Share on Google+</a>`

**To render the image in BODY**

~~~~
<img src="<?php echo htmlspecialchars($image); ?>" alt="<?php echo $alt; ?>">
~~~~
