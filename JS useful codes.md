#Useful codes

### Content Links
1. [For saving data in local storage `localStorage`](#get-the-array-difference-in-two-group-of-arrays)
2. [For `searching` elements without loop in JS](#get-all-the-data-that-exists-it-these-two-variables)



## For saving data in local storage `localStorage`
* It will save the data in local storage with key like cahce but it dont have expiration

```js

// Set an item in Local Storage
localStorage.setItem('key', 'value');
// Get an item from Local Storage
const retrievedValue = localStorage.getItem('key');
// Remove an item from Local Storage
localStorage.removeItem('key');
// Clear all items from Local Storage
localStorage.clear();


```

## For `searching` elements without loop in JS
* It will search all of the elements that you want using selector and will return it based on your condition

```js

let lastStatusNot3 = $('.student-inquiry-status').filter(function() {
	return $(this).val() !== '3';
}).last();


```
## Checking if the type of navigation that occurred on the page is NOT a page `reload`.
* It evaluates whether the current navigation is NOT a page reload, and you can add else to do some action is the page is reloaded.

* Deprecated
```js

// Check if the page navigation type is NOT a page reload (type 1)
if (performance.navigation.type !== 1) {
    // Code to be executed when the condition is true
    // This is where you can handle specific actions or logic for non-reload navigation
}

```
* Modern
```js

// Get the navigation timing object
const navigation = performance.getEntriesByType('navigation')[0];

// Check if the navigation is a reload
if (navigation.type === 'reload') {
  console.log('Page reloaded');
}
```


## Checking if the user will leave the page and retain the reload behaviour.
* It evaluates if the user will leave the page .

```js

window.addEventListener('beforeunload', function (event) {  // checking if user will leave/close/reload/clear session
	if (performance.navigation.type !== 2) {   // checking if not reload behaviour
		$.each(localStorage, function (key, value) { //run the desired action
			if (key.startsWith("policyInstructorKey_")) {
				localStorage.removeItem(key);
			}
		});
	}
});

```


## For smooth scrolling 
* smooth scrolling with url validation
* `https://example.com/zh-tw/textbook/page-detail/1/1`   &&   `https://example.com/textbook/page-detail/1/1`

```js

$(function(){
	$(document).on('click', 'a[rel="smoothscroll"]', function() {
		var speed = 600;
		var href = $(this).attr("href");
		var target = $(href == "#" || href == "" ? 'html' : href);
		var position = target.offset().top;
		$('body, html').animate({scrollTop:position}, speed, 'swing');
		
		$('#consolelog').html('href:' + href + 'target:' + target + 'position:' + position);

		var url = $(window.parent.location).attr('href').split('/');

		var langCode = ['zh-tw'];

		//check if it has a language code
		if (typeof url[3] !== "undefined" && langCode.includes(url[3])) {
			// Check if url[4] is "textbook"
			if (typeof url[4] !== "undefined" && url[4] === "textbook") {
			  // Perform scroll animation
			  $('body, html', window.parent.document).animate({ scrollTop: position + 130 }, speed, 'swing');
			}

		  } else {

			if (typeof url[3] !== "undefined" && url[3] === "textbook") {
				$('body, html', window.parent.document).animate({ scrollTop: position + 130 }, speed, 'swing');
			}
		  }

		return false;
	});
});

```

