Don't define multiple conditions inline

e.g. 
```php
if ($this->age > 90 || $this->goodEyes !== 2 || in_array($this->medication, ['morphine', 'blablapam']) || ($this->licenseExpired && !$appointment->date->gracePeriod)
{
  throw UnableToDriveException();
}
```

Instead write small function


```php
if ($this->unableToDrive())
{
  throw UnableToDriveException();
}

private function unableToDrive()
{
  return $this->tooOld() || $this->badEyes() || $this->onHeavyMedication() || !$this->havingADriversLicense();
}

private function tooOld()
{
  return $this->age > self::MAX_DRIVING_AGE;
}

private function badEyes()
{
  return $this->goodEyes !== self::NORMAL_AMOUNT_OF_HUMAN_EYES;
}

private function onHeavyMedication()
{
  return in_array($this->medication, ['morphine', 'blablapam']);
}

private function havingADriversLicense()
{
  return $this->licenseExpired && !$appointment->date->gracePeriod;
}


```
