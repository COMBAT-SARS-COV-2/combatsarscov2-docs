Tip - use mogrify to put black borders on image, as per [this page](https://legacy.imagemagick.org/discourse-server/viewtopic.php?t=17158).

` mogrify -shave 1x1 -bordercolor black -border 1 -format jpg *.jpg`

