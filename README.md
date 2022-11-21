# alpine-js-breadcrumbs
Makes an object of breadcrumbs (and/or search queries) and does other breadcrumb related things. 
Check the comments inline in the code. Pretty raw and not tested carefully at all, but seems to be working and easy enough to modify/customize.

# Note
This is an experiment and by no means finished/production ready and has not been carefully tested.  Sure it's got some bugs. This does not do any 'seo' schema yada yada or anything like that. It's just an than attempt to build an object of names and links from a url string that you can use to make your own breadcrumbs. Just an experiment and prob not the best way about it...but who cares.

# Why?
If you want a quick and dirty way to get breadcrumbs as data in Alpine so you can do stuff/display them perhaps this is interesting for you.  I needed a way to get breadcrumbs from a url so started writing it and just kept adding to it.

For example, if ajax-ing in content and not updating the url, but you want to extract some links and names (breadcrumbs) from the string, this does it. You then have to use that data in your template as you see fit.

You can also turn query strings into breadcrumb like object with name/url. Why? Not sure, but I added it in case. 

#Usage 
Add the file to your js following the standard procedures for Alpine data or use the inline script in this repo

In your html add <div x-data="breadcrub()"></div> and the rest is up to you configure the options.

# You can:
- Get an array of breadcrumbs with name, url from either the current window location OR a custom href. Custom href means you give it a url like http://dogs.com/dogs/cats and you'll get something like:
[
    {
        "name": "Home",
        "path": "/"
    },
    {
        "name": "Dogs",
        "path": "/dogs"
    },
    {
        "name": "Cats",
        "path": "/dogs/cats"
    }
]
- Blacklist certain urls or keywords (this is a bit rough, but works ok). You may wish to edit things like for exact match or includes etc.

customBlacklist: [
		'http://cats.com',
	], 
  
  Will do nothing but disable breadcrumbs and return an empty array of breadcrumbs if the url is http://cats.com
  
- String replacement - For example if your custom rules for string replacement are:
customReplacements: [
		{
			find: 'Cats',
			replace: 'I said dogs!',
			path: '',
		},
		{
			find: 'I said dogs!',
			replace: 'No, I said cats',
			path: '',
			pattern: 'https://dogs.com/dogs/(.*)',
		},
]
You should get get:
[
    {
        "name": "Home",
        "path": "/"
    },
    {
        "name": "Dogs",
        "path": "/dogs"
    },
    {
        "name": "No, I said cats",
        "path": "/dogs/cats"
    }
]

- Remove the home link 
- Use a custom icon for the home link
- Make the home (or the first breadcrumb) say 'back'
- Make the back button use the referrer url (previous url) if it exists on same domain or fallback to the default. 
- Option for back icon (alt icon)
- Remove the first item or last item
- Replace underscores and dashes
- Use the doc title for the last item name
- Remove (ignore) query strings. 
- Title case or lower case
etc...

