Don't create deeply nested logic, try to return early if some pre-conditions are not met.

Bad example:
```php
function avoidBlackCat($cat)
{
    if ($cat !== null) {
        if ($cat->color === 'black') {
            goTheOtherWay();
        }
    }
}
```

Better example:
```php
function avoidBlackCat($cat)
{
    if ($cat === null || $cat->color === 'black') {
       return;
    }
    goTheOtherWay();
}
```
