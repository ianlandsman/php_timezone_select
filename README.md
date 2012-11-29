PHP Timezone Select
===================

An HTML select list and JSON file of PHP timezones. I've cleaned up a few things and added a few niceties as well.

Based on the timezone selection we did for [Snappy](http://www.besnappy.com).

MIT License

You're welcome!

## JSON Format
```json
{
   "AF":{
      "name":"Afghanistan",
      "timezones":{
         "Asia\/Kabul":{
            "abbr":"AFT",
            "offset":16200,
            "name":"Kabul"
         }
      }
   },
}
```

## Example Usage
You can use the HTML version as is (perhaps some javascript to set the default if needed) but if you need to do something custom you can use the json to have full control.

```php
/*
//This example uses Laravel Blade syntax
//In the controlloer do something like:

$timezones = json_decode(file_get_contents(path('storage').'data/timezones.json'));
return View::make('home.index')->with('timezones', $timezones);
*/

<select name="timezone" id="timezone">
	@foreach($timezones AS $countr_abbr=>$country)
		<optgroup label="{{ $country->name }}">
			@foreach($country->timezones AS $php_abbr=>$info)
				<option value="{{ $php_abbr }}">{{ $info->name }} &nbsp; ({{ $info->abbr }})</option>
			@endforeach
		 </optgroup>
	 @endforeach
</select>
```
