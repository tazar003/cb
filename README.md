# Chargebee Membership WordPress Plugin

WordPress allows you to create websites and blogs and share Content, services, and products with users on the web. With Content generated through research reports, courses, online tutorials, and more every day, you can monetize your Content by setting up a paywall on your website.
A paywall is a way of gating your site's premium Content on a subscription basis.
With Chargebee's plugin for WordPress, you can implement a paywall on your site and charge users on a subscription basis. It allows you to restrict Content based on the subscription your customers have signed up for.

 Here's what you can do with it:
* Sync Plans from Chargebee to WordPress.
* Allow automatic Customer Portal access to all registered users via SSO.
* Sync Customer and Subscription creation details from WordPress to Chargebee.
* Insert shortcodes to show/hide content or forms.
* Configure Levels
* Create Subscriptions for a Customer.

Please note that this is a Beta version, so you might find things that don't work perfectly. :) If you find something that has to be fixed, please file an issue in the Git repo.

If you’ve added new functionalities that you think might be helpful for all, do send us a pull request. Your contribution would be greatly appreciated!

## Prerequisites
Ensure that you use these tools and their respective versions to set the plugin:
* WordPress version greater than 4.5.0
* PHP version 5.5.9 or greater
* MySQL version 5.6 or greater OR MariaDB version 10.0 or greater

## Installation
1. Navigate to  **Plugins>Add New Plugin** in your WordPress dashboard and click the Upload Plugin button at the top of the page. 
2. Upload the plugin's zip and click the "Install Now" button.
3. WordPress will automatically transfer the files, and you will see a screen that says, "Plugin installed successfully." Select the  **Activate Plugin link** below.
4. Upon activating, you will be redirected to the plugin's listing page, where a message from Chargebee will be displayed. Click on the message to start the setup process.
5. You will then be directed to Chargebee’s Settings page.

## Settings
### Integration
**Authentication**:
* Enter your "Chargebee site name" and "Chargebee API Key" under the "Integration" tab and Hit "Save API Key and Synchronize." You can retrieve the API from the Chargebee site under **Settings > Configure Chargebee > API Keys**.
* When a valid site name and API key are entered, your Plans (if any) from your Chargebee Site will automatically get imported into WordPress. You can view the plans under  **Chargebee > Products.** 									**Note**: Please try with Chargebee's TEST site. If you've tested your use cases and are satisfied with the plugin, you can sync your LIVE site.
**Set up Webhooks**
*  Click on "Add Webhook" under **Settings > Configure Chargebee > Webhooks**. 
* Copy the webhook URL from the plugin to your Chargebee site and add it to the form
* Enable "Protect webhook URL with basic authentication." Copy the username and password from the plugin and paste and hit "Create."


### General
   1. Default Membership Product: This enables you to select default plans for users. If a plan is selected, whenever a new user signs up, he will be subscribed to that plan. A Default plan can be a 0$ or a Free plan, configured in your Chargebee account
   2. Restricted Content Message: When a specific Level is set to restrict content and a user who doesn't belong to that level tries to access the Content, this message will be displayed. The user's level will be dynamically set using  {user_level}.


## Products
Verify Products Synced from Chargebee to WordPress. All your plans, defined in Chargebee, are synced automatically as Products in your WordPress account.

## Levels
Define Levels for your users
Levels are a method by which you can define access restrictions on your WordPress account. 
Create a Level, and select all your plans that fall under this level of access. A single level can have multiple products.

## Content Restriction

Content restrictions can be set in 3 ways: 
* Assigning a Level to a category & then assigning that category to post(s).
* Assigning a Level to a page/post from within the page/post screen using the “Chargebee Content Restriction” meta box. 
     or
* By using shortcodes in the content.


## Shortcodes

| Show Content | [cb_content_show level="level_id"] Your content [/cb_content_show]| This content will be shown to users who are on the plan associated with the Level ID mentioned in the shortcode.   |
|------------------------------------:|---------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| Hide Content                        | [cb_content_hide level="level_id"] Your content [/cb_content_hide]| This content will be hidden for the users who are on the plan associated with Level ID mentioned in the shortcode. |
| Checkout Subscription               | [cb_product_subscribe_hosted class="btn" product_id="item_price_id"] Subscribe [/cb_product_subscribe_hosted] | End users can checkout the subscription by clicking the link, which will load Chargebee's in-app checkout.         |
| Manage Subscription/ Account portal | [cb_account_portal class="btn"] Manage Subscription [/cb_account_portal]                                | End users can manage their subscription by clicking the link, which will load Chargebee's self-serve portal.       |
| Display Subscription                | [cb_display_subscription]                                                                               | End users can view their subscription details.                                                                     |
| Show content(guest users)           | [cb_not_logged_in] Your content [/cb_not_logged_in]                                                     | This content will be shown to users who have not logged in to your website.                                        |
| Show content(paid)                  | [cb_paid_subscription] Your content [/cb_paid_subscription]                                             | This content will be shown to users on paid plans.                                                                 |
| Show content(free)                  | [cb_free_subscription] Your content [/cb_free_subscription]                                             | This content will be shown to users on free plans.  |

* Replace "Product ID" in the Product Subscribe shortcode with the Product ID of the plan that needs to be represented. The product ID of a plan is similar to the Item Price ID on your Chargebee site.
* Make sure the "level_id" placeholder is replaced with an actual level_id when using shortcodes. If "level_id" is not mentioned for [cb_content_show] shortcode, the content will be shown to all users. Similarly, the content will be hidden for all users if "level_id" is not mentioned for [cb_content_hide] shortcode.



## Supported webhook event

Data flow supported from Chargebee to WordPress
 * subscription_created
 * subscription_changed
 * subscription_deleted
 * subscription_cancelled
 * item_price_created
 * item_price_deleted
 * item_price_updated
 * customer_created

## Limitations

1. Plans alone can be synced from Chargebee to Wordpress.
2. Single-page Checkout is not supported. In-app Checkout will load when your customer is making a purchase.
3. Pricing table is not supported. However, if you would like to display multiple plans on a single page, you can use the Subscribe shortcode for each plan. This way, your customers can checkout directly from one page.
4. Multi sites in Wordpress is not supported.
