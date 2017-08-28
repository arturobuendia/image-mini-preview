# image-mini-preview
Preview of an image link on mouse hover. This is an edit to Will Boyd's "mini-preview" script that is designed to show previews of entire
webpages in a small iframe. I was not able to find a Github repo for his project, but it is shared on Codegena. Upon using this for
my purposes to preview images and gifs on a mousehover, I found the script was not optimized for standalone img/gif links.

### The Header tag:
The below code is placed in the same location: the header element in the html file you wish to use.
In a Wordpress (WP) installation, simply place this after the "wp_head()" in your theme's "header.php" file.

1) Make sure we include Jquery (Google the latest jquery version):
```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>
```

2) We make sure to locate the .css file. In your WP installation, this should be put in the wp-includes/css folder:
```
<link href="http://yourwebsite.com/wp-includes/css/previewlinksBlog.css" rel="stylesheet">
```

3) We utilize the script. The $(window).on('load' ...) function is meant to run the script only after the full page has loaded.
In this instance, the element the script would apply to is all of the "a" link elements. You should change this to links that only
have their "href" attributes set to image files and not separate weblinks. Instead of $('a'), we should apply to a class of "a"
elements, such as $('.links-with-img-or-gif').

The prefetch of 'pageload' loads the images/gifs as soon as the page loads. The other options are 'parenthover', where
the image/gif loads when your mouse hovers over the parent element of where the script is applied, or 'none', where the 
image loads only when your mouse hovers over the link (slowest). These latter two options have not been tested for my edit.
```
<script type="text/javascript">
    $(window).on('load', function(){
        $('a').miniPreview({ prefetch: 'pageload' });
    });
</script>
```
Lastly, we load the javascript file, which should be placed in the wp-includes/js folder if you have a WP installation:
```
<script src="http://yourwebsite.com//wp-includes/js/previewlinksBlog.js"></script>
```
