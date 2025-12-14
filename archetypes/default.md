+++
date = '{{ .Date }}'
draft = true
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
description = ""
summary = ""
# image = "cover.jpg"
# categories = []
+++

<!--
NEW POST CHECKLIST:

1. description (REQUIRED)
   - Appears on site cards and social media preview cards
   - Keep concise: 1-2 sentences describing the post

2. summary (REQUIRED for social sharing)
   - Appears in RSS feed and LinkedIn cross-posts via Zapier
   - Can be same as description, or a slightly different hook
   - If omitted, RSS uses first paragraph of content instead

3. image (OPTIONAL)
   - Featured image for post cards
   - Place image file in same directory as index.md (page bundle)
   - Will be automatically optimized to AVIF/WebP

4. categories (OPTIONAL)
   - For organizing posts on the site

TIP: The summary appears as the lead-in text on LinkedIn,
followed by the URL (which shows the description in the card).
Consider how they read together.

SEE: README.md for full RSS/LinkedIn integration details
-->
