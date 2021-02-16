Write comments that explain WHY you did something, not WHAT the code does. That is reserved for the function name.

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
   The shop owner would like a dropdown menu with selectable times with an interval instead of a timepicker. 
   This is because a truck leaves every 30 minutes. The function is a little more generic and allows for other intervals to be passed when this requirement ever changes.
 */
function generateTimeIntervals($from, $to, $interval)
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
