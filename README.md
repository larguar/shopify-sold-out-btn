# Shopify Custom Sold Out Button Text


![HTML Badge](https://img.shields.io/badge/-HTML-323795) ![CSS Badge](https://img.shields.io/badge/-CSS-01A990) ![Shopify Liquid Badge](https://img.shields.io/badge/-Shopify%20Liquid-750460)


## Table of Contents 
* [Code](#code)    
* [Questions](#questions) 
* [Donate](#donate)
* [Notes](#notes)


## Code

:file_folder: **sections/main-product.liquid**

Search for first `<span class="button__text"` and replace `{%- liquid -%}` snippet with:
```
{% comment %} [LG] Custom Sold Out Button Text {% endcomment %}
{%- liquid
  unless default_to_first_variant
    if product.available
      echo 'products.grid.choose_variant_first' | t
    else
      echo 'products.page.inventory.sold_out_variant' | t
    endif
  else
    if current_variant.available
      unless block.settings.show_preorder
        echo 'products.page.add_to_cart_button' | t
      else
        echo 'products.page.preorder_button' | t
      endunless
    elsif current_variant == null
      echo 'products.page.inventory.unavailable_variant' | t
    elsif product.tags contains "clearance"
      echo "Gone for Good"
    elsif product.selected_or_first_available_variant.incoming
      echo "More On The Way!"
    else
      echo "Temporarily Out"
    endif
  endunless
-%}
{% comment %} [LG] End Custom Sold Out Button Text {% endcomment %}
```

## Questions
If you have any questions, feel free to find me at:
* Email: laurenguardala@gmail.com
* Website: [larguar.com](https://larguar.com)
* Github: [@larguar](https://github.com/larguar)


## Donate
Appreciate this code? Say thanks with a coffee:

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/W7W21YVJJ)


## Notes
[^1]: This code is specific to the [Combine](https://themes.shopify.com/themes/combine/styles/objects) theme in Shopify, but should work for other themes with some adjustments. File names will likely be different across themes.
[^2]: Replacing the contents means the settings on the Customize end will no longer work (sold out badge, discount badge, and custom badges).
[^3]: This is the file I created for my shop's custom CSS styles. If you have your own file already created, you can add this snippet to that file. If you need to create a new file, just make sure you link to it in your `layout/theme.liquid` file.
