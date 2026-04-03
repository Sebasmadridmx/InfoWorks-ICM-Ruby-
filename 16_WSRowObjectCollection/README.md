# WSRowObjectCollection

A collection of `WSRowObject`s.

## Availability

| Context | Available |
|---------|-----------|
| ![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) | Yes |
| ![UI](https://img.shields.io/badge/UI-green) | Yes |

---

## Methods Summary

| # | Method | Returns | Availability |
|---|--------|---------|--------------|
| 01 | [[] (Get Index)](#01-get-index) | `WSRowObject?` | EXCHANGE, UI |
| 02 | [each](#02-each) | `WSRowObject` | EXCHANGE, UI |
| 03 | [length](#03-length) | `Integer` | EXCHANGE, UI |

---

## Method Details

### 01. [] (Get Index)

```ruby
#[(index)] ⇒ WSRowObject?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the `WSRowObject` from the collection at the specified index.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `index` | `Integer` | The index requested (zero-based). |

#### Returns

`WSRowObject?` — The object found, or `nil` if there is no object at this index.

---

### 02. each

```ruby
#each { |ro| ... } ⇒ WSRowObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Iterates through the collection, yielding a `WSRowObject`.

#### Returns

`WSRowObject` — Each object in the collection, yielded in turn.

#### Examples

```ruby
network.row_object_collection('_nodes').each { |ro| puts ro.id }
```

```ruby
network.row_object_collection('_nodes').each do |ro|
  puts ro.id
end
```

---

### 03. length

```ruby
#length ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the length of this collection, i.e. how many `WSRowObject`s it contains.

#### Returns

`Integer` — The number of objects in the collection.

---

*Documentation generated from the official Autodesk InfoWorks ICM 2025 help pages.*
