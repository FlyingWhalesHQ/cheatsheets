---
layout: default
title: ImageMagick sizes
permalink: /imagemagick-sizes/
---

# ImageMagick Sizes Cheatsheet

To use with Carrierwave, Paperclip, Dragonfly and other gems that use minimagick gem.

```rb
'400x300'         # resize, maintain aspect ratio
'400x300!'        # force resize, don't maintain aspect ratio
'400x'            # resize width, maintain aspect ratio
'x300'            # resize height, maintain aspect ratio
'400x300<'        # resize only if the image is smaller than this
'400x300>'        # resize only if the image is larger than this
'50x50%'          # resize width and height to 50%
'400x300^'        # resize width, height to minimum 400,300, maintain aspect ratio
'2000@'           # resize so max area in pixels is 2000
'400x300#'        # resize, crop if necessary to maintain aspect ratio (centre gravity)
'400x300#ne'      # as above, north-east gravity
'400x300se'       # crop, with south-east gravity
'400x300+50+100'  # crop from the point 50,100 with width, height 400,300
```

---
