## Some sample queries

<details>
  <summary>
    Input JSON
  </summary>
<pre class="highlight highlight-source-json">
{
  "Address": {
    "City": "Winchester",
    "Postcode": "SO21 2JN",
    "Street": "Hursley Park"
  },
  "Age": 28,
  "Email": [
    {
      "address": [
        "fred.smith@my-work.com",
        "fsmith@my-work.com"
      ],
      "type": "office"
    },
    {
      "address": [
        "freddy@my-social.com",
        "frederic.smith@very-serious.com"
      ],
      "type": "home"
    }
  ],
  "FirstName": "Fred",
  "Other": {
    "Alternative.Address": {
      "City": "London",
      "Postcode": "E1 6RF",
      "Street": "Brick Lane"
    },
    "Misc": null,
    "Over 18 ?": true
  },
  "Phone": {
    "Cell": {
      "number": "01962 001235",
      "type": "office"
    },
    "Fax": {
      "number": "077 7700 1234",
      "type": "mobile"
    },
    "Main": {
      "number": "0203 544 1234",
      "type": "home"
    },
    "Mobile": {
      "number": "01962 001234",
      "type": "office"
    }
  },
  "Surname": "Smith"
}
</pre>
</details>

<details>
  <summary>
    JSONATA Query <br />
    Here we are trying to get the key of an object to be included as part of the output. 
    If the parent object was an array the maker of the json would have embedded the key in the object like: [ { "number":"ttt.ttt", "type":"mobile", "label":"Fax"} ..]
    To get the keys, we use $keys(%). % points to the parent. To get the index in the context, we first pin the context location index in a variable ($p) 
    with the use of # (like in Phone.%#$p) and use it to index the keys output.
  </summary>
<pre class="highlight highlight-source-json">
$.Phone.*#$p.{"number":number,"type":$keys(%)[$p]}
</pre>
</details>
<details>
  <summary>
    Output
  </summary>
<pre class="highlight highlight-source-json">
[
  {
    "number": "01962 001235",
    "type": "Cell"
  },
  {
    "number": "077 7700 1234",
    "type": "Fax"
  },
  {
    "number": "0203 544 1234",
    "type": "Main"
  },
  {
    "number": "01962 001234",
    "type": "Mobile"
  }
]
</pre>
</details>

try this [here](https://try.jsonata.org/58zlkqVM6)

[Stackoverflow JSONATA questions](https://stackoverflow.com/questions/tagged/jsonata)

