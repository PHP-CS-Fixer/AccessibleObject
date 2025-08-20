# 💀 Deprecation notice

Accessing internals using this package makes it difficult for your IDE/SCA tools to track types properly.
If you need to access internals, consider the following alternative:
```php
$bar = \Closure::bind(static fn ($object): string => $object->bar, null, Foo::class)($object);
```

# AccessibleObject

`AccessibleObject` is small class allowing you to easily access internals of any object.
In general, it's bad practice to do so.
While we strongly discourage you to using it, it may be helpful in debugging or testing old, sad, legacy projects.

# Example

```PHP
<?php
class Foo
{
    private string $bar = 'baz';
}

$object = new Foo();
$bar = $object->bar; // PHP Fatal error:  Uncaught Error: Cannot access private property Foo::$bar

$accessibleObject = new AccessibleObject($object);
$bar = $accessibleObject->bar; // 'baz'
```
