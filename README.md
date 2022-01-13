### CARIFY Web Components

#### Introduction

These web components are built with the intent to be used by 3rd parties or external websites. It will allow you to include/embed

functionality from the CARIFY website (for example a search grid with vehicles) directly into your own website.

#### TL;DR

Include the CARIFY components script in your document head and use the custom
HTML element tags.

A full example of the `carify-vehicle-grid` component that has been fully customized with a _blue-ish_ theme via the custom CSS properties and the available attribute configurations can be found in the `example` folder.

#### Getting Started

To get started, you should include the following script in the head of your HTML page or website:

```html
<script src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@^2/dist/carify.min.js?dealer={DEALER_ID}"></script>
```

> Note: You should replace **{DEALER_ID}** with your _own_ unique dealer ID obtained from the CARIFY admin interface.

If on the other hand, you are part of a group you should change your script `src` attribute to to following:

```html
<script src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@^2/dist/carify.min.js?group={GROUP_ID}"></script>
```

> Note: You should replace **{GROUP_ID}** with your _own_ unique group ID which you can obtain by contacting CARIFY.

We follow [semantic versioning](https://semver.org) with the release of these components to ensure we don't introduce unwanted breaking changes to components you embed in your website. Please take note of the current semantic version constraint in the URL: `^2`.

These components could potentially be receiving rolling updates by the week or by the day, so we recommend that you stick to the `^2` version constraint.

This way, your page that includes the script, will automatically receive _bug fixes_ **and** _new features_ but **no** breaking changes. We will only introduce breaking changes in a _major_ version change, i.e. `^3`.

If you wish to however include a _specific_ version of the components, can you specify that in the URL as well, example:

```html
<script src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@2.2.0/dist/carify.min.js"></script>
```

You can view available releases on the [releases page](https://github.com/carify-me/carify-components/releases).

#### Components

Getting started with the components is straight forward. They are built as [custom HTML elements](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements) with modern web technologies, so that you can just include these component anywhere on your page as a custom HTML tag, for example:

```html
<carify-vehicle-grid></carify-vehicle-grid>
```

#### Language

We officially support four languages: English (`en`), German (`de`), French(`fr`) and Italian (`it`).

You can indicate which language the component should use by specifying it in the [global HTML lang attribute](https://www.w3schools.com/tags/att_global_lang.asp).

If for example, you would like the custom HTML element to be rendered in French, you would use the following snippet:

```html
<carify-vehicle-grid lang="fr"></carify-vehicle-grid>
```

> Note: If you **do not** specify a language, the component will try to determine which language to use by the _lang_ attribute defined in your HTML document definition. For example, this component would be rendered in Italian:

```html
<!DOCTYPE html>
<html lang="it">
  <head>
    <script src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@^2/dist/carify.min.js"></script>
  </head>
  <body>
    <carify-vehicle-grid></carify-vehicle-grid>
  </body>
</html>
```

> If no language is specified anywhere, the component will render using the default language, which is English.

#### The GRID component

Tag: `<carify-vehicle-grid>`

##### Attributes

You can customize this component by specifying custom attributes:

| Attribute  | Description                                                       | Default |
| ---------- | ----------------------------------------------------------------- | ------: |
| paginate   | number of cards to display per page                               |      12 |
| heading    | specify a heading for the grid                                    |  _none_ |
| slider     | use multiple images on vehicle cards instead of a single image    |   false |
| sortable   | add a dropdown to the grid that allows users to sort it           |   false |
| searchable | add a dropdown to the grid that allows users to search and filter |   false |
| config     | an advanced configuration object (see advanced config)            |  _none_ |

##### CSS Styles

For semantic configuration, we allow you to customize the the vehicle grid through [custom css properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties).

Below is a list of custom CSS properties/variables that you can define for the `carify-vehicle-grid` component in your CSS:

| Property                       | Description                                                           |
| ------------------------------ | --------------------------------------------------------------------- |
| --active-page-indicator-bg     | Background color of active page in pagination                         |
| --active-page-indicator-color  | Text color of active page in pagination                               |
| --heading-color                | Text color of optional header provided through attribute              |
| --card-text-color              | Text color of the default card contents                               |
| --card-background-color        | Background color of the card                                          |
| --card-border-radius           | Border radius of the card                                             |
| --busy-indicator-color         | Color of the busy indicator when the grid is fetching/updated data    |
| --vehicle-name-color           | Text color of the vehicle name in the card                            |
| --vehicle-specs-color          | Text color of the vehicle specifications in the card                  |
| --vehicle-price-color          | Text color of the vehicle price                                       |
| --package-detail-bg            | Background color of package (duration/distance) indicators/pills      |
| --package-detail-color         | Text color of package (duration/distance) indicators/pills            |
| --vehicle-price-strike-color   | Color of the strike-through price if the vehicle is on promotion      |
| --badge-electric-color         | Background color of the electric badge                                |
| --badge-recent-color           | Background color of the recent badge (vehicle was recently added)     |
| --badge-special-color          | Background color of the recent badge (vehicle has a discounted price) |
| --badge-hybrid-color           | Background color of the hybrid badge                                  |
| --badge-popular-color: #fa6aff | Background color of the popular badge (vehicle is popular)            |
| --badge-text-color             | The text color of the badges                                          |
| --active-filter-bg             | Background color of a filter indicator when it is applied/active      |
| --active-filter-color          | Text color of a filter indicator when it is applied/active            |
| --filter-search-bg             | Background color of the search button                                 |
| --filter-search-color          | Text color of the search button                                       |
| --filter-view-bg               | Background color fo the view button when filters are applied          |
| --filter-view-color            | Text color fo the view button when filters are applied                |
| --drop-down-bg                 | Background color of the drop-down option lists                        |
| --drop-down-color              | Text color fo the drop-down option lists                              |
| --drop-down-active             | Background color of the active/selected item in the drop-down list    |
