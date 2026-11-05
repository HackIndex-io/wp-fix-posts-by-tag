# Posts By Tag (HackIndex Patched)

> [!IMPORTANT]
> This is an unofficial fork of [Posts By Tag](https://wordpress.org/plugins/posts-by-tag/) by [Sudar Muthu](https://github.com/sudar/posts-by-tag). HackIndex is not affiliated with or endorsed by the original author.

The original plugin is no longer maintained and its latest release (3.2.1) has a [known vulnerability](https://www.wordfence.com/threat-intel/vulnerabilities/id/92a81d4a-58ed-4812-a1f8-db86e410393c). HackIndex maintains this fork for security fixes only:

- We fix security issues and keep the plugin working on current WordPress and PHP versions.
- We do not add features or change how the plugin works.
- It is a drop-in replacement: same plugin folder, `[posts-by-tag]` shortcode, widget, template functions and custom fields, so your widgets and posts keep working.

Need help with this fork? [Open an issue](https://github.com/HackIndex-io/posts-by-tag/issues) here, please don't contact the original author about it.

## What it does

Shows a list of posts from a set of tags in a sidebar widget, with the `[posts-by-tag]` shortcode or with the `posts_by_tag()` template function. The tags can also come from the current post, its slug or the "Posts By Tag Page Fields" box on the edit screen. See [readme.txt](readme.txt) for all options.

## Security fixes

### 3.2.2

- Contributor+ stored Cross-Site Scripting ([CVE-2025-62983](https://www.cve.org/CVERecord?id=CVE-2025-62983), [Wordfence advisory](https://www.wordfence.com/threat-intel/vulnerabilities/id/92a81d4a-58ed-4812-a1f8-db86e410393c)): the `link_target` shortcode attribute was printed in the `target` attribute of every link without escaping, so a contributor could add `[posts-by-tag link_target='x" onmouseover="...']` to a post and run scripts for every visitor. The link target and the other values in the post list are now escaped.
- Tag names are escaped in the CSS class of each post. Contributors can create tags, and a tag name with a quote broke out of the attribute.
- The widget title and tags in the "Posts By Tag Page Fields" box were saved and printed without any filtering, in the edit screen and in the widget. They are now sanitized on save and escaped on output, which also neutralizes values stored before the update.
- Post titles are escaped in the thumbnail `title` and `alt` attributes, and author names, tag links and the widget settings form are escaped too.
- Tag names and slugs are escaped for JavaScript when they replace `[TAGS]` or `[POST_SLUG]` in the Google Analytics event code.
- Fixed PHP 8 warnings (dynamic property, undefined variables)
- Tested with WordPress 7.1 and PHP 8.0 to 8.5

## Install

1. Download `posts-by-tag.zip` from the [latest release](https://github.com/HackIndex-io/posts-by-tag/releases/latest).
2. Upload the zip in **Plugins > Add New > Upload Plugin** and choose **Replace current with uploaded**. Your settings are kept.
3. Don't delete the original plugin first: deleting a plugin can run its uninstall and remove its settings.

WordPress does not update this fork automatically. Watch this repo's releases to get new security fixes.

## License

GPLv2 or later, like the original. See [LICENSE](LICENSE). Provided without any warranty.

All credit for the plugin goes to [Sudar Muthu](https://github.com/sudar/posts-by-tag). The full upstream history is kept in this repository, and [HISTORY.md](HISTORY.md) has the original changelog.
