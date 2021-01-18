---
---
# Jekyll template with navbar

This repo only deals with the website navigation and structure.

## Navigation Links

To set what links appear in the top navigation edit `_data/menu.yml`. Use the following format to set the URL and title for as many links as you'd like.

```yaml
group_name:
  - name:  Page name
    url:   /pageURL/
    submenu:
      - name: Page name
        url:  /pageURL/
```

We `for` loop  `group_name` = `navigation`.
