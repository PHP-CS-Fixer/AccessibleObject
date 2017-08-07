# AccessibleObject

`AccessibleObject` is small class allowing you to easily access internals of any object.
In general, it's bad practice to do so.
While we strongly discourage you to using it, it may be helpful in debugging or testing old, sad, legacy projects.

# Example

```PHP
<?php
class Foo
{
    private $bar = 'baz';
}

$object = new Foo();
echo $object->bar; // PHP Fatal error:  Uncaught Error: Cannot access private property Foo::$bar

$accessibleObject = new AccessibleObject($object);
echo $accessibleObject->bar; // 'baz'
```
