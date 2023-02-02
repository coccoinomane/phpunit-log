Defines the `Loggable` trait to log from within your PHPUnit tests.

# Usage

1. Install the package with `composer require --dev coccoinomane/phpunit-log`.
1. Include the trait in your TestCase with `\use PHPUnitLog\Loggable;`.
1. Start logging with `this->log( $message )` or `this->print( $message )`.

# Features

- To log a message to screen, call `self::print( $message )`.
- To log a message to file, call `self::log( $message )`.
- The file will be named after the test class and placed in the subfolder _tests/logs_.
- Customize the log folder via the `logsPath` environment variable.
- To delete the log files before each run:
  ```php
  if (file_exists(self::getLogFilePath())) {
    unlink(self::getLogFilePath());
  }
  ```
- For further customizations, see the docs in [`Loggable`](./src/Loggable.php) or the tests in [`LoggableTest`](./tests/LoggableTest.php).

The `Loggable` trait is used by [`WordPressTestCase`](https://github.com/idearia/wp-tests).

# Custom folder for the logs

By default, the log files will be placed in the _tests/logs_ folder; set the `logsPath` environment variable to use a different folder.
You can use both relative and absolute paths.

To set `logsPath` in _phpunit.xml_:

```xml
<php>
    <env name="logsPath" value="./tests/logs"/>
</php>
```
