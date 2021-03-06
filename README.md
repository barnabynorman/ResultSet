# ResultSet
ResultSet is a project based around array type data sets. I wrote the majority of the library as an Eloquent like class to query data held in JSON files. Later I used it with the output from SQL queries, creating object instances for each database row and storing them in the ResultSet held in memory, giving me an abstraction between data and logic and a fast way to get to the data without having to write queries every time. Because I held my instances of ResultSet in memory I would read from the database once and query the ResultSet multiple times, which made it fast! An older project that I had written that had multiple database queries, (and admittedly poor structure), when rewired using ResultSet went from seconds down to milliseconds - and that was on every page load!

Obviously a ResultSet is not for everybody - there are probably much better ways of working like structuring data better to start with, so that queries are required less, caching and I have not tested it with large datasets so it could run like a dog! But I like that I can take a set of data, create a ResultSet with it and have quite a powerful toolset to get at the data at my fingertips.

The ResultSet is a php ArrayObject at heart, with a bunch of methods to filter / query and manipulate the data held inside, either as objects or arrays (or both). There are no rockets involved, just plain old simple php that anyone could write, (mainly foreach loops), take a look. Its very simple to use, just create a new object or get an instance using a static method and pass in your data and start using.

## Getting started
### With Composer
```bash
$ composer require barnabynorman/result-set
```

```json
{
    "require": {
        "barnabynorman/result-set": "^1.00"
    }
}
```

```php
<?php
require 'vendor/autoload.php';

use ResultSet\ResultSet;

$rs = new ResultSet(['one', 'two', 'three']);
print_r($rs->first());
```

### Without Composer
But it's so simple with [composer!](https://getcomposer.org/) Download the ResultSet latest release and put the contents of the ZIP archive into a directory in your project. Then require the file ResultSet.php.

```php
<?php
require 'path/to/ResultSet.php';

use ResultSet\ResultSet;

$rs = new ResultSet(['one', 'two', 'three']);
print_r($rs->first());
```
