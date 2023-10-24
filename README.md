### CARIFY Web Components

#### Introduction

These web components are built with the intent to be used by 3rd parties or external websites. It will allow you to include/embed

functionality from the CARIFY website (for example a search grid with vehicles) directly into your own website.

#### TL;DR

Include the CARIFY components script in your document head and use the custom
HTML element tags.

A full example of the `carify-vehicle-grid` component that has been fully customized with a _custom theme_ via the custom CSS properties and the available attribute configurations can be found in the `example` folder.

#### Getting Started

To get started, you should include the following script in the head of your HTML page or website:

```html
<script src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@^4/dist/carify.min.js?dealer={DEALER_ID}"></script>
```

> Note: You should replace **{DEALER_ID}** with your _own_ unique dealer ID obtained from the CARIFY admin interface.

If on the other hand, you are part of a group you should change your script `src` attribute to to following:

```html
<script src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@^4/dist/carify.min.js?group={GROUP_ID}"></script>
```

> Note: You should replace **{GROUP_ID}** with your _own_ unique group ID which you can obtain by contacting CARIFY.

We follow [semantic versioning](https://semver.org) with the release of these components to ensure we don't introduce unwanted breaking changes to components you embed in your website. Please take note of the current semantic version constraint in the URL: `^4`.

These components could potentially be receiving rolling updates by the week or by the day, so we recommend that you stick to the `^4` version constraint.

This way, your page that includes the script, will automatically receive _bug fixes_ **and** _new features_ but **no** breaking changes. We will only introduce breaking changes in a _major_ version change, i.e. `^5`.

If you wish to however include a _specific_ version of the components, can you specify that in the URL as well, example:

```html
<script src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@4.0.2/dist/carify.min.js"></script>
```

You can view available releases on the [tags page](https://github.com/carify-me/carify-components/tags).

#### Components

Getting started with the components is straight forward. They are built as [custom HTML elements](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements) with modern web technologies, so you can just include these component anywhere on your page as a custom HTML tag, for example:

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
    <script src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@^4/dist/carify.min.js"></script>
  </head>
  <body>
    <carify-vehicle-grid></carify-vehicle-grid>
  </body>
</html>
```

> If no language is specified anywhere, the component will render using the default language, which is English.

---

#### The GRID component

Tag: `<carify-vehicle-grid>`

##### Attributes

You can customize this component by specifying custom attributes:

| Attribute    | Description                                                       | Default |
| ----------   | ----------------------------------------------------------------- | ------: |
| utm_source   | UTM source query parameter value to generate in vehicle links     | partners|
| utm_campaign | UTM campaign query parameter value to generate in vehicle links   |  carify |
| paginate     | Number of cards to display per page                               |      12 |
| paginate     | Number of cards to display per page                               |      12 |
| heading      | Specify a heading for the grid                                    |  _none_ |
| slider       | Use multiple images on vehicle cards instead of a single image    |   false |
| sortable     | Add a dropdown to the grid that allows users to sort it           |   false |
| searchable   | Add a search bar to the top of the grid that allows users to search and filter |   false |
| motion       | Add motion animation to a card when hovering over it              |   false |
| internal     | If specified, vehicle card links will not open in a new tab       |   false |
| page         | Custom page to navigate to when a card is clicked                 |  _none_ |
| config       | An advanced configuration object (see advanced config)            |  _none_ |

> Note on UTM Campaign value:
If a _dealer_ of _group_ query parameter is defined in the script inclusion, that value will be used
unless an explicit _utm_campaign_ value is specified.

##### Grid Advanced configuration

You can specify and advanced `config` property as a JSON object to the `<carify-vehicle-grid>`
component with following available properties

| Attribute      | Description                                                             | Default |
| -----------    | ----------------------------------------------------------------------- | ------: |
| advanced       | Show or hide the 'More filters' button                                  |    true |
| transparent    | Make the backdrop of the more filters popup transparent                 |   false |
| topAlign       | Align the more filters popup to the top of the widget instead of center |   false |
| hide           | Hide specific filters from the more filters popup menu                  |  _none_ |
| filters        | Pre-apply filters to the grid                                           |  _none_ |
| durationFilter | Filter duration drop-down to only show certain options (Number array)   |  _none_ |
| distanceFilter | Filter kilometer drop-down to only show certain options (Number array)  |  _none_ |

Available `hide` options

- `gear` (Hide the transmission filter)
- `fuel` (Hide the fuel type filter)
- `type` (Hide the car type filter)
- `power` (Hide horse power filter)
- `drive` (Hide drive type filter)
- `seats` (Hide the seats filter)
- `canton` (Hide the canton filter)
- `dealer` (Hide the dealers filter)
- `makes` (Hide the makes filter)
- `models` (Hide the models filter)

Example: Do not show the `Transmission Type` and `Fuel Type` filters on the more filters popup

```html
<carify-vehicle-grid config='{"hide": ["gear", "fuel"]}'></carify-vehicle-grid>
```

---

#### The vehicle component

Tag: `<carify-vehicle-info>`

##### Attributes

| Attribute | Description                                             | Default |
| --------- | ------------------------------------------------------- | ------: |
| uuid      | Thee UUID of the vehicle to fetch via the CARIFY API    |       - |
| handover  | Should the handover date input option be displayed      |   false |
| no-tab    | Prevent a new tab from opening when clicking book now   |   false |

> If no UUID is provided to the `<carify-vehicle-info>` component, by default it will look for a `uuid` query parameter in the page that it is included in.
> For example, if it is included in a page: `https://example.com/vehicle?uuid=123` it wil use `123` as the UUID of the vehicle to fetch from the CARIFY API.

---

##### CSS Styles

For semantic configuration, we allow you to customize the the vehicle grid through [custom css properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties).

Below is a list of custom CSS properties/variables that you can define for different CARIFY components in your CSS.
You are encouraged to create your own 'theme' and style these components to match the design and/or look and feel of your website.

| Property                       | Description                                                             | Default |
| ------------------------------ | ----------------------------------------------------------------------- | ------: |
| --busy-indicator-color         | Color of busy indicator when busy fetching data                         |    #000 |
| --grid-font                    | The font the grid should use                                            | inherit |
| --grid-font-base               | The base font size of the grid.                                         |    16px |
| --grid-columns                 | Number of columns to use per row in the layout of the vehicle grid      |       4 |
| --heading-color                | Color of the grid heading (if a heading is provided)                    |    #000 |
| --active-page-indicator-color  | Color of the active page indicator for pagination                       |    #000 |
| --active-page-indicator-bg     | Background color of the active page indicator for pagination            | #efefef |
| --card-font                    | The font vehicle cards should use                                       | inherit |
| --card-font-base               | The base font size of a card                                            |    16px |
| --card-shadow                  | CSS drop shadow definition for a card                                   |       - |
| --card-border-radius           | The border radius of the card                                           |    20px |
| --card-background-color        | The background color of a card                                          |    #fff |
| --card-image-background        | The background color of the vehicles images                             | default |
| --card-text-color              | The default text color of a card                                        |    #000 |
| --vehicle-name-color           | Color of the vehicle name inside a card                                 |    #000 |
| --vehicle-specs-color          | Color of listed vehicle specifications inside a card                    |    #000 |
| --vehicle-price-color          | Color of the vehicle price inside a card                                |    #000 |
| --vehicle-price-strike-color   | Color of the strike-through price if the vehicle is on promotion        | #963131 |
| --badge-text-color             | Text color of the badges inside a card                                  |    #000 |
| --badge-electric-color         | Background color of the electric badge                                  | #efefef |
| --badge-recent-color           | Background color of the recent badge (vehicle was recently added)       | #efefef |
| --badge-special-color          | Background color of the special badge (vehicle has a discounted price)  | #efefef |
| --badge-popular-color          | Background color of the popular badge (vehicle is popular)              | #efefef |
| --badge-hybrid-color           | Background color of the hybrid badge                                    | #efefef |
| --package-detail-color         | Text color of package information (months/distance) inside a card       |    #fff |
| --package-detail-bg            | Background color of package information (months/distance) inside a card | #696969 |
| --package-detail-border-radius | Border radius of the package details pills                              |    40px |
| --heart-fill-color             | Fill color of the heart icon when vehicle is favoured by user           | #ff0000 |
| --filter-search-bg             | Background color of the 'Search' button inside the filter/search bar    | #efefef |
| --filter-search-color          | Text color of the 'Search' button inside the filter/search bar          |    #222 |
| --filter-view-bg               | Background color of the 'View' button inside the more filters popup     | #efefef |
| --filter-view-color            | Text color of the 'View' button inside the more filters popup           |    #222 |
| --active-filter-bg             | Background color an applied filter inside the more filters popup        | #efefef |
| --active-filter-color          | Text color an applied filter inside the more filters popup              |    #222 |
| --drop-down-bg                 | Background color of the drop-down option lists                          |    #fff |
| --drop-down-color              | Text color fo the drop-down option lists                                |    #222 |
| --drop-down-active-color       | Text color of the active/selected item in the drop-down list            |    #222 |
| --drop-down-active-bg          | Background color of the active/selected item in the drop-down list      | #efefef |
| --info-font                    | The font the vehicle information pane should use                        | inherit |
| --info-font-base               | The base font size of the vehicle information pane.                     |    16px |
| --info-accent-color            | The accent color the vehicle information pane should use                |    teal |
| --gallery-background           | The background color of images in the vehicle gallery                   |   black |
