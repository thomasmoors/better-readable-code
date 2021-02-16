Add a comment above every regular expression with a link to https://regex101.com/ which contains your expression and a list of testcases
Note: this still has the downside to be dependent of an external service, but I trust this service to be online.


```PHP

public function isDutchZipcode()
{
  // https://regex101.com/r/DBSmh6/1/
  preg_match_all($re, $str, $matches, PREG_SET_ORDER, 0);
  return !empty($matches);
}
```
