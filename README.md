# Bootstrap Toggle
Bootstrap-4 Toggle is a highly flexible **Bootstrap 4.x** plugin that converts checkboxes into toggles.

This repository has been forked from [minhur/bootstrap-toggle](https://github.com/minhur/bootstrap-toggle) in order to provide compliance with **Accessibility Requirements WCAG 2.1** in responsed to the issue [minhur/bootstrap-toggle#125](https://github.com/minhur/bootstrap-toggle/issues/125)

### Installation

```html
<link href="https://cdn.jsdelivr.net/gh/CSOIreland/bootstrap-toggle@2.2.2.1/css/bootstrap-toggle.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/gh/CSOIreland/bootstrap-toggle@2.2.2.1/js/bootstrap-toggle.min.js"></script>
```

## Usage

### Basic example
Simply add `data-toggle="toggle"` to convert checkboxes into toggles.

```html
<input type="checkbox" checked data-toggle="toggle">
```

### Stacked checkboxes
Refer to Bootstrap Form Controls documentation to create stacked checkboxes. Simply add `data-toggle="toggle"` to convert checkboxes into toggles.

```html
<div class="checkbox">
  <label>
    <input type="checkbox" data-toggle="toggle">
    Option one is enabled
  </label>
</div>
<div class="checkbox disabled">
  <label>
    <input type="checkbox" disabled data-toggle="toggle">
    Option two is disabled
  </label>
</div>
```

### Inline Checkboxes
Refer to Bootstrap Form Controls documentation to create inline checkboxes. Simply add `data-toggle="toggle"` to a convert checkboxes into toggles.

```html
<label class="checkbox-inline">
  <input type="checkbox" checked data-toggle="toggle"> First
</label>
<label class="checkbox-inline">
  <input type="checkbox" data-toggle="toggle"> Second
</label>
<label class="checkbox-inline">
  <input type="checkbox" data-toggle="toggle"> Third
</label>
```

## API

### Initialize by JavaScript
Initialize toggles with id `toggle-one` with a single line of JavaScript.

```html
<input id="toggle-one" checked type="checkbox">
<script>
  $(function() {
    $('#toggle-one').bootstrapToggle();
  })
</script>
```

### Options
Options can be passed via data attributes or JavaScript. For data attributes, append the option name to `data-`, as in `data-on="Enabled"`.

```html
<input type="checkbox" data-toggle="toggle" data-on="Enabled" data-off="Disabled">
<input type="checkbox" id="toggle-two">
<script>
  $(function() {
    $('#toggle-two').bootstrapToggle({
      on: 'Enabled',
      off: 'Disabled'
    });
  })
</script>
```

Name|Type|Default|Description|
---|---|---|---
on|string/html|"On"|Text of the on toggle
off|string/html|"Off"|Text of the off toggle
size|string|"normal"|Size of the toggle. Possible values are `large`, `normal`, `small`, `mini`.
onstyle|string|"primary"|Style of the on toggle. Possible values are `default`, `primary`, `success`, `info`, `warning`, `danger`
offstyle|string|"default"|Style of the off toggle. Possible values are `default`, `primary`, `success`, `info`, `warning`, `danger`
style|string| |Appends the value to the class attribute of the toggle. This can be used to apply custom styles. Refer to Custom Styles for reference.
width|integer|*null*|Sets the width of the toggle. if set to *null*, width will be calculated.
height|integer|*null*|Sets the height of the toggle. if set to *null*, height will be calculated.

### Methods
Methods can be used to control toggles directly.

```html
<input id="toggle-demo" type="checkbox" data-toggle="toggle">
```

Method|Example|Description
---|---|---
initialize|$('#toggle-demo').bootstrapToggle()|Initializes the toggle plugin with options
destroy|$('#toggle-demo').bootstrapToggle('destroy')|Destroys the toggle
on|$('#toggle-demo').bootstrapToggle('on')|Sets the toggle to 'On' state
off|$('#toggle-demo').bootstrapToggle('off')|Sets the toggle to 'Off' state
toggle|$('#toggle-demo').bootstrapToggle('toggle')|Toggles the state of the toggle
enable|$('#toggle-demo').bootstrapToggle('enable')|Enables the toggle
disable|$('#toggle-demo').bootstrapToggle('disable')|Disables the toggle

## Events

### Event Propagation
Note All events are propagated to and from input element to the toggle.

You should listen to events from the `<input type="checkbox">` directly rather than look for custom events.

```html
<input id="toggle-event" type="checkbox" data-toggle="toggle">
<div id="console-event"></div>
<script>
  $(function() {
    $('#toggle-event').change(function() {
      $('#console-event').html('Toggle: ' + $(this).prop('checked'))
    })
  })
</script>
```

### API vs Input
This also means that using the API or Input to trigger events will work both ways.

```html
<input id="toggle-trigger" type="checkbox" data-toggle="toggle">
<button class="btn btn-success" onclick="toggleOn()">On by API</button>
<button class="btn btn-danger" onclick="toggleOff()">Off by API</button>
<button class="btn btn-success" onclick="toggleOnByInput()">On by Input</button>
<button class="btn btn-danger" onclick="toggleOffByInput()">Off by Input</button>
<script>
  function toggleOn() {
    $('#toggle-trigger').bootstrapToggle('on')
  }
  function toggleOff() {
    $('#toggle-trigger').bootstrapToggle('off')  
  }
  function toggleOnByInput() {
    $('#toggle-trigger').prop('checked', true).change()
  }
  function toggleOffByInput() {
    $('#toggle-trigger').prop('checked', false).change()
  }
</script>
```
