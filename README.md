# RSS Retriever Lite

[![WordPress](https://img.shields.io/badge/wordpress.org-plugin-blue)](https://wordpress.org/plugins/rss-retriever-lite/)  
Lightweight feed importer for WordPress with support for RSS, Atom, Google Product Feed, Yandex feeds, YouTube and more.

Learn more at [rssretriever.com](https://rssretriever.com)

---

## Features

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

---

## Installation

1. Upload the plugin files to the `/wp-content/plugins/rss-retriever/` directory, or install the plugin through the WordPress plugins screen directly.  
2. Activate the plugin through the "Plugins" screen in WordPress.  
3. Go to the plugin settings page and configure your feed sources.  

---

## FAQ

### Can I customize the layout of imported posts?
Yes. The plugin includes powerful HTML post templates with placeholders such as `%post_title%`, `%post_content%`, `%post_excerpt%`, or `%xml_tags[...]%`.  
This gives you full control over how imported articles or products look in WordPress.

---

### How to import content into WooCommerce products?
Select **product** in the **Post type** dropdown. Additional taxonomy fields will appear for brands, categories, and tags.  
You can also enable **Categories to WooCommerce** to automatically convert feed categories into WooCommerce categories.

---

### Can the plugin automatically assign tags?
Yes. Enable **Auto tags** and the plugin will scan content for words matching existing tags in your site.

---

### Can I import YouTube channel and playlist feeds?
Yes. Supported feed URLs:  
- `https://www.youtube.com/feeds/videos.xml?channel_id=...`  
- `https://www.youtube.com/feeds/videos.xml?playlist_id=...`  

When adding such a feed, select **Create from media attachment** in **Post thumbnails**.

---

### How to work with WPML or Polylang multilingual sites?
Add the feed separately for each language (EN, FR, DE, etc.), assign language group, and enable automatic translation.  
This way each imported post will have translated versions connected in WPML/Polylang.

---

### How to automatically remove outdated posts?
Use the **Post lifetime** option to set how many hours an imported post should exist before auto-deletion.

---

### Can I randomize publication dates?
Yes. Use **Post date adjustment range** with values like `[0..60]` or `[-60..-10]` for flexible scheduling.

---

### Can I translate imported content automatically?
Yes. Supported APIs: Google Translate, Yandex Translate (v1.5 and v2), DeepL Free and Pro.

---

### When to set custom User-Agent or headers?
If a feed blocks default WordPress requests. You can mimic a browser or send API keys in headers.

---

### How does automatic feed update work?
Two modes:  
- **Auto (WP-Cron)** – built-in WordPress scheduler.  
- **Cron job/manual** – external cron for maximum reliability.

---

### How to enrich posts with YouTube videos?
Use placeholder `%youtube_video[keyword]%` (e.g. `%youtube_video[%post_title%]%`).

---

### Why does the featured image appear twice?
Because the theme displays the featured image and the plugin also inserts it.  
Solution: disable in theme, use child theme, or enable the **Hide Featured Media** option in FIFU.

---

## License

This plugin is licensed under the [GPLv2 or later](https://www.gnu.org/licenses/gpl-2.0.html).  