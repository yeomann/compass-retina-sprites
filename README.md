# Compass-Retina-Sprites

![alt text](https://lh5.googleusercontent.com/-vfpFIq1cw0w/Uo96k6YurwI/AAAAAAAAAws/kX3uCe7r0hs/w500-h284-no/logo.png "Compass-Retina-Sprites- danishraza")

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png


## A mixin to create retina sprites with hover & active states

While building [Swimming website](http://havuz.neu.edu.tr), I came across the need to use compass sprites with hover states on normal and retina devices. Not being able to find anything that would suite my needs, I forked a gist from [this Gist](https://gist.github.com/2140082) and added hover & active parameters. Big thanks to [thulstrup](https://github.com/thulstrup) and  [rstacruz](https://github.com/rstacruz)!

I created a drop in utility mixin to allow compass to automatically create sprites for normal and retina devices, and also providing hover and active states.

### Features

* Generate Normal & Retina Sprites
* Optional Hover & Active States
* Optional Sprite Spacing/Padding


There is Demo Example included in demo folder with working sample socil icons example.

## Instructions

* Drop __RetinaSprites.scss into your location in sass folder 
* Now, link that file in your main file, @import "__YOURFOLDERNAME__/retina-sprites"; eg. styles.scss
* Both files are provided before demo folder
* SASS settings is Setup.Now let's Create two folders in your images folder. For my example I've created "sprites" for 1x sprites and "sprites2x" for 2x sprites. In my example you can see that Compass/Sass is creating both Sprites in main images folder. Drop your photo's in these folders, 

## Remember!!

* **They should have the same file name**.
* **Also make sure the retina images are divisible by 4**. If they are not, it can lead to problem like clipping and shifting.

In your SCSS file, declare where your sprites are located. In this example I have my social icons in a separate scss file, and I place the following in the top of this file.

	$sprites: sprite-map("sprite/*.png", $spacing: 1px); // import normal sprites
	$sprites2x: sprite-map("sprite2x/*.png", $spacing: 2px); // import 2x sprites
    
If you would like to add padding to your sprites, use the spacing parameter and double the value for the retina version:

$sprites: sprite-map("sprite/*.png", $spacing: 1px); // import normal sprites, 1px padding space
$sprites2x: sprite-map("sprite2x/*.png", $spacing: 2px); // import 2x sprites, 2px padding space 

## Advance Options

/* Creates the sprite maps and placeholder classes used by the other mixins. */
@include generate-sprite-map($sprites, $sprites2x, $with-dimensions: true);

/* Allows for pre-defined auto-generated classes. */
@include retina-sprite-classes($sprites, $sprites2x, $prefix: 'sprite-', $with-dimensions: true);

where,
* $sprites, is the 1x Sprite Folder which means (Normal Folder).
* $scprites2x, is the 2x Sprite Folder which is Retina Display Icons. 
* $prefix, is fix word you will be added to every icons of sprite eg:

<code>< a class="sprite-googleplus" href="https://plus.google.com/u/0/+danishraza">Google+< /a></code>

* $with-dimensions, represent that dimension for retina icons is corrent, Boolean is required to use for that Option.
* more option are available on reading mixin file.

Almost ready to rock and roll!! Create a class for your sprite, and use an include to generate it.
 	
	.myHoverActiveButton {
		@include retina-sprite(signIn, $hover: true, $active: true);    // imports signIn.png, signIn_hover.png, and signIn_active.png
	}

    .myHoverButton {
	   @include retina-sprite(signIn, $hover: true);                    // imports signIn.png and signIn_hover.png
    }

    .myBoringButton {
       @include retina-sprite(signIn);                                  // imports signIn.png
    }

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/9c03052a2c62c8153c13242efe0f6d2a "githalytics.com")](http://githalytics.com/AdamBrodzinski/Retina-Sprites-for-Compass)

