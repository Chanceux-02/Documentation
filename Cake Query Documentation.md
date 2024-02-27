# Cake Query Documentation

## Contents Link
1. [Update multiple fields using condition](#update-multiple-fields-using-id)
2. [Get all the data in database](#get-all-the-data-in-database)
3. [Get all the data with condition](#get-all-the-data-with-condition)
4. [Get all the data field/s with condition](#get-all-the-data-fields-with-condition)
5. [Get all the data of field/s with condition NOT](#get-all-the-data-of-fields-with-condition-not)
6. [Delete multiple data in database base in your condition](#delete-multiple-data-in-database-base-in-your-condition)
7. [Save multiple datas](#save-multiple-datas)
8. [Use open/close replica](#use-openclose-replica)
9. [Load Model](#load-model)

## Update multiple fields using id
* It will update the field/s (first array) where condition = 1 (second array)
```php
	$this->YourModel->updateAll(
				array(
					'YourModel.your_table_column' => "'Your Video name (need inside of qoutes if string like this)'",
					'YourModel.your_table_column2' => 27
				),
				array(
					'YourModel.your_table_column' => 1
				)
			);
```

## Get all the data in database
* It will get all of the data in database like select * from table
 ```php
$response = $this->YourModel->find('all');
```

## Get all the data with condition
* It will get all of the data in database based on your condition like select * from table where condition = value
 ```php
$response = $this->YourModel->find('all', [
				'conditions' => [
					'your_table_column ' => 'value', 
				]
			]);
```

## Get all the data field/s with condition
* It will get fields data in database based on your condition like select field from table where condition = value
 ```php
$response = $this->YourModel->find('list', [
				'field' => ['your_table_column' =>  'value']
			]);
```

## Get all the data of field/s
* It will get fields data in database 
 ```php
$response = $this->YourModel->find('list', [
			'fields' => ['your_table_column'],
		]);
```

## Get all the data of field/s with condition NOT
* It will get all fields data in database exept for your condition
 ```php
$response = $this->YourModel->find('list', [
			'fields' => ['your_table_column'],
			'conditions' => [
				'NOT' => [
					'your_table_column' => 'value'
				]
			]
		]);
```

## Delete multiple data in database base in your condition
* It will delete the datas in database base in your multiple ids
 ```php
$this->YourModel->deleteAll([
						'your_table_column IN' => $YourMultipleIdsInsideVar, 
					], false);
```

## Delete multiple data in database base with multiple condition
* It will delete the datas in database base in your multiple condition
 ```php
$this->YourModel->deleteAll([
							'your_table_column IN' => $groupOfIds,
							'your_table_column2' => 'value'
						], false);
```
## Save multiple datas
* It will save multiple datas
 ```php
$dataToSave = [];
			
foreach ($personData['items'] as $items) {
	$check = $items['id'];
		$dataToSave[] = [
			'your_table_column' =>  $items['id'],
			'your_table_column2' =>  $items['name']['localized']['title'],
			'your_table_column3' =>  $items['age']['categoryId'],
			'your_table_column4' => $items['address']
		];
}

if (!empty($dataToSave)) {
	try {
		$this->loadModel('YourModel');
		$this->YourModel->create();
		$this->YourModel->saveAll($dataToSave);
		echo 'Record saved successfully.';
	} catch (Exception $e) {
		//throw $th;
	}
}
```
## Use open/close replica
* Use this in every fetch query to avoid bugs
  ```php
	$this->YourModel->openDBReplica();
					$YourModel = $this->YourModel->find('list', [
						'fields' => ['your_table_column']
					]);
	$this->YourModel->closeDBReplica();
  ```

## Load Model
```php
$this->loadModel('YoutubePlaylist');
```

