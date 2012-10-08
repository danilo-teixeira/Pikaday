Pickaday
========

### A refreshing JavaScript Datepicker

[**Try Pickaday Demos**](http://dbushell.github.com/Pickaday/)

## Usage

**Pickaday** can be bound to an input field:

```html
<input type="text" id="datepicker" value="2012-10-08">
```

Add the JavaScript to the end of your document:

```html
<script src="pickaday.js"></script>
<script>
    var picker = new Pickaday({ field: document.getElementById('datepicker') });
</script>
```

If you're using **jQuery** make sure to pass only the first element:

```javascript
var picker = new Pickaday({ field: $('#datepicker')[0] });
```

If the Pickaday instance is not bound to a field you can append the element anywhere:

```javascript
var field = document.getElementById('datepicker');
var picker = new Pickaday({
    onSelect: function(date) {
        field.value = picker.toString()
    }
});
field.parentNode.insertBefore(picker.el, field.nextSibling);
```
### Configuration

As the examples demonstrate above
Pickaday has many useful options:

* `field` bind the datepicker to a form field
* `bound` automatically show/hide the datepicker on `field` focus (default `true` if `field` is set)
* `format` the default output format for `.toString()` and `field` value
* `defaultDate` the initial date to view when first opened
* `setDefaultDate` make the `defaultDate` the initial selected value
* `firstDay` first day of the week (`0`: Sunday, `1`: Monday, etc)
* `minDate` the minimum/earliest date that can be selected
* `maxDate` the maximum/latest date that can be selected
* `yearRange` number of years either side (e.g. `10`) or array of upper/lower range (e.g. `[1900,2012]`)
* `isRTL` reverse the calendar for right-to-left languages
* `i18n` language defaults for month and weekday names (see internationalization below)
* `onSelect` callback function for when a date is selected
* `onOpen` callback function for when the picker becomes visible 
* `onClose` callback function for when the picker is hidden


### Methods

You can control the date picker after creation:

```javascript
<script>
    var picker = new Pickaday({ field: document.getElementById('datepicker') });
</script>
```

`picker.toString('YYYY-MM-DD')`

Returns the selected date in a string format. If [Moment.js](http://momentjs.com/) exists (recommended) then Pickaday can return any format Moment understands.

`picker.getMoment()`

Returns a [Moment.js](http://momentjs.com/) object for the selected date (Moment must be loaded before Pickaday).

`picker.getDate(new Date()`

Returns a basic JavaScript `Date` object of the selected day, or `null` if no selection.

`picker.setDate('2012-01-01'))`

Set the current selection. This will be restricted within the bounds of `minDate` and `maxDate` options if they're specified.

`picker.gotoDate(new Date(2012, 1))`

Change the current view to see a specific date. This example will jump to February 2012 ([month is a zero-based index](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Date)).

`picker.gotoToday()`

Shortcut for `picker.gotoDate(new Date())`

`picker.gotoMonth(2)`

Change the current view by month (0: January, 1: Feburary, etc).

`picker.nextMonth()`
`picker.prevMonth()`

Go to the next or previous month (this will change year if necessary).

`picker.gotoYear()`

Change the year being viewed.

`picker.isVisible()`

Returns `true` or `false`.

`picker.show()`

Make the picker visible.

`picker.hide()`

Hide the picker making it invisible.

`picker.destroy()`

Hide the picker and remove all event listeners — no going back!

### Internationalization

The default `i18n` configuration format looks like this:

```javascript
i18n: {
    months        : ['January','February','March','April','May','June','July','August','September','October','November','December'],
    weekdays      : ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'],
    weekdaysShort : ['Sun','Mon','Tue','Wed','Thu','Fri','Sat']
}
```

You must provide 12 months and 7 weekdays (with abbreviations). Always specify weekdays in this order with Sunday first. You can change the `firstDay` option to reorder if necessary (0: Sunday, 1: Monday, etc). You can also set `isRTL` to `true` for languages that are read right-to-left.

## Change Log

### 8th October 2012

* Basic documentation written
* GitHub repository is ready to go…

* * *

Author: David Bushell [http://dbushell.com](http://dbushell.com/) [@dbushell](http://twitter.com/dbushell/)

Copyright © 2012 David Bushell | BSD & MIT license