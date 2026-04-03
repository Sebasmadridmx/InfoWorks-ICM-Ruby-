# WSValidation

A single validation message.

All methods in this class are read only, and return the value of one of the fields found in the UI validation window.

## Availability

| Context | Available |
|---------|-----------|
| ![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) | Yes |
| ![UI](https://img.shields.io/badge/UI-green) | Yes |

---

## Methods Summary

| # | Method | Returns | Availability |
|---|--------|---------|--------------|
| 01 | [code](#01-code) | `Integer` | EXCHANGE, UI |
| 02 | [field](#02-field) | `String` | EXCHANGE, UI |
| 03 | [field_description](#03-field_description) | `String` | EXCHANGE, UI |
| 04 | [message](#04-message) | `String` | EXCHANGE, UI |
| 05 | [object_id](#05-object_id) | `String?` | EXCHANGE, UI |
| 06 | [object_type](#06-object_type) | `String?` | EXCHANGE, UI |
| 07 | [priority](#07-priority) | `Integer` | EXCHANGE, UI |
| 08 | [scenario](#08-scenario) | `String` | EXCHANGE, UI |
| 09 | [type](#09-type) | `String` | EXCHANGE, UI |

---

## Method Details

### 01. code

```ruby
#code ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the code of the validation message.

#### Returns

`Integer` — The validation message code.

---

### 02. field

```ruby
#field ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the field name. This may not be a real database field, but if it is then the actual field name rather than the description (the name used in the UI) will be returned.

#### Returns

`String` — The field name.

#### Example

```ruby
puts validation.field
# => 'wn_node'
```

---

### 03. field_description

```ruby
#field_description ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the field description. The field description is how the field would appear in the UI.

#### Returns

`String` — The UI-facing description of the field.

#### Example

```ruby
puts validation.field_description
# => 'node'
```

---

### 04. message

```ruby
#message ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the text content of the validation message.

#### Returns

`String` — The validation message text.

---

### 05. object_id

```ruby
#object_id ⇒ String?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the object ID from the validation message, if any.

#### Returns

`String?` — The object ID, or `nil` if not present.

---

### 06. object_type

```ruby
#object_type ⇒ String?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the object type from the validation message, if any.

#### Returns

`String?` — The object type, or `nil` if not present.

---

### 07. priority

```ruby
#priority ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the priority of the validation message.

#### Returns

`Integer` — The priority value of the validation message.

---

### 08. scenario

```ruby
#scenario ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the scenario name for the validation message.

#### Returns

`String` — The name of the scenario, or `'base'` for the base scenario.

---

### 09. type

```ruby
#type ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the type of the validation message as a string.

#### Returns

`String` — One of `error`, `warning`, or `information`.

---

*Documentation generated from the official Autodesk InfoWorks ICM 2025 help pages.*
