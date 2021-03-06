{{#template name="Raw"}}
The `raw()` method is responsible for getting a plain value from a document's field. This means that even if a given field is defined as a nested Astronomy class, it will return a plain JavaScript object instead.

**Getting a single value**

```js
User = Astro.Class({
  name: 'User',
  /* ... */
  fields: {
    'address': {
      type: 'object',
      nested: 'Address'
    }
  }
});

var user = Users.findOne();
// Getting a plain value of the "address" field.
user.raw('address'); // {city: 'San Francisco', state: 'CA'}
```

**Getting multiple fields**

You can also get raw values of multiple fields at once by providing an array of fields names.

```js
user.raw(['firstName', 'lastName', 'age']);
```

The code above will return an object of key-value pairs, where the key is a field name and the value is a plain field value.

**Getting all fields**

Sometime you may want to get raw values of the all fields in a document. You just have to use the `raw()` method without any argument.

```js
user.raw(); // Get all values.
```

**Getting nested fields**

The example below shows how you would access nested fields.

```js
var user = new User();
user.set('address', {
  city: 'San Francisco',
  state: 'CA'
});
user.raw('address.city'); // Returns "San Francisco".
```

As you can see, we've used the `.` notation to access a nested field. The `raw` method will return the `San Francisco` string.
{{/template}}
