# phpstorm-templates
## PHP Getter Method
```
#if ( ($RETURN_TYPE && $TYPE_HINT == $RETURN_TYPE) )#else/** @return ${TYPE_HINT} */#end
public ${STATIC} function get${NAME}()#if(${RETURN_TYPE}): ${RETURN_TYPE}#else#end
{
#if (${STATIC} == "static")
    return self::$${FIELD_NAME};
#else
    return $this->${FIELD_NAME};
#end
}
```
This generates the following getters:
```php
class Foo
{
    private string $first;
    private array $second;
    /** @var array<string> */
    private array $third;
    /** @var array<string> */
    private $fourth;
    private Bar $sixth;

    public function getFirst(): string
    {
        return $this->first;
    }

    public function getSecond(): array
    {
        return $this->second;
    }

    public function getThird(): array
    {
        return $this->third;
    }

    /** @return string[] */
    public function getFourth(): array
    {
        return $this->fourth;
    }

    public function getSixth(): Bar
    {
        return $this->sixth;
    }
}
```

## PHP Fluent Setter Method
```
#if ( ($SCALAR_TYPE_HINT == $TYPE_HINT) )#else/** @param ${TYPE_HINT} $${PARAM_NAME} */#end
public function set${NAME}(#if (${SCALAR_TYPE_HINT})${SCALAR_TYPE_HINT} #else#end$${PARAM_NAME})#if(${RETURN_TYPE}): static#else#end
{
    $this->${FIELD_NAME} = $${PARAM_NAME};
    return $this;
}
```

This generates the following setters:
```php
class Foo
{
    private ?string $first;
    private array $second;
    /** @var array<string> */
    private array $third;
    /** @var array<string> */
    private $fourth;
    private Bar $sixth;

    /** @param string|null $first */
    public function setFirst(?string $first): static
    {
        $this->first = $first;
        return $this;
    }

    public function setSecond(array $second): static
    {
        $this->second = $second;
        return $this;
    }

    public function setThird(array $third): static
    {
        $this->third = $third;
        return $this;
    }

    /** @param string[] $fourth */
    public function setFourth(array $fourth): static
    {
        $this->fourth = $fourth;
        return $this;
    }

    public function setSixth(Bar $sixth): static
    {
        $this->sixth = $sixth;
        return $this;
    }
}
```

## PHP Setter Method
```
#if (${SCALAR_TYPE_HINT})#else/** @param ${TYPE_HINT} $${PARAM_NAME} */#end
public ${STATIC} function set${NAME}(#if (${SCALAR_TYPE_HINT})${SCALAR_TYPE_HINT} #end$${PARAM_NAME})#if (${VOID_RETURN_TYPE}):void #end
{
#if (${STATIC} == "static")
    self::$${FIELD_NAME} = $${PARAM_NAME};
#else
    $this->${FIELD_NAME} = $${PARAM_NAME};
#end
}
```

This generates the following setters:
```php
class Foo
{
    private ?string $first;
    private array $second;
    /** @var array<string> */
    private array $third;
    /** @var array<string> */
    private $fourth;
    private Order $sixth;

    /** @param string|null $first */
    public function setFirst(?string $first): void
    {
        $this->first = $first;
    }

    public function setSecond(array $second): void
    {
        $this->second = $second;
    }

    public function setThird(array $third): void
    {
        $this->third = $third;
    }

    /** @param string[] $fourth */
    public function setFourth(array $fourth): void
    {
        $this->fourth = $fourth;
    }

    public function setSixth(Order $sixth): void
    {
        $this->sixth = $sixth;
    }
}
```
