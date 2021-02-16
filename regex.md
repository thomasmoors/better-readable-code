Add a comment above every regular expression with a link to https://regex101.com/ which contains your expression and a list of testcases

The reasoning behind this is that regex is harder to read and deserves some explaination as to what you as an author try to achieve.
Note: this still has the downside to be dependent of an external service, but I trust this service to be online. You can of course also create some unit tests for them.


```PHP

public function isDutchZipcode()
{
  // https://regex101.com/r/DBSmh6/1/
  preg_match_all($re, $str, $matches, PREG_SET_ORDER, 0);
  return !empty($matches);
}
```
