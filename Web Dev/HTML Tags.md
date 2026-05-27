## iframe
`<iframe src="url" width="x" height="y">`
- Horrible for SEO
	- Crawlers can't look inside iframes


## Meta Tags

### Description
Sets the description for search engines.
`<meta name="description" content="describing text"`

### Content Width
Sets the content width in the browser. Use the following line to keep the content width dynamically scaled with the browser window.

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

## Media Tags

These tags *embed* media into the website, allowing the user to view it in real-time.
If you want to add media *downloads*, just use a `<a>` tag instead.

### Audio


### Video
```html
<video controls muted loop poster='url>`
<source src='video_source.mp4' type='video/mp4'>
```