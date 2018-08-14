---
layout: page
---

Specific use case of the following snippet -

> Need to recursively copy all image files in a directory to a new directory
without maintaining directory structure

Meaning, for example, we need to copy all files from a directory `img` to
`uploads/2018/08`. Even if the file exists at `img/2016/03/cat.jpg`, we want it
at `uploads/2018/08/cat.jpg`.

```php
<?php

$old_dir = 'img';
$new_dir = 'uploads/2018/08/';

if (!file_exists($old_dir)) {
  echo "Source directory doesn't exist." . PHP_EOL;
}

if (!file_exists($new_dir)) {
  echo "Destination directory doesn't exist. Creating destination directory." . PHP_EOL;
  mkdir($new_dir, 0755, true);
}

// http://php.net/manual/en/class.recursivedirectoryiterator.php#97228
$Directory = new RecursiveDirectoryIterator($old_dir);
$Iterator = new RecursiveIteratorIterator($Directory);
$Regex = new RegexIterator($Iterator, '/^.+\.(jpg|png|jpeg)$/i', RecursiveRegexIterator::GET_MATCH);

echo "Copying from " . $old_dir . " to " . $new_dir . PHP_EOL;

foreach ($Regex as $filename) {
  if (!file_exists($new_dir . basename($filename[0]))) {
    echo "Copying " . basename($filename[0]) . PHP_EOL;
    copy($filename[0], $new_dir . basename($filename[0]));
  } else {
    echo "Skipping " . basename($filename[0]) . " as it already exists at destination"  . PHP_EOL;
  }
}
```
