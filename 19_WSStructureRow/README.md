# WSStructureRow

A single element (row) in a `WSStructure`.

## Availability

| Context | Available |
|---------|-----------|
| ![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) | Yes |
| ![UI](https://img.shields.io/badge/UI-green) | Yes |

---

## Methods Summary

| # | Method | Returns | Availability |
|---|--------|---------|--------------|
| 01 | [[] (Get Field)](#01-get-field) | `Any` | EXCHANGE, UI |
| 02 | [[]= (Set Field)](#02-set-field) | `void` | EXCHANGE, UI |

---

## Method Details

### 01. [] (Get Field)

```ruby
#[(field)] ⇒ Any
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the value of the named field, which could be any data type.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `field` | `String` | The field name. |

#### Returns

`Any` — The value of the field.

#### Example

```ruby
puts struct_row['flow']
# => 42.01
```

---

### 02. []= (Set Field)

```ruby
#[(field)]=(value) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the value of the named field. The value's Ruby type should be appropriate for the field, e.g. a date field requires a Ruby `DateTime` object.

> **Note:** For any changes to be saved, the parent `WSStructure#write` method must be called.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `field` | `String` | The field name. |
| `value` | `Any` | The value for the field. Must be an appropriate type for the field. |

#### Returns

`void`

#### Examples

```ruby
struct_row['date_time'] = DateTime.now
struct_row['flow'] = 42.01
```

---

*Documentation generated from the official Autodesk InfoWorks ICM 2025 help pages.*
