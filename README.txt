=== WooCommerce Pay for Payment ===
Contributors: podpirate
Donate link: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=QFR9BVRT6SEP6
Tags: ecommerce, woocommerce, payment gateway, fee
Requires at least: 3.5
Tested up to: 4.1
Stable tag: 1.3.5
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
WC requires at least: 2.2
WC tested up to: 2.3
Setup individual charges for each payment method in woocommerce.


== Description ==

Add individual charges for each payment method as a flat rate and/or as a percentage of the cart total.
The plugin first calculates the percentage rate and then adds the fixed rate on top.

You can use placeholders in the payment item title:

- [FIXED_AMOUNT]: Will print money-formatted fixed amount you entered.
- [PERCENT_AMOUNT]: will print out percental amount you entered
- [CART_TOTAL]: will print out money-formatted cart totals. 
- Example: `Payment Fee ([FIXED_AMOUNT] + [PERCENT_AMOUNT]% of [CART_TOTAL])`


Requires at least woocommerce 2.2.

= Features =
- Fixed charge and/or a percentage of cart total
- Translations in German, Spanish ([muchas graçias!](https://github.com/GosserBox)) and Turkish localization ([çok](https://www.transifex.com/accounts/profile/TRFlavourart/) [teşekkürler!](https://github.com/TRRF))
- Plugin API. See [GitHub](https://github.com/mcguffin/woocommerce-payforpayment) for details.

= Limitations =
- Better not use it with paypal. (Legal issue, see FAQ as well.)

Latest files on [GitHub](http://codex.wordpress.org/Managing_Plugins).


== Installation ==

Just follow the standard [WordPress plugin installation procedere](http://codex.wordpress.org/Managing_Plugins).

== Frequently asked questions ==

= Can I use it with paypal? =

No. PayPal does not permit charging your customer for using PayPal. This is a legal issue rather than a technical one.
See [PayPal User Agreement](https://www.paypal.com/webapps/mpp/ua/useragreement-full?country.x=US&locale.x=en_US#4), > "4.6 No Surcharges" for details. 
You have been warned.

= Can't to setup my payment requirements in the user interface. The option I need is missing. =

The plugin user interface only offers either a fixed amout or a percentage of the carts subtotal. 
If you need to implement more complex calcuations like 'no charges for orders above 100 Bucks' or '2% of cart subtotal but at least 2 Bucks', 
you'll have to use one of the filters. See [Plugin API](https://github.com/mcguffin/woocommerce-payforpayment#plugin-api) for details.

<code>woocommerce_pay4pay_apply</code> specifies if a charge will be applied.

<code>woocommerce_pay4pay_applyfor_{$payment_gateway_id}</code> specifies if a charge will be applied on a certain payment method.

<code>woocommerce_pay4pay_{$payment_gateway_id}_amount</code> allows you to alter the amount of the charge being added.


= I want to use the latest files. How can I do this? =

Use the GitHub Repo rather than the WordPress Plugin. Do as follows:

1. If you haven't already done: [Install git](https://help.github.com/articles/set-up-git)

2. in the console cd into Your 'wp-content/plugins´ directory

3. type `git clone git@github.com:mcguffin/wp-access-areas.git`

4. If you want to update to the latest files (be careful, might be untested on Your WP-Version) type `git pull´.

= I found a bug. Where should I post it? =

I personally prefer GitHub, to keep things straight. The plugin code is here: [GitHub](https://github.com/mcguffin/woocommerce-payforpayment)
But you may use the WordPress Forum as well.

= I found a bug and fixed it. How can I contribute? =

Either post it on [GitHub](https://github.com/mcguffin/wp-access-areas) or—if you are working on a cloned repository—send me a pull request.


== Screenshots ==

1. User interface. You can find this in every payment gateway configuration.


== Changelog ==

= 1.3.5 =
- Fix: make it work with stripe for woocommerce by Stephen Zuniga

= 1.3.4 =
- Code Refactoring: set plugin textdomain to plugin slug
- Translations: Minor correction in español and german translations

= 1.3.3 =
- Feature: Minimum and maximum charges.

= 1.3.2 =
- Feature: Deactivate if WooCommerce version is below requirement.
- Fix: Missing Taxes

= 1.3.1 =
- Fix Admin: Payment gateway Class not found (may occur with 3rd party gateways)
- Fix: textdomain loading
- Update turkish localisation

= 1.3.0 =
- Feature: Enhanced UI
- Feature: Select tax class to be applied to payment fee
- Feature: Select if cart taxes will be included on payment fee calculation
- Feature: Placeholders in fee title.
- Fixes: completely repeat all woocommerce tax and fee calculation steps after payment fee has been added. 

= 1.2.5 =
- Fix: incorrect fee calculation.

= 1.2.3 =
- Fix: Safely Restrict payment fee to 2 Decimals.

= 1.2.2 =
- Fix: [Calculate taxes](http://wordpress.org/support/topic/cant-use-the-plugin-generate-false-amount-in-adding)
- Fix: cart contents taxes and shipping taxes included into fee calculation
- Refactoring: Discard cart_has_fee() check, as it is already done by woocommerce

= 1.2.1 =
- Feature: [Calculate custom fee](http://wordpress.org/support/topic/not-calculating-custom-fees)

= 1.2.0 =
- Feature: add option to disable payment fee when free shipping is selected
- Feature: add pay4pay column in woocommerce checkout settings
- Plugin-API: add filter `woocommerce_pay4pay_apply`
- Code Refactoring: separated admin UI from frontend to keep things lean.
- Code Refactoring: use function <code>WC()</code> (available since WC 2.1) in favour of <code>global $woocommerce</code>.
- Compatibility: requires at least WC 2.1.x, 

= 1.1.1 =
- Added wpml configuration file to keep compatibility with http://wordpress.org/plugins/woocommerce-multilingual/

= 1.1.0 =
- Added option to include shipping cost in fee calculation
- Fixed issue where malformed amounts where sent to external payment services in WC 2.1.6

= 1.0.2 =
- Fixed an issue where Pay4Pay options did not show up after saving checkout settings in WC 2.1.0
- Updated turkish translation ([Thanks a lot!](https://www.transifex.com/accounts/profile/TRFlavourart/))

= 1.0.1 =
- Fix plugin URL

= 1.0.0 =
- Initial release


== Upgrade notice ==
Requires at least WooCommerce 2.2.
