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
