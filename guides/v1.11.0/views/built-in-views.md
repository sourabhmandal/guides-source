Ember comes pre-packaged with a set of views for building basic controls like text inputs, check boxes, and select lists. Usually, these views will be used via the [input helpers](../../templates/input-helpers/). However, the base views may be helpful in creating custom form behaviors.

* [Ember.Checkbox](https://api.emberjs.com/classes/Ember.Checkbox.html)
* [Ember.TextField](https://api.emberjs.com/classes/Ember.TextField.html)
* [Ember.TextArea](https://api.emberjs.com/classes/Ember.TextArea.html)

For example, here we have created a custom text field that toggles a dirty property:

```handlebars {data-filename=app/templates/some-template-using-a-view.hbs}
{{view "my-input" value=name inputDidChange=nameDidChange}}
```

```javascript {data-filename=app/views/my-input.js}
export default Ember.TextField.extend({
  inputDidChange: false,
  change: function() {
    this.set('inputDidChange', true);
  }
});
```

Ember itself provides one additional view not covered by the input helpers, and this is the select box view.

* [Ember.Select](https://api.emberjs.com/classes/Ember.Select.html)

This class can also be customized by extending it. To use the select view bundled with Ember, call it via the view helper:

```handlebars
{{view "select" content=people
                optionLabelPath="content.fullName"
                optionValuePath="content.id"
                prompt="Pick a person:"
                selection=selectedPerson}}
```

The select view is extremely feature-rich, and may perform badly when rendering many items. Due to this, it has not yet been converted into an component or helper like other inputs.
