#### CARIFY Widget/Component Integration

CARIFY provides web components in order to give third parties and dealers the ability to list their vehicles on their own website. Note that the booking and checkout process will still happen explicitly on the CARIFY website.

##### Setup

To get started, follow these steps to register the CARIFY web components on your website.

1. Ensure that the language of your website is set to one of our supported languages `en`, `de`, `fr` or `it`. For example if you want the components to use German, set the `lang` attribute in your HTML as follows:

   ```html
   <html lang="de">
   ```

   > The lang attribute can also be something like de-CH, or en-US etc.

2. Ensure that you have a proper `viewport` meta element set in the head of your HTML document as well. This is needed to properly render elements for different screen sizes.

   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   ```

3. Include the CARIFY web components script in your website. You will need to pass your unique _Dealer ID_ provided by CARIFY as an `id` parameter to the script. If your dealer ID is `123-ABC-XYZ` for example, you would include the script as follows:

   ```html
   <script type="module" src="https://cdn.jsdelivr.net/gh/carify-me/carify-components@^5/dist/carify.min.js?id=123-ABC-XYZ"></script>
   ```

   > Note **type="module"** for the script

4. Contact CARIFY support to **whitelist** your website in order for the widgets to be allowed to query our API from your domain.



##### Catalog Component

Once you have completed the setup, you can include the `carify-vehicle-catalog` component in your website markup.

It currently supports three parameters:

1) `filter`- Will display a filter bar at the top of the vehicle catalog
2) `limit`- Sets the number of vehicle cards to display per page on the catalog
3) `target`- Set a custom page to navigate to on your website if a vehicle card is clicked. If this is omitted, clicking a vehicle card will open a new tab and navigate to the vehicle's page on the CARIFY website.

So, if for example you want to include your catalog, with a filter, a limit of 12 vehicles per page and for it to navigate to a `/carify/product/vehicle` page/url on your own website, you would include it as follows:

```html
<carify-vehicle-catalog target="/carify/product/vehicle" limit="12" filter></carify-vehicle-catalog>
```

> Note that the catalog component will automatically include the vehicle's **UUID** in the query string parameters of the target page, in order for the component to identify which vehicle details to fetch and display on the page.
>
> Specifying a target of **/carify/product/vehicle** for example, will a generate a link that that looks something like:
> **/carify/product/vehicle?uuid=e7a2b6a9-feeb-4abc-b697-fd25c4308e9b**
>
> Some other CARIFY related query parameters might also be included in this URL.



##### Product Component

Following steps from the catalog component section, on your custom `/carify/product/vehicle` page/url on your website, you can now include the `carify-vehicle-product` component.

> Note that the CARIFY web components script in the setup section must also be included on this page.

It currently supports two parameters

1. `show-provider`- If set, the component will show the dealer/provider below the vehicle equipment section
2. `book-now`- If set, clicking the "Start booking request" button will directly navigate to the booking/checkout page of the vehicle on the CARIFY website, instead of the vehicle details and package configuration page.

So, if for example you want the vehicle product component to _not_ show the provider, but go directly to the booking/checkout page on CARIFY, you would include it as follows:

```html
<carify-vehicle-product book-now></carify-vehicle-product>
```



##### Customization

You can customize the CARIFY web components using CSS variables. Just target the component in a `styles` tag in your HTML markup and set the relevant CSS variables. If for example, you want the accent color of the components to be _purple_ you would set it as follows:

````html
<style>
 carify-vehicle-catalog, carify-vehicle-product {
     --crf-accent-color: purple;
 }
</style>
````

The following customization variables are currently supported:

`--crf-font-family`- Set the font-family to use in the components

`--crf-accent-color`- Set the accent color to use in the components

`--crf-text-color`- Set the text color to use in the components

`--crf-section-radius`- Set the radius of elements such as vehicle cards and sections
