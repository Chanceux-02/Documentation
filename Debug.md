# Debugging ideas

1. [To show the element that you click without using id, classes, or element](#to-show-the-element-that-you-click-without-using-id-classes-or-element)
2. [Debugging if its really targetting the element and applied the changes](#debugging-if-its-really-targetting-the-element-and-applied-the-changes)
2. [Debugging to show the raw queries](#debugging-to-show-the-raw-queries)

## To show the element that you click without using id, classes, or element
* It will show the element that you click in the console.
```js
document.addEventListener('click', function(event) {
  console.log(event.target);
});

or

document.addEventListener('click', function(event) {
  document.querySelector('.sub-list-title').click();
});
```

## Debugging if its really targetting the element and applied the changes
* It will add test class in the element so that you can see where its position.
```js
$(target).addClass('TEST HEREEE');
```

## Debugging to show the raw queries
* It will show you the raw queries.
```php
//change the core.php deug = 2
CakeLog::debug('---- LOU DEBUG '.json_encode($this->PutYourModelHere->getDataSource()->getLog(false, false)));
```
