---
title: JSON Basics
description: Basics of JSON
date: 2025-01-28 15:14:00 -0300
# image:
#   path: "/assets/img/posts/wall.png"
#   alt: "Breaking Through The Wall"
category:
 - json
 - devops
 - data_serialization
 - fundamentals
tags:
  - json
  - devops
  - data_serialization
  - fundamentals
---

## What is JSON?

JSON (JavaScript Object Notation) is a human-readable data serialization format that is commonly used for configuration files and data exchange. It is based on the JavaScript programming language and is easy to read and write.

## JSON Document Structure

A JSON document consists of one or more JSON objects, which are enclosed in curly braces `{}`. Each object contains key-value pairs, where the key is a string enclosed in double quotes `""`, followed by a colon `:`, and the value can be a string, number, boolean, array, or another object. The key-value pairs are separated by commas.

## JSON Objects and Data Types

A JSON object is a collection of key-value pairs, where the key is a string and the value can be a string, number, boolean, array, or another object. JSON supports the following data types:

- **String**: A sequence of characters enclosed in double quotes `""`.
- **Number**: A numeric value, which can be an integer or a floating-point number.
- **Boolean**: A logical value that can be `true` or `false`.
- **Array**: An ordered list of values enclosed in square brackets `[]`.
- **Object**: A collection of key-value pairs enclosed in curly braces `{}`.
- **Null**: A special value that represents `null` or an empty value.
- **Nested Objects**: Objects can contain other objects as values.
- **Nested Arrays**: Arrays can contain other arrays or objects as values.
- **Mixed Data Types**: JSON allows mixing different data types within an object or array.

### JSON String, Number, Null and Boolean Example:

```json
{
  "name": "John Doe",  //string
  "age": 30,  //number
  "is_student": false  //boolean
  "null_value": null  //null
}
```

### JSON Array Example:

```json
{
  "fruits": ["apple", "banana", "orange"]  //array
}
```

### JSON Object Example:

```json
{
  "person": { //object
    "name": "John Doe", //string
    "age": 30, //number
    "is_student": false //boolean
  }
}
```

### JSON Nested Object Example:

```json
{
  "person": { //object
    "name": "John Doe", //string
    "age": 30, //number
    "is_student": false, //boolean
    "address": { //nested object
      "street": "123 Main St", //string
      "city": "Anytown", //string
      "state": "NY", //string
      "zip": "12345" //string
    }
  }
}
```

### JSON Nested Array Example:

```json
{
  "person": { //object
    "name": "John Doe", //string
    "age": 30, //number
    "is_student": false, //boolean
    "hobbies": ["reading", "hiking"] //nested array
  }
}
```

### JSON Mixed Data Types Example:

```json
{
  "person": { //object
    "name": "John Doe", //string
    "age": 30, //number
    "is_student": false, //boolean
    "hobbies": ["reading", "hiking"], //array
    "address": { //nested object
      "street": "123 Main St", //string
      "city": "Anytown", //string
      "state": "NY", //string
      "zip": "12345" //string
    }
  }
}
```

## Comments in JSON

JSON does not support comments.

## JSON Parsers

To validate and format JSON data, you can use online parsers.
My favorite online JSON parser is [codebeautify.org](https://codebeautify.org/json-parser-online)

## Conclusion

JSON is a popular data serialization format due to its simplicity and readability. Understanding the basic structure of JSON objects and data types is essential for working with JSON files effectively. Good luck!
