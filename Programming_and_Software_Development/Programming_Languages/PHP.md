# PHP Cheat Sheet

## Embedding PHP in HTML
```php
<?php
    // Your PHP code here
?>
```

## Comments
- **Single-line comments:**
  ```php
  // This is a single-line comment
  # This is another single-line comment
  ```

- **Multi-line comments:**
  ```php
  /*
   This is a multi-line comment
   spanning multiple lines
  */
  ```

## Naming Conventions
- **Variables:** Use camelCase starting with a lowercase letter.
  ```php
  $firstName = 'John';
  ```

- **Functions:** Use camelCase starting with a lowercase letter.
  ```php
  function calculateTotal() {
      // Function code
  }
  ```

- **Classes:** Use PascalCase (also known as UpperCamelCase).
  ```php
  class ProductItem {
      // Class code
  }
  ```

- **Constants:** Use uppercase letters with underscores.
  ```php
  const ACCESS_KEY = '123abc';
  ```

## Outputting Data
- **Using `echo`:**
  ```php
  echo 'Hello, PHP!';
  ```

- **Using `print`:**
  ```php
  print 'Hello, PHP!';
  ```

- **Debugging Output:**
  - **`var_dump()`:** Displays structured information about variables, including their type and value.
    ```php
    var_dump($variable);
    ```

  - **`print_r()`:** Prints human-readable information about a variable.
    ```php
    print_r($array);
    ```

## Variables
- **Declaration and Initialization:**
  ```php
  $name = 'Alice';       // String
  $isActive = true;      // Boolean
  $age = 30;             // Integer
  $height = 5.9;         // Float
  ```

- **Predefined Variables:**
  - `$GLOBALS`: Access global variables from anywhere in the script.
  - `$_SERVER`: Contains information such as headers, paths, and script locations.
  - `$_GET`: Collects data sent via URL parameters.
  - `$_POST`: Collects data from HTML form submissions.
  - `$_REQUEST`: Contains the contents of both `$_GET` and `$_POST`.
  - `$_SESSION`: Used to manage session data.
  - `$_COOKIE`: Stores cookies sent to the server.

## Advanced Variable Handling
- **Type Casting:**
  ```php
  $num = (int)$string;
  $float = (float)$num;
  ```

- **Variable Variables:**
  ```php
  $a = 'hello';
  $$a = 'world';
  echo $hello; // Outputs: world
  ```

## Common String Functions
- **`strlen()`**: Get the length of a string.
  ```php
  echo strlen('Hello'); // Outputs: 5
  ```

- **`str_replace()`**: Replace all occurrences of a search string with a replacement string.
  ```php
  echo str_replace('world', 'PHP', 'Hello world'); // Outputs: Hello PHP
  ```

- **`strpos()`**: Find the position of the first occurrence of a substring in a string.
  ```php
  echo strpos('Hello world', 'world'); // Outputs: 6
  ```

- **`trim()`**: Remove whitespace from the beginning and end of a string.
  ```php
  echo trim('  Hello PHP  '); // Outputs: Hello PHP
  ```

- **`explode()`**: Split a string by a delimiter into an array.
  ```php
  $arr = explode(',', 'one,two,three');
  print_r($arr); // Outputs: ['one', 'two', 'three']
  ```

- **`implode()`**: Join array elements into a string with a delimiter.
  ```php
  echo implode('-', ['one', 'two', 'three']); // Outputs: one-two-three
  ```

## Array Functions
- **`array_push()`**: Add elements to the end of an array.
  ```php
  $array = [1, 2];
  array_push($array, 3, 4);
  print_r($array); // Outputs: [1, 2, 3, 4]
  ```

- **`array_merge()`**: Merge one or more arrays.
  ```php
  $array1 = ["a", "b"];
  $array2 = ["c", "d"];
  $result = array_merge($array1, $array2);
  print_r($result); // Outputs: ["a", "b", "c", "d"]
  ```

- **`array_slice()`**: Extract a portion of an array.
  ```php
  $array = ["a", "b", "c", "d"];
  $slice = array_slice($array, 1, 2);
  print_r($slice); // Outputs: ["b", "c"]
  ```

- **`array_pop()`**: Remove the last element of an array.
  ```php
  $array = [1, 2, 3];
  array_pop($array);
  print_r($array); // Outputs: [1, 2]
  ```

- **`count()`**: Count the number of elements in an array.
  ```php
  echo count([1, 2, 3]); // Outputs: 3
  ```

## Conditional Statements
- **`if` statement:**
  ```php
  if ($condition) {
      // Code to execute if $condition is true
  }
  ```

- **`if...else` statement:**
  ```php
  if ($condition) {
      // Code if $condition is true
  } else {
      // Code if $condition is false
  }
  ```

- **`elseif` statement:**
  ```php
  if ($condition1) {
      // Code if $condition1 is true
  } elseif ($condition2) {
      // Code if $condition2 is true
  } else {
      // Code if neither condition is true
  }
  ```

- **`switch` statement:**
  ```php
  switch ($variable) {
      case "value1":
          // Code for value1
          break;
      case "value2":
          // Code for value2
          break;
      default:
          // Default code
  }
  ```

## Loops
- **`for` loop:**
  ```php
  for ($i = 0; $i < 10; $i++) {
      echo $i;
  }
  ```

- **`while` loop:**
  ```php
  while ($condition) {
      // Code to execute while $condition is true
  }
  ```

- **`do...while` loop:**
  ```php
  do {
      // Code to execute
  } while ($condition);
  ```

- **`foreach` loop:**
  ```php
  foreach ($array as $key => $value) {
      echo "$key => $value\n";
  }
  ```

## PHP Error Handling
- **`try...catch` Block:**
  ```php
  try {
      // Code that may throw an exception
  } catch (Exception $e) {
      echo 'Caught exception: ',  $e->getMessage(), "\n";
  }
  ```

- **Custom Error Handler:**
  ```php
  set_error_handler(function ($errno, $errstr, $errfile, $errline) {
      echo "Error [$errno]: $errstr in $errfile on line $errline\n";
  });
  ```

## File Handling
- **Opening a File:**
  ```php
  $file = fopen('example.txt', 'r');
  ```

- **Reading a File:**
  ```php
  while (($line = fgets($file)) !== false) {
      echo $line;
  }
  fclose($file);
  ```

- **Writing to a File:**
  ```php
  $file = fopen('example.txt', 'w');
  fwrite($file, 'Hello, PHP!');
  fclose($file);
  ```
