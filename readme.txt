=== RSS Retriever Lite ===
Tags: rss, autoblogging, aggregator, wpml, woocommerce
Requires at least: 5.0
Tested up to: 6.8
Requires PHP: 7.4
Stable tag: 1.0.2
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Lightweight feed importer for WordPress with support for RSS, Atom, Google Product Feed, Yandex feeds, YouTube and more.

== Description ==

RSS Retriever Lite is a feed importer for WordPress. It allows you to import and publish content from various feed sources directly into your site.

**Features:**

- Full support for RSS and Atom feeds
- YouTube video feeds (channels and playlists)
- Google Product feed import
- Yandex Product feed import
- Support for compressed feeds (ZIP, GZIP, BZ2)
- Automatic feed updates
- Advanced post filtering
- Scheduler with flexible intervals and delayed publication
- Feed translation via Google, Yandex and DeepL APIs
- Support for Polylang and WPML multilingual plugins
- Support for custom post types and taxonomies (e.g. WooCommerce products)
- Automatic WooCommerce tag and category generation
- Smart autotagging and categorization
- Fully customizable HTML post templates with placeholders
- Automatic embedding of relevant YouTube videos in posts
- Post lifetime control to ensure content freshness
- Post thumbnail generation
- FIFU plugin integration for thumbnail hotlinking
- RSS media attachment support
- PNG image conversion to JPEG and WebP
- WordPress media library integration
- Automatic conversion of character encodings to UTF-8
- HTML cleanup and sanitization
- Custom HTML tag removal
- Custom user-agent and HTTP header support

== Installation ==

1. Upload the plugin files to the `/wp-content/plugins/rss-retriever/` directory, or install the plugin through the WordPress plugins screen directly.
2. Activate the plugin through the 'Plugins' screen in WordPress.
3. Go to the plugin settings page and configure your feed sources.

== Frequently Asked Questions ==

= Can I customize the layout of imported posts? =
Yes. The plugin includes powerful HTML post templates for titles, slugs, content, and excerpts. You can use placeholders such as `%post_title%`, `%post_content%`, `%post_excerpt%`, or `%xml_tags[...]%` to design your own structure. This gives you full control over how imported articles or products look in WordPress - from simple layouts to complex, SEO-optimized templates that automatically include dynamic data from the feed.

Examples:
- To add a link back to the original source at the end of each post: `Source: %link%`
- To display the publication date from the feed: `Published on %post_date%`

These templates make it easy to enrich your posts with useful information, improve SEO, and maintain a consistent style across all imported content.

= How to import content into WooCommerce products? =
The plugin can import any supported feed (RSS, Google Product Feed, Yandex Product Feed) as WooCommerce products.

To do this, select **product** in the **Post type** dropdown. After that, in the **Custom taxonomies** section you will see additional text fields: **Brands**, **Product categories**, **Product tags**, and **Product shipping classes**. You can enter values here separated by commas and/or use placeholders. For example, `%xml_tags[g:price]%` when importing from a Google Product Feed, or `%xml_tags[price]%` when importing from a Yandex Market (YML) feed.

Optionally, you can enable the **Categories to WooCommerce** checkbox to automatically convert categories from an RSS feed into WooCommerce product categories.

= Can the plugin automatically assign tags to imported posts? =
Yes. If you enable the **Auto tags** option, the plugin will scan the content of each imported post and automatically apply tags that already exist in your WordPress site whenever matching words are found in the text.

= Can I import YouTube channel and playlist feeds? =
Yes. YouTube video feeds are supported.

For YouTube, you need to use the official feed URLs that Google still provides.

Examples:
- https://www.youtube.com/feeds/videos.xml?channel_id=UC_x5XG1OV2P6uZZ5FSM9Ttw
- https://www.youtube.com/feeds/videos.xml?playlist_id=PL41UI99jyjP9eu9M76TIwQ-ihpvr7cs9n

When adding such a feed, go to the feed settings **Media handling** in the dropdown **Post thumbnails**, select **Create from media attachment**. YouTube provides thumbnails via `<media:thumbnail>` in the feed (as media attachments), so this option ensures that each imported post gets a proper WordPress featured image.

= How can I import feeds with multiple language versions (WPML or Polylang)? =
If you are using WPML or Polylang and have more than one language on your site, you can create translated versions of each imported post automatically.

For example, if your site has English (EN) as the main language and French (FR) and German (DE) as additional languages, you need to add the same feed three times in the RSS Retriever Syndicator. We recommend adding the language code (EN, FR, DE) to the feed name so it is easier to manage.

