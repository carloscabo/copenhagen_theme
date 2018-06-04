# Villabona-Tabladiello Theme by Carlos Cabo based on Copenhagen Theme by Zendesk

You can read the original documentation fot Copenhagen theme at its repository <https://github.com/zendesk/copenhagen_theme>

Here you'll find mdifications ans 

## How to use

This is the latest version of the Copenhagen theme available for Guide. It is possible to use this repository as a starting point to build your own custom theme. You can fork this repository as you see fit.

## Customizing your theme

Once you have forked this repository you can feel free to edit templates, CSS in `style.css` (if you would like to use SASS go to the [Using SASS section](#using-sass)), javascript and manage assets.

### Manifest file
The manifest allows you to define a group of settings for your theme that can then be changed via the UI in Theming Center.
For example, if you update the manifest file to look like this and you then import your theme to Theming Center:
```js
{
  "name": "Villabona-Tabladiello",
  "author": "Carlos Cabo",
  "version": "1.0.1",
  "api_version": 1,
  "settings": [{
    "label": "Colors",
    "variables": [{
      "identifier": "brand_color",
      "type": "color",
      "description": "Brand color for major navigational elements",
      "label": "Brand color",
      "value": "#7B7B7B"
    }]
  }, {
   "label": "Custom setting group",
   "variables": [{
     "identifier": "custom_var",
  	 "type": "text",
  	 "description": "Custom variable to change the title",
  	 "label": "Title",
  	 "value": "Welcome to our Help Center"
   }]
  }]
}

```
You would see two setting groups with a variable each in your theme inside Theming Center with the correct input types:
![Manifest](https://zendesk.box.com/s/7hq7ohd7dt5buh56izawxipybi41fs80)

You can read more about the manifest file [here](https://support.zendesk.com/hc/en-us/articles/115012547687--THEMING-CENTER-BETA-Settings-manifest-reference)

### Settings folder
If you have a variable of type file, you need to provide a default file for that variable in the `/settings` folder. This file will be used on the settings panel by default and users can upload a different file if they like.
Ex.
If you would like to have a variable for the background image of a section, the variable in your manifest file would look something like this:

```js
{
  ...
  "settings": [{
    "label": "Images",
    "variables": [{
      "identifier": "background_image",
      "type": "file",
      "description": "Background image for X section",
      "label": "Background image",
    }]
  }]
}

```

And this would look for a file inside the settings folder named: `background_image`
You can find more information about adding assets [here](https://support.zendesk.com/hc/en-us/articles/115012399428--THEMING-CENTER-BETA-Using-your-own-theme-assets-for-Help-Center)

### Adding assets
You can add assets to the asset folder and use them in your CSS, Javascript and templates.
You can read more about assets [here](https://support.zendesk.com/hc/en-us/articles/115012399428--THEMING-CENTER-BETA-Using-your-own-theme-assets-for-Help-Center)


## Publishing your theme
After you have customized your theme you can download the repository as a `zip` file and import it into Theming Center.

You can follow the documentation for importing [here](https://support.zendesk.com/hc/en-us/articles/115012794168--THEMING-CENTER-BETA-Importing-and-exporting-your-theme-and-manifest-file#topic_jpd_zdc_hbb).

You can also preview your theme before you import it to Theming Center with the Zendesk App Tools framework, you can read more about local preview [here](https://support.zendesk.com/hc/en-us/community/posts/115007717507-Local-Theme-Preview-via-Zendesk-Application-Tools)

## Templates
The theme includes all the templates that are used for a Help Center that has *all* the features available.
List of templates in the theme:
* Article page
* Category page
* Community post list page
* Community post page
* Community topic list page
* Community topic page
* Contributions page
* Document head
* Error page
* Footer
* Header
* Home page
* New community post page
* New request page
* Requests page
* Search results page
* Section page
* Subscriptions page
* User profile page

## Styles
The styles that Theming Center needs to use in the theme are in the `style.css` file in the root folder.

The styles for the theme are split using Sass partials, all the partials are under [styles/](/blob/master/styles/), they are all included in the "main" file [index.scss](/blob/master/styles/index.scss) and then compiled to CSS.
If you wish to use SASS you can go to the [using SASS section](#using-sass)

## Assets
These are the images and font files that are needed for the theme.
These includes:
* Default Favicon
* Home page banner image
* Community banner image (for Community topics list page)
* Community image (for Community section in Home page)
* Copenhagen icons font
* Entypo icon font
* Dropdown arrow

# Using SASS

I recomend you to use `node-sass` to compile the SASS files executing the following command in the root folder of the proect:

```
node-sass --output-style nested ./styles/index.scss ./style.css
```

Yo can also use `nodemon` to launch a monitr that compiles the styles atomatically when some `sass` file changes:

```
nodemon --watch ./styles -e css,scss -x "node-sass --output-style nested ./styles/index.scss ./style.css"
```

# Inject local CSSs in production server for developent

To copy paste your CSS in the Zendesk server is a tiring process, you can use a trick for a faster development.

1. Start a local server
```
php -S 127.0.0.1:8888
```

2. Replace the `style.css` path in the `href` attribute to point to your local server
```
$('link[rel="stylesheet"][href*="style.css"]').first().attr('href','http://127.0.0.1:8888/style.css')
```
3. Use some hnady Chrome extension as `Reload CSS` to reload the CSSs as you make changes ;)

# Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/zendesk/copenhagen_theme
Please mention @zendesk/delta when creating a bug report or a pull request.
