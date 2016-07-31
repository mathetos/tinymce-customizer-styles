# TinyMCE Customizer Styles

This is a "drop-in" file for WordPress themes to have their Customizer colors dynamically affect their TinyMCE styles
---

This file automatically generates inline styles into your TinyMCE Editor in WordPress generated from the colors in your Customizer.

This is a useful function for Theme author who wish to have their Post/Page editor more closely reflect the look and feel that your Theme creates with its Customizer setings.

## How to Use
 
It's just a matter of dropping in the file, and filtering the main array.
 
**STEP 1** 
 
Drop this file into your theme and include it like so: `include(get_stylesheet_directory_uri() . 'tinymce-customizer-styles.php');`
 
Of course you might want to put it in a sub-folder, but that's up to you.
 
**STEP 2**
 
Customize the inline styles according to your theme_mods by filtering the action with your own function. 
 
This example is for Twenty Sixteen:
 
```
function kwh_define_theme_mods( $theme_mods ) {
 	$theme_mods = array(
 		'page_background_color' => array(
 			array(
 				'selectors'  => 'body',
 				'properties' => array( 'background-color' )
 			),
 			array(
 				'selectors'  => 'ins',
 				'properties' => array( 'color' )
 			)
 		),
 		'link_color' => array(
 			array(
 				'selectors'  => 'a',
 				'properties' => array( 'color' )
 			),
 			array(
 				'selectors'  => 'ins',
 				'properties' => array( 'background-color' )
 			)
 		),
 		'main_text_color' => array(
 			array(
 				'selectors'  => 'body, blockquote cite',
 				'properties' => array( 'color' )
 			),
 			array(
 				'selectors'  => 'blockquote',
 				'properties' => array( 'border-color' )
 			),
 			array(
 				'selectors'  => 'code',
 				'properties' => array( 'background-color' ),
 				'alpha'      => '0.2'
 			),
 			array(
 				'selectors'  => 'table, th, td, pre',
 				'properties' => array( 'border-color' ),
 				'alpha'      => '0.2'
 			)
 		),
 		'secondary_text_color' => array(
 			array(
 				'selectors'  => 'blockquote',
 				'properties' => array( 'color' )
 			)
 		)
 	);
 
 	return $theme_mods;
 }
 add_filter( 'kwh_theme_mods', 'kwh_define_theme_mods' );
 
 ```
**STEP 3**
 
There is no step three, you're done! Unless you'd like to further customize your theme_mods, go at it, have fun.

##About This Project

This started as an idea that Matt Cromwell (@mathetos) put forward. He believed something like this was possible but didn't know exactly where to hook into TinyMCE.

Through the Advanced WordPress Facebook Group both Kevin Hoffman (@kevinwhoffman) and Samuel Wood (@Otto42) chimed in. Otto provided the exact hook and method for making this happen.

Kevin then took the basic concept and then created the main helper function which cycles through all your theme_mods to generate the inline CSS on the fly.

[Matt did a write-up about it here](https://www.mattcromwell.com/dynamic-tinymce-editor-styles-wordpress/).
