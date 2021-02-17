Write comments that explain WHY you did something, not WHAT the code does. That is reserved for the function name.
Of course you can still use PHPDoc to add typehinting for older versions of PHP and to generate function descriptions that show up when hovering said function.

![code hint](https://github.com/thomasmoors/better-readable-code/blob/main/code%20hint.PNG)

But as you can see the comment about why this function exists in the first place is way more helpful.

Bad example:
```php

/**
 * Generate time intervals
 * @param $from
 * @param $to
 * @param $interval
 * @return array
 */
function times($from, $to, $interval)
{
    $availableTimes = [];

    $from = strtotime($from);
    $to = strtotime($to);

    while ($from <= $to) {
        $time = new DateTime();
        $time->setTime(date('H', $from), date('i', $from));
        $availableTimes[] = $time->format(TIME_FORMAT);
        $from = $time->modify("+ ${interval} minutes")->getTimestamp();
    }

    return $availableTimes;
}
```
Better example:

```php

/**
 * Generates an array of times with a set interval
 * @param $from string the start time
 * @param $to string the end time
 * @param $interval int the interval in minutes
 * @return array
 */
function generateTimeIntervals($from, $to, $interval)
{
/**
   The shop owner would like a dropdown menu with selectable times with an interval instead of a timepicker. 
   This is because a truck leaves every 30 minutes. The function is a little more generic and allows for other intervals to be passed when this requirement ever changes.
 */
    $availableTimes = [];

    $from = strtotime($from);
    $to = strtotime($to);

    while ($from <= $to) {
        $time = new DateTime();
        $time->setTime(date('H', $from), date('i', $from));
        $availableTimes[] = $time->format(TIME_FORMAT);
        $from = $time->modify("+ ${interval} minutes")->getTimestamp();
    }

    return $availableTimes;
}
```
