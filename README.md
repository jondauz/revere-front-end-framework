# Revere Front-End Framework

SASS (& HTML examples) for the Revere Suite.

## Page Structure

Revere pages are broken up into the following five sections.

* [Page Header](#page-header)
* [Main Navigation](#main-navigation)
* [User Navigation](#user-navigation)
* [Layouts](#layouts)
 * [Primary](#primary)
 * [Overview](#overview)
 * [Settings](#settings)
 * [Flow](#flows)
* [Page Footer](#page-footer)
* [Standards Across Apps](#standards-across-apps)

## Page Header

Page header consists of the app logo and a button visible on small viewports to toggle between the _navigation_ and _canvas_.

### Logo

Logos are generated as data URI’s in `_header.scss`. Each logo should be placed in an h1 tag classed with `.logo` and the app name spelled out. The logo is generated by the h1.logo and the body class for the specific app.

Logos are displayed as svg background images, declared from the body class, e.g. body.revere.dashboard displays the dashboard logo.

### Navigation Toggle

This `button` will be consistent throughout all apps.

```
<button id=“navigation-toggle” class=“v-nav-toggle”>
	Menu
	<svg class=“icon nav-menu”>
		<use xlink:href=“/revere-front-end-framework/icons/icons.svg#menu”>
		</use>
	</svg>
</button>
```

## Main Navigation

Main navigation provides the user with a way to navigate through top levels of each app and between various Revere apps and products through an unordered list of items. Each app will display app specific links as the first list items and the last list items consist of the standard items across all apps listed below:

* **Revere Suite**
** All apps beginning with **Revere Dashboard**, then remaining apps in alphabetical order. All apps include Revere as the first word followed by [app name]
* **Knowledge Base** - http://kb.reverehq.com/
* **Support** - http://dashboard.reverehq.com/support/ 

Class Structure for Main Navigation below, [view html](https://github.com/revolution-messaging/revere-pattern/blob/staging/views/_mainnav.html)

```
.navigation__main
	.navigation__main--list
		.navigation__main--list-item
		.navigation__main--list-item-parent // li with child ul
   .navigation__main--list-child
   
  // Icons
  .navigation__main--icon
```

## User Navigation
User Navigation contains the username (and gravatar where applicable) of the individual user with one of two actions available depending upon the app.
1. username and gravatar links to the users settings page on dashboard: https://dashboard.reverehq.com/settings/
2. username clicks to reveal a logout action that logs the user out of the Revere Suite.

The second component within the User navigation is the client menu. The client menu is placed after the username in mark-up as a dropdown allowing the user to switch between client accounts on various apps. 

Design pattern for User Navigation is similar to Main Navigation, with `navigation__[element]` changed from `main` to `user`. [View raw mark-up here](https://github.com/revolution-messaging/revere-pattern/blob/staging/views/_usernav.html)

#### Additional content

Multiple Revere Apps require additional items in the page header. On a large viewport, these items appear to the left of the header logo and are horizontally centered to the **logo** and the **User Navigation**.

* **Calling**
** Add Flow link
* **Direction**
** Short URL Creator
** Chicklet Bookmarklet
* **Mobile**
** Broadcast Scheduler
** Subscriber Search

*During certain actions within Revere Apps, it is undesirable to permit users to switch accounts. To achieve the disabling of the account switcher, add the class `.disabled`.

##### To-Dos
* Incorporate @Dauzy's js for `.disabled` on the user nav into vanilla jquery or javascript for incorporation in the FEF.

## Layouts

### Primary

The main content area of Dashboards and Apps is defined by the `.primary` class and consists of a `header` followed by a _canvas_ area that is defined by the `.canvas` class.

### Canvas

The canvas area is the main body of any revere app, and consists of three different types of interfaces, **overview**, **settings** and **flow**. .

The canvas interface is used to display content as well as linear and simple user flows. Please look to any portion of [Revere Dashboard](https://dashboard.reverehq.com/), [Revere Direction](https://direction.reverehq.com/) or [Revere Exchange](https://exchange.reverehq.com/).

### Overview

Overview `.overview` layouts are used to display summary or overview information. This could be tiles of all ad campaigns in [Exchange](https://exchange.reverehq.com/), account management in [Direction](//direction.reverehq.com), or documentation in the [Pattern Library](//pattern.reverehq.com).

### Settings

The Settings `.settings` layout is designed primarily for linear forms and other interactions. An example of a _settings_ layout is the ad campaign builder in [Exchange](//exchange.reverehq.com) and the user settings page in [Dashboard](//dashboard.reverehq.com).


### Flow

The flow interface is intended to display more complex and non-linear user flows such as the call-flow builder in **[Revere Calling](https://calling.reverehq.com/)** and mobile flows in **[Revere Mobile](https://mobile.reverehq.com/)**

_* Flow interfaces have not officially been added to the FEF._


## Page Footer

The footer will be identical across all apps, and dashboard footers will differ from apps in color alone. 

### Adding Footers to New Apps

Follow the procedure below when creating a new app or dashboard. 

* Copy the the `views/_footer.html` file from [Revere Pattern](https://github.com/revolution-messaging/revere-pattern/) 
* Locate the `// Footer Copyright` in `main.js` file in the [FEF]("Revere Front End Framework"), add your app name to the  section.

Content from the `views/_footer.html` file in Revere Pattern is required to be a direct descendant and final block element in the `<body>` and directly above the `<script>` tags just above the `</body>`.
 
## Standards across apps

* No `:hover` to reveal actions. Dropdown menus and miscellaneous reveals will always appear _on-click_, never _on-hover_.

###### To-Dos

* create boilerplate Revere logo
* `.dashboard .navigation__user` needs to reveal on _click_ not on _hover_. Note: `navigation__user` works as intended in the `.app` environment.

<!-- ### Body Classes

Design for specific apps is defined by the body class. Each app must contain the following body classes,  -->


### Page Structure

**Needs Writeup on page structure**

### Icon handling

All icon art should be exported as SVGs with no fill or stroke applied. This is so that we can control those and others filters via CSS. SVGs should be saved in to `icons/svg/`. When new icons have been saved to this folder, it will be necessary to re-generate the SVG sprite. Run `gulp svgstore`. This will create a new SVG sprite file called `icons.svg` in `icons/`. All of the SVG icons will be saved with the ID of the file name of which they were saved.

The default style for all icons can be found in `revere-front-end-framework/sass/_icons.scss`. You may also use this file to change the CSS attributes of specific icons.

Markup:

```html
    <svg class="icon icon-[name]">
      <use xlink:href="#icon-name"></use>
    </svg>
```    
  
* to do: Automate inclusion of markup to display icons in icons.php include

## Patterns

- Pagination: Revere currently has a standard pagination display (just page numbers), and an advanced display (adds Previous, Next, First and Last). 

### SASS File Structure
- Base Styles `/base`: Base directory contains boilerplate styles.
 - Fonts `/base/_fonts.scss`: **Helvetica Neue** is the standard Revere Typeface. *Browser caching needs to be added*
 - Colors `/base/_colors.scss`: All the colors of the rainbow that are permitted in the Revere Suite
 - Defaults `/base/_defaults.scss`: Standard formatting across the Revere Suite.
 - Tables `/base/table.scss`: Default display of tables throughout the Revere Suite.
- Helper Styles `/helpers`: Helpers directory contains support files.
 - Logos `/helpers/_revere_logo.scss`: For caching purposes, we load all logos in one file.
 - Icons `/helpers/_icons.scss`: Icon styles for various contexts
 - Mixins `/helpers/_mixins.scss`: The Mixins file holds mixins. 
 - Animations `/helpers/.scss`: Animations are contained within a single file so they can easily be added to new apps and contexts
- Layouts `/layouts/`: The Layout directory
- Modules `/modules`: The modules directory contains display modules. 
 - Feedback `/modules/_feedback.scss`:
 - [Pagination `/modules/_pagination.scss`](/blocks.html#pagination):
 - Forms `/modules/forms/*`:
   - Forms `/_forms.scss`: **Needs work** elements in this directory need to be updated to sub-files for individual elements.
 - Navigation `/modules/navigation/*.scss`:
 - Palette `/modules/_palette.scss`:
 - Header `/modules/_hed.scss`: The Header module contains standard padding for standard `.[block]__hed` headers.