In the settings of each feed instance:
1. Select the correct language group (EN, FR, or DE).
2. Enable automatic translation into that language.

This way every imported post will have its own translated version in the correct language group, fully integrated with WPML or Polylang.

= How can I automatically remove outdated posts or products? =
You can control this using the **Post lifetime** setting. It defines the period in hours after which an imported post will be automatically deleted. If you do not want to limit the lifetime, set this parameter to **0**.

This is especially useful when importing WooCommerce products or any other content where freshness matters, such as product feeds, time-limited offers, or news updates.

= Can I control or randomize the publication dates of imported posts? =
Yes, the plugin allows you to adjust publication dates using the **Post date adjustment range** setting. This range defines a random offset (in minutes) that will be applied to each imported post. For example, if you set `[0..60]`, each post date will be shifted forward by a random value between 0 and 60 minutes. Negative values are also supported, so a range like `[-60..-10]` will backdate posts into the past.

This option works together with the **Base date** setting, which can be either **Get date from post** or **Use syndication date** (the current time). Combined, these settings give you full flexibility: you can backdate imported content, spread posts more evenly in time, or even schedule them into the future.

= Can I translate imported content automatically? =
Yes, the plugin supports automatic translation via Google, Yandex, and DeepL APIs.

For **Yandex Translate**, you can use API keys from both versions - v1.5 and v2 are supported.

For **DeepL**, both free and paid API keys work. If you enter a free API key on the **Accounts** page, make sure to also enable the **Use DeepL API Free** option in the translator settings so the plugin knows which API endpoint to use.

= When would I need to set a custom User-Agent or HTTP headers? =
Some websites restrict access to their feeds or content depending on the client making the request. By setting a custom **User-Agent** and additional **HTTP headers**, the plugin can mimic a regular browser or pass required authorization data. This helps when importing from sources that block default WordPress requests, require API keys, or expect specific headers in order to deliver the feed correctly.

= How does the plugin handle automatic feed updates? =
You can choose between two modes for pulling feeds automatically:

- **Auto** - uses the built-in WordPress scheduler (WP-Cron). This option works out of the box and does not require any server configuration.
- **Cron job or manually** - lets you run imports via a real server-side cron job or by triggering the process manually. This mode is recommended if you want more reliable scheduling or full control over when and how often feeds are updated.

With both options available, you can decide whether to rely on WordPress's internal scheduler or configure a system-level cron job for maximum precision and stability.

= How to enrich imported posts with relevant YouTube videos? =
You can automatically embed YouTube videos into your imported posts using the `%youtube_video[keyword]%` placeholder.

Example: `%youtube_video[%post_title%]%`

The value inside the brackets can be any text string or another supported placeholder such as `%post_title%`, `%xml_tags[name]%`, etc.

= Why does the featured image appear twice in posts? =
This usually happens because the plugin automatically sets a featured image (taken from the RSS enclosure, the first image in the post, or another source), and at the same time your WordPress theme is programmed to display the featured image above the post content. As a result, the same image is shown twice.

How to fix it:
1. Check your theme settings - many themes provide an option to hide the featured image on single post pages.
2. If your theme does not have such an option, you can create a child theme and remove the call to `the_post_thumbnail()` (or `get_the_post_thumbnail()`) from the single post template.
3. As an alternative, you can install the free plugin [Featured Image from URL (FIFU)](https://wordpress.org/plugins/featured-image-from-url/), which has a "Hide Featured Media" option that prevents featured images from being displayed in single posts while keeping them in archives and listings.

== External services ==

This plugin connects to external translation APIs (Google Translate, Yandex Translate, DeepL)
in order to translate imported content. Requests may include text to translate and
language codes. These services are used only if the user configures an API key.

- Google Translate API: https://cloud.google.com/translate/docs, https://policies.google.com/privacy
- Yandex Translate API: https://yandex.com/dev/translate/, https://yandex.com/legal/confidential/
- DeepL API: https://www.deepl.com/pro-license, https://www.deepl.com/privacy

== Changelog ==

= 1.0.2 =
* Fix feed options saving: restored original logic for text fields and checkboxes, added wp_unslash() and sanitize_text_field() for security

= 1.0.1 =
* %youtube_video[keyword]% placeholder added

= 1.0.0 =
* Initial release

== Upgrade Notice ==

= 1.0.2 =
Fix feed options saving: restored original logic for text fields and checkboxes, added wp_unslash() and sanitize_text_field() for security

= 1.0.1 =
%youtube_video[keyword]% shortcode added

= 1.0.0 =
Initial release
