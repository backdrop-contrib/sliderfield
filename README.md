# Slider Field

Integrates jQuery UI Slider with Backdrop.
It provides one form element and one widget
All slider parameters are configurable either as parameters for form element or in widget settings form

## Features

- A widget that adds slider to numeric fields.
- Group sliding : by using it one can connect several sliders, the result is
  by changing one slider the others sliders linked to it will also change.
  There are several group types that indicate how the other sliders change.
  Look for "group".
- Form API element for using slider in custom forms.
- Slider color sets.
- Flexible Ajax support.
- Supports most of jquery slider parameters like orientation, disable/enable,
  animation, step, etc for both UI and Form Element.
- Setting default length for slider.
- Adjustable slider widget that allows changing slider range dynamically.
- Supports all numeric field types.
- Supports integer , float and decimal numbers as step.
- Can display bubble/hint near slider handles.
- Compatible with editablefields module.
- Fields using slider field can have empty value, proper UI is implemented to
  handle it.
- Full Webform integration.
- Compatibility with form api #states.
- Customizable through #attributes and proper css wrappers.

Note: It's not yet possible to create two handled sliders via Field UI.

## Installation

Enable the module at Administer >> Modules.

## FAQ

How to enable touch support for mobile devices?

It's out of the scope of this module but you may read this issue for how to do
it <https://www.drupal.org/node/2396457>.

## Implement

For Field Widget you can use "Slider Field" as widget for any numeric field type.

You may use Forms API element type slider or transfer_slider.

For demonstration you can can enable sliderfield_example module and visit examples/sliderfield.

Example:

```php
  $form['slider'] = array(
    '#type' => 'transfer_slider',
    '#title' => t('Slider test'),
    '#left_value' => 0,
    '#right_value' => 200,
    '#left' => t('Left input'),
    '#right' => t('Right input'),
    '#size' => 4,
  );

  $form['slider1'] = array(
    '#title' => NULL,
    '#title2' => NULL,
    '#input_title' => t('Min'),
    '#input2_title' => t('Max'),
    /**
    * Make the min value adjustable dynamically via another element
    * Type of the value is CSS selector
    * like .myfield, #element_id
    */
    '#adjust_field_min' => NULL,
    /**
    * Make the max value adjustable dynamically via another element
    * Type of the value is CSS selector
    * like .myfield, #element_id
    */
    '#adjust_field_max' => NULL,
    /**
     * Boolean: When set to true, the handle will animate with the default duration.
     * String: The name of a speed, such as "fast" or "slow".
     * Number: The duration of the animation, in milliseconds.
     */
    '#animate' => 'fast',
    /**
     * Disables the slider if set to true.
     */
    '#disabled' => FALSE,
    /**
     * The maximum value of the slider.
     */
    '#max' => 100,
    /**
     * The minimum value of the slider.
     */
    '#min' => 0,
    /**
     * Determines whether the slider handles move horizontally (min on left, max on right)
     * or vertically (min on bottom, max on top). Possible values: "horizontal", "vertical".
     */
    '#orientation' => 'horizontal',
    /**
     * Whether the slider represents a range.
     * Multiple types supported:
     *   Boolean: If set to true, the slider will detect if you have two handles and create a stylable range element between these two.
     *   String: Either "min" or "max". A min range goes from the slider min to one handle. A max range goes from one handle to the slider max.
     */
    '#range' => FALSE,
    /**
     * Determines the size or amount of each interval or step the slider takes between the min and max.
     * The full specified value range of the slider (max - min) should be evenly divisible by the step.
     */
    '#step' => 1,
    /**
     * Determines the value of the slider, if there's only one handle.
     * If there is more than one handle, determines the value of the first handle.
     * Or an array of values can be passed array('value'=>1 , 'value2'=> 2) ,
     * the order of values is important
     */
    //'#value' => 0,
    '#default_value' => NULL,
    /**
     * Some default color styles for ease of use
     * red, green, blue
     */
    '#slider_style' => NULL,
    /**
     * Default size for input values
     */
    '#size' => 3,
    /**
     * If set to FALSE will display inputs only when javascript is disabled
     */
    '#display_inputs' => TRUE,
    /**
     * If enabled display the current values of slider
     * as simple text
     */
    '#display_values' => FALSE,
    /**
     * Format of the displayed values
     * The usage is mostly for showing $,% or other signs near the value
     */
    '#display_values_format' => '%{value}%',
    /**
     * Display a hint/bubble near each slider handle showing the value of that handle
     */
  '#display_bubble' => FALSE,
  /**
  * Format of the displayed values in bubble/hint, The usage is mostly for showing $,% or other signs near the value. Use %{value}% as slider value
  * For range slider it can have two values separated by || like "$%{value}%MIN||$%{value}%MAX"
  */
  '#display_bubble_format' => '%{value}%',
    /**
     * Acceptable types are the same as css with and height and it will be used as width
     * or height depending on #orientation
     */
    '#slider_length' => NULL,
    /**
     * Display the element inside a fieldset
     */
    '#display_inside_fieldset' => FALSE,
    /**
     * Sliders with the same group will be linked
     * The behavior of linked sliders depends on group_type parameter
     * group name can only contain letters, numbers and underscore
     */
    '#group' => NULL,
    /**
     * same : All sliders in the same group will have the same value.
     * lock : All sliders in the same group will move with the exact same amount
     * total : The total value of all sliders will be between min/max , increasing value of
     *         one slider decreases the rest of the sliders in the same group
     */
    '#group_type' => 'same',
    /**
     * When set to TRUE, other sliders in the same
     * group will change only if this slider changes
     * values : TRUE , FALSE
     */
    '#group_master' => FALSE,
    /**
     * Disable buildin range validation
     * useful when element is used as widget
     * for fields, since integer fields have range validation
     * values : TRUE , FALSE
     */
    '#validate_range' => TRUE,
    /**
     * In case there are other fields that should be sync dynamically when
     * the slider changes
     * value : .my_field_css_class
     */
    '#fields_to_sync_css_selector' => NULL,
     /**
      * When field is not required, and display_inputs option is inactive
      * a checkbox will be shown allowing user to ignore the field
      * and enter no value
      * values : TRUE , FALSE
      */
     '#display_ignore_button' => FALSE,
     /**
      * When the slider does not have any value by enabling this option it won't show the
      * the slider handle unless user clicks on the slider to select a value
      * values : TRUE , FALSE
      */
     '#hide_slider_handle_when_no_value' => FALSE,
  );
```

## Issues

Bugs and Feature requests should be reported in the Issue Queue:
<https://github.com/backdrop-contrib/sliderfield/issues>

## Current Maintainers

- [Herb v/d Dool](https://github.com/herbdool)
- Seeking more maintainers.

## Credits

Ported to Backdrop by [Herb v/d Dool](https://github.com/herbdool). Originally
developed for Drupal by [Sina Salek](https://www.drupal.org/u/sinasalek),
[mrfelton](https://www.drupal.org/u/mrfelton), [jrowny](https://www.drupal.org/u/jrowny).

## License

This project is GPL v2 software. See the LICENSE.txt file in this directory for
complete text.
