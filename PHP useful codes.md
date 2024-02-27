#Useful codes

### Content Links
1. [Get the array difference in two group of arrays](#get-the-array-difference-in-two-group-of-arrays)
2. [Get all the data that exists it these two variables](#get-all-the-data-that-exists-it-these-two-variables)
2. [To filter data that you want to save without using a loop using array_filter()](#to-filter-data-that-you-want-to-save-without-using-a-loop-using-array_filter)


## Get the array difference in two group of arrays
* In this example it will get all of the arrays in $firstArrays variable that dont exists in $secondArrays variable (the difference of the $firstArrays)
```php
$getAllDiff = array_diff($firstArrays, $secondArrays);
```
## Get all the data that exists it these two variables
* In this example it will get all of the data that exists in both variables
```php
$getTheSameDatas = array_intersect($firstDatas, $secondDatas);
```
## Batch process code logic
* It will slice your datas in 50 batches
```php
$batchSize = 50;
$totalIds = count($yourHundredIds);
$startIndex = 0;

while ($startIndex < $totalIds) {
  // Get the next batch of 50 IDs
  $batchIds = array_slice($yourHundredIds, $startIndex, $batchSize);

  // You can use now the $batchIds
  // Do something

  // Increment the start index for the next batch
  $startIndex += $batchSize;

}
```
## To filter data that you want to save without using loop using `array_filter()`
* It will remove the 103 id in list without yung loops.

```php

<?php

$idList = [101, 102, 103, 104, 105]; 

$params = [ 'remove_this' => 103 ]; // pwedi biskan number not array

$excludeId = $params['remove_this'];
$filteredIds = array_filter($idList, function ($id) use ($excludeId) {
    return $id != $excludeId;
});

// Display the teacher ID to exclude
echo "Excluding teacher ID: $excludeId" .PHP_EOL .PHP_EOL;

// Display the filtered list using $filteredIds
echo "On-air teacher IDs after excluding $excludeId: " . implode(', ', $filteredIds) . PHP_EOL;

// Example output:
// Original On-air teacher IDs: 101, 102, 103, 104, 105
// Excluding teacher ID: 103
// On-air teacher IDs after excluding 103: 101, 102, 104, 105
?>

```


## To get all of the teacher ids without looping in associative array format `array_map()`
* It will get all of the ids inside of `$data` without using loop.
  
```php
<?php
// Example data
$data = [
    ['Teacher' => ['id' => 101]],
    ['Teacher' => ['id' => 102]],
    ['Teacher' => ['id' => 103]],
];

// Applying array_map
$teacherIds = array_map(function ($teacher) {
    return $teacher['Teacher']['id'];
}, $data);

print_r($teacherIds);
// Result
// Array
// (
//     [0] => 101
//     [1] => 102
//     [2] => 103
// )

```

## skip the proccess using `continue`
* It will explicitly skip the process, might be useful someday
* 
```php
<?php

// Sample array with items
$numbers = [1, 2, 3, 4, 5, 6];

foreach ($numbers as $number) {
    // Check if the number is not divisible by 2
    if ($number % 2 !== 0) {
        echo "Skipping processing for odd number $number\n";
        continue; // Skip the rest of the loop code for this iteration
    }

    // Process each $number item here (for even numbers)
    $result = $number * 2;
    echo "Processing item $number: Result = $result\n";
}

?>

```

## For `dynamic` initializing properties in class
* It will initialize the properties dynamicaly so you cant declare all of that manually

```php

class CommonTable {
    private $properties = [];

    public function __construct($data) {
        if (is_array($data)) {
            foreach ($data as $var => $val) {
                $this->properties[$var] = $val;
            }
        }

        //check the properties that initialized
        print_r($this->properties['id']);
        die();
    }
}


```

## For `caching` in PHP
* It will cache the data and you can manipulate it using this code

```php

//exapmle value
$toSave = 'this is example data';
//declare
$myMemcached = new myMemcached();
//make your key
$memKey = 'put_your_unique_key_here_'.$id;
// save the data
$myMemcached->set([
	'key' => $memKey,
	'value' => $toSave,
	'expire' => 60 // 1 minute
]);
//get the cached data
$cachedData = $myMemcached->get($memKey);
//delete the data 
$myMemcached->delete($memKey);


```


