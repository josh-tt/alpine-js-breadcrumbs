# alpine-js-breadcrumbs
Makes an object of breadcrumbs (and/or search queries) and other breadcrumb related things. 
Check the comments inline in the code. Pretty raw and not tested carefully at all, but seems to be working and easy enough to modify/customize. 
# Why?
If you want a quick and dirty way to get breadcrumbs as data and do stuff/display them.  I needed a way to get breadcrumbs from a url and a flexible way to make changes to them. For example, if ajax-ing in content and not updating the url. 
You can also make get query strings in an object like the breadcrumbs if needed.
# You can:
- Get an array of breadcrumbs with name, url from either the current window location OR a custom href. 
- Blacklist certain urls or keywords (this is a bit rough, but works). You may wish to edit things like for exact match or includes etc.
- Remove the home link 
- Use a custom icon for the home link
- Make the home (or the first breadcrumb) say 'back'
- Make the back button use the referrer url (previous url) if it exists on same domain or fallback to the default. 
- Option for back icon (alt icon)
- Remove the first item or last item
- Replace underscores and dashes
- Use the doc title for the last item name
- Remove (ignore) query strings. 
etc...

This does not do any 'seo' yada yada or anything other than attempt to build an object of names and links that you can use to make your own breadcrumbs. 
