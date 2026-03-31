# WSModelObjectCollection

A collection of `WSModelObject` objects (including derived classes).

## Availability

| Context | Available |
|---------|-----------|
| EXCHANGE | Yes |
| UI | Yes |

---

## Methods Summary

| # | Method | Return Type | Availability |
|---|--------|-------------|--------------|
| 01 | [[]](#01--get-index) | `WSModelObject?` | EXCHANGE, UI |
| 02 | [each](#02-each) | `WSModelObject` | EXCHANGE, UI |
| 03 | [length](#03-length) | `Integer` | EXCHANGE, UI |

---

## Method Details

### 01. [] (Get Index)

```ruby
#[](index) ⇒ WSModelObject?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the object from the collection at the specified index.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| index | `Integer` | The index requested (zero-based). |

#### Return Value

`WSModelObject`, `nil` — The object found, or `nil` if there is no object at this index.

---

### 02. each

```ruby
#each { |mo| ... } ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Iterates through the collection, yielding a `WSModelObject`.

#### Return Value

`WSModelObject`

#### Example

```ruby
database.model_object_collection('Geometry').each { |mo| puts mo.name }

database.model_object_collection('Geometry').each do |mo|
  puts mo.name
end
```

---

### 03. length

```ruby
#length ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the number of objects in this collection.

#### Return Value

`Integer`
