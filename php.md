---
title: PHP
date: 2021-01-04 15:23:28
icon: icon-php
background: bg-purple-900
tags:
categories:
  - Programming
intro: |
    This [PHP](https://www.php.net/manual/en/) cheat sheet provides a reference for quickly looking up the correct syntax for the code you use most frequently. 
---


Getting started {.cols-3}
---------------


### hello.php
```php
<?php // begin with a PHP open tag.

echo "Hello World\n";
print("Hello quickref.me");

?>
```
PHP run command
```shell script
$ php hello.php
```



### Variables
```php
$boolean1 = true;
$boolean2 = True;

$int = 12;
$float = 3.1415926;
unset($float);  // Delete variable

$str1 = "How are you?";
$str2 = 'Fine, thanks';
```
See: [Types](#types)




### Strings
```php
$url = "quickref.me";
echo "I'm learning PHP at $url";

// Concatenate strings
echo "I'm learning PHP at " . $url;

$hello = "Hello, ";
$hello .= "World!";
echo $hello;   # => Hello, World!
```
See: [Strings](#strings-2)




### Arrays
```php
$num = [1, 3, 5, 7, 9];
$num[5] = 11;
unset($num[2]);    // Delete variable
print_r($num);     # => 1 3 7 9 11
echo count($num);  # => 5
```
See: [Arrays](#arrays-2)



### Operators
```php
$x = 1;
$y = 2;

$sum = $x + $y;
echo $sum;   # => 3
```
See: [Operators](#operators-2)


### Include {.row-span-3}
#### vars.php
```php
<?php // begin with a PHP open tag.
$fruit = 'apple';
echo "I was imported";
return 'Anything you like.';
?>
```
#### test.php
```php
<?php
include 'vars.php';
echo $fruit . "\n";   # => apple

/* Same as include,
cause an error if cannot be included*/
require 'vars.php';

// Import only once
include_once 'vars.php';

// Include through HTTP
include 'http://x.com/file.php';

// Include and the return statement
$result = include 'vars.php';
echo $result;  # => Anything you like.
?>
```



### Functions
```php
function add($num1, $num2 = 1) {
    return $num1 + $num2;
}
echo add(10);    # => 11
echo add(10, 5); # => 15
```
See: [Functions](#functions-3)




### Comments 
```php
# This is a one line shell-style comment

// This is a one line c++ style comment

/* This is a multi line comment
   yet another line of comment */
```



### Constants
```php
define("MY_CONST", "hello");

echo MY_CONST;   # => hello

# => MY_CONST is: hello
echo 'MY_CONST is: ' . MY_CONST; 
```


### Classes
```php
class Student {
    public function __construct($name) {
        $this->name = $name;
    }
}
$alex = new Student("Alex");
```
See: [Classes](#classes-2)





Types {.cols-3}
---------------


### Boolean {.row-span-2}
```php
$boolean1 = true;
$boolean2 = TRUE;
$boolean3 = false;
$boolean4 = FALSE;

$boolean5 = (boolean) 1;   # => true
$boolean6 = (boolean) 0;   # => false
```
Boolean are case-insensitive




### Integer {.row-span-2}
```php
$int1 = 28;    # => 28
$int2 = -32;   # => -32
$int3 = 012;   # => 10 (octal)
$int4 = 0x0F;  # => 15 (hex)
$int5 = 0b101; # => 5  (binary)

# => 2000100000 (decimal, PHP 7.4.0)
$int6 = 2_000_100_000;
```
See also: [Integers](https://www.php.net/manual/en/language.types.integer.php)


### Strings
```php
echo 'this is a simple string';
```
See: [Strings](#strings-3)

### Arrays
```php
$arr = array("hello", "world", "!");
```
See: [Arrays](#arrays-3)


### Float (Double)
```php
$float1 = 1.234;
$float2 = 1.2e7;
$float3 = 7E-10;

$float4 = 1_234.567;  // as of PHP 7.4.0
var_dump($float4);    // float(1234.567)

$float5 = 1 + "10.5";   # => 11.5
$float6 = 1 + "-1.3e3"; # => -1299
```



### Null
```php
$a = null;
$b = 'Hello php!';
echo $a ?? 'a is unset'; # => a is unset
echo $b ?? 'b is unset'; # => Hello php

$a = array();
$a == null    # => true
$a === null   # => false
is_null($a)   # => false
```


### Iterables
```php
function bar(): iterable {
    return [1, 2, 3];
}
function gen(): iterable {
    yield 1;
    yield 2;
    yield 3;
}
foreach (bar() as $value) {
    echo $value;   # => 123
} 
```


Strings {.cols-3}
---------------



### String
```php
# => '$String'
$sgl_quotes = '$String';

# => 'This is a $String.'
$dbl_quotes = "This is a $sgl_quotes.";

# => a 	 tab character.
$escaped   = "a \t tab character.";

# => a slash and a t: \t
$unescaped = 'a slash and a t: \t';
```




### Multi-line
```php
$str = "foo";

// Uninterpolated multi-liners
$nowdoc = <<<'END'
Multi line string
$str
END;

// Will do string interpolation
$heredoc = <<<END
Multi line
$str
END;
```



### Manipulation
```php
$s = "Hello Phper";
echo strlen($s);       # => 11

echo substr($s, 0, 3); # => Hel
echo substr($s, 1);    # => ello Phper
echo substr($s, -4, 3);# => hpe

echo strtoupper($s);   # => HELLO PHPER
echo strtolower($s);   # => hello phper

echo strpos($s, "l");      # => 2
var_dump(strpos($s, "L")); # => false
```
See: [String Functions](https://www.php.net/manual/en/ref.strings.php)



Arrays {.cols-3}
---------------

### Defining {.row-span-2}
```php
$a1 = ["hello", "world", "!"]
$a2 = array("hello", "world", "!");
$a3 = explode(",", "apple,pear,peach");
```
#### Mixed int and string keys
```php
$array = array(
    "foo" => "bar",
    "bar" => "foo",
    100   => -100,
    -100  => 100,
);
var_dump($array);
```
#### Short array syntax
```php
$array = [
    "foo" => "bar",
    "bar" => "foo",
];
```



### Multi array
```php
$multiArray = [ 
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
];

print_r($multiArray[0][0]) # => 1
print_r($multiArray[0][1]) # => 2
print_r($multiArray[0][2]) # => 3
```


### Multi type {.row-span-2}
```php
$array = array(
    "foo" => "bar",
    42    => 24,
    "multi" => array(
         "dim" => array(
             "a" => "foo"
         )
    )
);

# => string(3) "bar"
var_dump($array["foo"]);

# => int(24)
var_dump($array[42]);    

# =>  string(3) "foo"
var_dump($array["multi"]["dim"]["a"]);
```



### manipulation
```php
$arr = array(5 => 1, 12 => 2);
$arr[] = 56;      // Append
$arr["x"] = 42;   // Add with key
sort($arr);       // Sort
unset($arr[5]);   // Remove
unset($arr);      // Remove all
```
See: [Array Functions](https://www.php.net/manual/en/ref.array.php)

### Indexing iteration
```php
$array = array('a', 'b', 'c');
$count = count($array);

for ($i = 0; $i < $count; $i++) {
    echo "i:{$i}, v:{$array[$i]}\n";
}
```

### Value iteration
```php
$colors = array('red', 'blue', 'green');

foreach ($colors as $color) {
    echo "Do you like $color?\n";
}
```
### Key iteration
```php
$arr = ["foo" => "bar", "bar" => "foo"];

foreach ( $arr as $key => $value )
{
  	echo "key: " . $key . "\n";
    echo "val: {$arr[$key]}\n";
}
```

### Concatenate arrays
```php
$a = [1, 2];
$b = [3, 4];

// PHP 7.4 later
# => [1, 2, 3, 4]
$result = [...$a, ...$b];
```

### Into functions
```php
$array = [1, 2];

function foo(int $a, int $b) {
	echo $a; # => 1
  	echo $b; # => 2
}
foo(...$array);
```


### Rest parameters
```php
function foo($first, ...$other) {
	var_dump($first); # => a
  	var_dump($other); # => ['b', 'c']
}
foo('a', 'b', 'c' /*, ...*/ );
// or
function foo($first, string ...$other){}
```



Operators {.cols-4}
---------------



### Arithmetic
| -  | -              |
|----|----------------|
| `+`  | Addition       |
| `-`  | Subtraction    |
| `*`  | Multiplication |
| `/`  | Division       |
| `%`  | Modulo         |
| `**` | Exponentiation |

### Assignment
| -      | -                 |
|--------|-------------------|
| `a += b` | Same as `a = a + b` |
| `a -= b` | Same as `a = a – b` |
| `a *= b` | Same as `a = a * b` |
| `a /= b` | Same as `a = a / b` |
| `a %= b` | Same as `a = a % b` |


### Comparison {.row-span-2}
| -   | -                            |
|-----|------------------------------|
| `==`  | Equal                        |
| `===` | Identical                    |
| `!=`  | Not equal                    |
| `<>`  | Not equal                    |
| `!==` | Not identical                |
| `<`   | Less than                    |
| `>`   | Greater than                 |
| `<=`  | Less than or equal           |
| `>=`  | Greater than or equal        |
| `<=>` | Less than/equal/greater than |

### Logical
| -    | -            |
|------|--------------|
| `and`  | And          |
| `or`   | Or           |
| `xor`  | Exclusive or |
| `!`    | Not          |
| `&&`   | And          |
| `||` | Or           |




### Arithmetic {.col-span-2}
```php
// Arithmetic
$sum        = 1 + 1; // 2
$difference = 2 - 1; // 1
$product    = 2 * 2; // 4
$quotient   = 2 / 1; // 2

// Shorthand arithmetic
$num = 0;
$num += 1;       // Increment $num by 1
echo $num++;     // Prints 1 (increments after evaluation)
echo ++$num;     // Prints 3 (increments before evaluation)
$num /= $float;  // Divide and assign the quotient to $num
```



### Bitwise
| -  | -                  |
|----|--------------------|
| `&`  | And                |
| `|`  | Or (inclusive or)  |
| `^`  | Xor (exclusive or) |
| `~`  | Not                |
| `<<` | Shift left         |
| `>>` | Shift right        |




Conditionals {.cols-3}
---------------

### If elseif else
```php
$a = 10;
$b = 20;

if ($a > $b) {
    echo "a is bigger than b";
} elseif ($a == $b) {
    echo "a is equal to b";
} else {
    echo "a is smaller than b";
}
```


### Switch
```php
$x = 0;
switch ($x) {
    case '0':
        print "it's zero";
        break; 
    case 'two':
    case 'three':
        // do something
        break;
    default:
        // do something
}
```

### Ternary operator
```php
# => Does
print (false ? 'Not' : 'Does');

$x = false;
# => Does
print($x ?: 'Does');

$a = null;
$b = 'Does print';
# => a is unsert
echo $a ?? 'a is unset';
# => print
echo $b ?? 'b is unset';
```



Loops {.cols-3}
---------------


### while
```php
$i = 1;
# => 12345
while ($i <= 5) {
    echo $i++;
}
```

### do while
```php
$i = 1;
# => 12345
do {
    echo $i++;
} while ($i <= 5);
```


### for i
```php
# => 12345
for ($i = 1; $i <= 5; $i++) {
    echo $i;
}
```

### break
```php
# => 123
for ($i = 1; $i <= 5; $i++) {
    if ($i === 4) {
        break;
    }
    echo $i;
}
```

### continue
```php
# => 1235
for ($i = 1; $i <= 5; $i++) {
    if ($i === 4) {
        continue;
    }
    echo $i;
}
```

### foreach
```php
$a = ['foo' => 1, 'bar' => 2];
# => 12
foreach ($a as $k) {
    echo $k;
}
```
See: [Array iteration](#value-iteration)



Functions {.cols-3}
---------------


### Returning values
```php
function square($x)
{
    return $x * $x;
}
echo square(4);  # => 16
```




### Variable functions
```php
function bar($arg = '')
{
    echo "In bar(); arg: '$arg'.\n";
}

$func = 'bar';
$func('test'); # => In bar(); arg: test
```





### Anonymous functions
```php
$greet = function($name)
{
    printf("Hello %s\r\n", $name);
};

$greet('World');
$greet('PHP');
```




### Default parameters
```php
function coffee($type = "cappuccino")
{
    return "Making a cup of $type.\n";
}
# => Making a cup of cappuccino.
echo coffee();
# => Making a cup of .
echo coffee(null);
# => Making a cup of espresso.
echo coffee("espresso");
```



### Arrow Functions
```php
$y = 1;
 
$fn1 = fn($x) => $x + $y;

// equivalent to using $y by value:
$fn2 = function ($x) use ($y) {
    return $x + $y;
};
echo $fn1(5);   # => 6
echo $fn2(5);   # => 6
```




### Recursive functions
```php
function recursion($x)
{
    if ($x < 5) {
        echo "$x";
        recursion($x + 1);
    }
}

echo recursion(1);  # => 1234
```


Classes {.cols-3}
---------------


### Constructor
```php
class Student {
    public function __construct($name) {
        $this->name = $name;
    }
  	public function print() {
        echo "Name: " . $this->name;
    }
}
$alex = new Student("Alex");
$alex->print();    # => Name: Alex
```

### Inheritance
```php
class ExtendClass extends SimpleClass
{
    // Redefine the parent method
    function displayVar()
    {
        echo "Extending class\n";
        parent::displayVar();
    }
}

$extended = new ExtendClass();
$extended->displayVar();
```

### Classes variables {.row-span-2}
```php
class MyClass
{
    const MY_CONST       = 'value';
    static $staticVar    = 'static';

    // Visibility
    public static $var1  = 'pubs';

    // Class only
    private static $var2 = 'pris';

    // The class and subclasses
    protected static $var3 = 'pros';

    // The class and subclasses
    protected $var6      = 'pro';

    // The class only
    private $var7        = 'pri';  
}
```
Access statically
```php
echo MyClass::MY_CONST;   # => value
echo MyClass::$staticVar; # => static
```



### Magic Methods
```php
class MyClass
{
    // Object is treated as a String
    public function __toString()
    {
        return $property;
    }
    // opposite to __construct()
    public function __destruct()
    {
        print "Destroying";
    }
}
```


### Interface
```php
interface Foo 
{
    public function doSomething();
}
interface Bar
{
    public function doSomethingElse();
}
class Cls implements Foo, Bar 
{
    public function doSomething() {}
    public function doSomethingElse() {}
}
```

Miscellaneous {.cols-3}
-------------

### Basic error handling
```php
try {
    // Do something
} catch (Exception $e) {
    // Handle exception
} finally {
    echo "Always print!";
}
```

### Exception in PHP 8.0 {.col-span-2}
```php {.wrap}
$nullableValue = null;

try {
	$value = $nullableValue ?? throw new InvalidArgumentException();
} catch (InvalidArgumentException) { // Variable is optional
    // Handle my exception
    echo "print me!";
}
```

### Custom exception {.row-span-2}
```php
class MyException extends Exception {
    // do something
}
```
Usage
```php
try {
    $condition = true;
    if ($condition) {
        throw new MyException('bala');
    }
} catch (MyException $e) {
    // Handle my exception
}
```

### Nullsafe Operator {.row-span-2}
```php
// As of PHP 8.0.0, this line:
$result = $repo?->getUser(5)?->name;

// Equivalent to the following code:
if (is_null($repo)) {
    $result = null;
} else {
    $user = $repository->getUser(5);
    if (is_null($user)) {
        $result = null;
    } else {
        $result = $user->name;
    }
}
```
See also: [Nullsafe Operator](https://wiki.php.net/rfc/nullsafe_operator)

### Regular expressions
```php
$str = "Visit Quickref.me";
echo preg_match(/me/i, $str); # => 1
```
See: [Regex in PHP](/regex#regex-in-php)

### fopen() mode

| -    | -                        |
|------|--------------------------|
| `r`  | Read                     |
| `r+` | Read and write, prepend  |
| `w`  | Write, truncate          |
| `w+` | Read and write, truncate |
| `a`  | Write, append            |
| `a+` | Read and write, append   |



Also see 
-------

- [PHP Docs](https:#www.php.net/manual/en/index.php)
- [Learn X in Y minutes](https://learnxinyminutes.com/docs/php/)



