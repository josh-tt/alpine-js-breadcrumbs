# alpine-js-breadcrumbs
Makes an object of breadcrumbs (and/or search queries) and does other breadcrumb related things. 
Check the comments inline in the code. Pretty raw and not tested carefully at all, but seems to be working and easy enough to modify/customize.

# Note
This is an experiment and by no means finished/production ready and has not been carefully tested.  Sure it's got some bugs. This does not do any 'seo' schema yada yada or anything like that. It's just an than attempt to build an object of names and links from a url string that you can use to make your own breadcrumbs. Just an experiment and prob not the best way about it...but who cares.

# Why?
If you want a quick and dirty way to get breadcrumbs as data in Alpine so you can do stuff/display them perhaps this is interesting for you.  I needed a way to get breadcrumbs from a url so started writing it and just kept adding to it.

You can also turn query strings into breadcrumb like object with name/url. Why? Not sure, but I added it thinking of displaying 'tags' for search queries

#Usage 
Add the file to your js following the standard procedures for Alpine data 
import breadcrumbs from './yourpath/breadcrumbs';
Alpine.data( 'breadcrumbs', breadcrumbs );
window.Alpine = Alpine;
Alpine.start();

#Example

```
<div x-data="breadcrumbs({href:'http://test.com/cats/dogs/birds'})">
<template x-for="(crumb, index) in allCrumbs" :key="index">
	<li class="flex">
	    <div class="flex items-center">
		<svg class="h-full w-6 flex-shrink-0 text-gray-200" viewBox="0 0 24 44" preserveAspectRatio="none" fill="currentColor" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
		    <path d="M.293 0l22 22-22 22h1.414l22-22-22-22H.293z" />
		</svg>
		<a :href="crumb.path" x-text="crumb.name" class="ml-4 text-sm font-medium text-gray-500 hover:text-gray-700"></a>
	    </div>
	</li>
</template>
</div>
```
# Options (some names have changed in code that are listed below - no time to update) :
```
disabled, // Disables the crumbs by emptying the array which allows automatic hide/show. Bypassed urls will set disable to be true.
	href, // The current url or the user input url
	home, // Show the home or first crumb (if back is on, back is home and home is first)
	allowOneItem, // show the breadcrumb even if there is only one item
	back, // Replace the first item with 'back' text
	referrerUrl, // use the window referrer url as the back url
	last, // Show last item
	title, // use document title for the last item
	lettercase, // uppercase, lowercase, capitalize
	stripDashes, // Remove dashes from the crumb names
	stripUnderscores, // Remove underscores from the crumb names
	trailingSlash, // Add trailing slash to the generated hrefs
	whitelistUrls: [
		...whitelistUrls, // User defined urls to enable breadcrumbs on - setting disabled to false (opposite of blacklistUrls) - // Use a regex wildcard to match multiple urls
		// 'http://something.com/foo/*',

	],
	blacklistUrls: [
		...blacklistUrls, // User defined urls to bypass (others below are built-in - can't be changed) - // Use a regex wildcard to match multiple urls
		// 'http://something.com/bar/*',
	],
	stringReplace, // Enable string replacement
	stringReplacements: [
		...stringReplacements, // User defined string replacements (others below are built-in - can't be changed)
		{
			find: 'bird',
			replace: 'birdie',
			path: '/dogs/cats/some-bird',
			pattern: '',
		},
		{
			find: 'BAZ',
			replace: 'replaced texts',
			path: '/foo/baz',
			pattern: '',
		},
		{
			find: '',
			replace: '',
			path: '',
			pattern: 'https://dogs.com/dogs/(.*)', // Todo: Reimplement pattern from previous version
		},
	],
	showFirstOnly, // only show the first item
	showPreviousOnly, // only show the previous item
	svg, // 'home', 'back', 'alt'
	homeSvg, // Svg markup for home
	backSvg, // Svg markup for back
	altSvg, // Svg markup for alt```
etc...

