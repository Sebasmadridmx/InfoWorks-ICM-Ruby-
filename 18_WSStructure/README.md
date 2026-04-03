# WSStructure

A structure blob field of a `WSRowObject`, i.e. a field that contains an array of structured data.

It is a collection of `WSStructureRow` objects, each of which represents a single row / entry in the structure. The collection has a fixed length which can be updated with the `length=` method. You cannot dynamically insert or remove objects. You must first set the length and then access objects by their index.

> **Important:** If any changes are made to the length or the `WSStructureRow` objects, the `write` method must be called on both this object **and** the parent `WSRowObject`.

## Availability

| Context | Available |
|---------|-----------|
| ![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) | Yes |
| ![UI](https://img.shields.io/badge/UI-green) | Yes |

---

## Methods Summary

| # | Method | Returns | Availability |
|---|--------|---------|--------------|
| 01 | [[] (Get Index)](#01-get-index) | `WSStructureRow?` | EXCHANGE, UI |
| 02 | [each](#02-each) | `WSStructureRow` | EXCHANGE, UI |
| 03 | [length](#03-length) | `Integer` | EXCHANGE, UI |
| 04 | [length= (Set)](#04-length-set) | `void` | EXCHANGE, UI |
| 05 | [write](#05-write) | `void` | EXCHANGE, UI |

---

## Method Details

### 01. [] (Get Index)

```ruby
#[(index)] ⇒ WSStructureRow?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the object from the collection at the specified index.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `index` | `Integer` | The index requested (zero-based). |

#### Returns

`WSStructureRow?` — The object found, or `nil` if there is no object at this index.

---

### 02. each

```ruby
#each { |row| ... } ⇒ WSStructureRow
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Iterates through the collection, yielding a `WSStructureRow` object. This is similar to iterating through the rows of a table.

#### Returns

`WSStructureRow` — Each row in the structure, yielded in turn.

#### Examples

```ruby
struct.each { |row| puts row['date_time'] }
```

```ruby
struct.each do |row|
  puts row['date_time']
end
```

---

### 03. length

```ruby
#length ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the length of the structure, i.e. how many rows it contains. Each row is a `WSStructureRow` object.

#### Returns

`Integer` — The number of rows in the structure.

---

### 04. length= (Set)

```ruby
#length=(length) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the length of the structure, i.e. how many rows it contains. Each row is a `WSStructureRow` object.

To add rows to the structure, you must first use this method to set the appropriate length. You can reference the current length to append a single row.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `length` | `Integer` | The new length of the structure. |

#### Returns

`void`

#### Example

```ruby
# Add one new row to the structure
structure.length = structure.length + 1
```

---

### 05. write

```ruby
#write ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Writes any changes to this object and the `WSStructureRow` objects it contains.

> **Note:** The `#write` method on the parent `WSRowObject` must also be called.

#### Returns

`void`

---

*Documentation generated from the official Autodesk InfoWorks ICM 2025 help pages.*
