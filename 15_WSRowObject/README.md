# WSRowObject

An individual object in a network.

> **Note:** Methods that return this type of object may actually return a derived class, for example a `WSNode` for nodes or `WSLink` for links.

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
| 03 | [_* (Get Tag)](#03-get-tag) | `Any` | EXCHANGE, UI |
| 04 | [_*= (Set Tag)](#04-set-tag) | `void` | EXCHANGE, UI |
| 05 | [autoname](#05-autoname) | `void` | EXCHANGE, UI |
| 06 | [category](#06-category) | `String` | EXCHANGE, UI |
| 07 | [contains?](#07-contains) | `Boolean` | EXCHANGE, UI |
| 08 | [delete](#08-delete) | `void` | EXCHANGE, UI |
| 09 | [field](#09-field) | `WSFieldInfo?` | EXCHANGE, UI |
| 10 | [gauge_results](#10-gauge_results) | `Array<Float>` | EXCHANGE, UI |
| 11 | [id](#11-id) | `String` | EXCHANGE, UI |
| 12 | [id= (Set)](#12-id-set) | `void` | EXCHANGE, UI |
| 13 | [is_inside?](#13-is_inside) | `Boolean` | EXCHANGE, UI |
| 14 | [navigate](#14-navigate) | `Array<WSRowObject>` | EXCHANGE, UI |
| 15 | [navigate1](#15-navigate1) | `WSRowObject?` | EXCHANGE, UI |
| 16 | [objects_in_polygon](#16-objects_in_polygon) | `Array<WSRowObject>` | EXCHANGE, UI |
| 17 | [result](#17-result) | `Float` | EXCHANGE, UI |
| 18 | [results](#18-results) | `Array<Float>` | EXCHANGE, UI |
| 19 | [selected= (Set)](#19-selected-set) | `void` | EXCHANGE, UI |
| 20 | [selected?](#20-selected) | `Boolean` | EXCHANGE, UI |
| 21 | [table](#21-table) | `String` | EXCHANGE, UI |
| 22 | [table_info](#22-table_info) | `WSTableInfo` | EXCHANGE, UI |
| 23 | [write](#23-write) | `void` | EXCHANGE, UI |

---

## Method Details

### 01. [] (Get Field)

```ruby
#[(field)] ⇒ Any
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the value of a field, using hash-like syntax. May return a simple value, or a `WSStructure` if the field is a structure blob.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `field` | `String` | The name of the field. |

#### Returns

`Any` — The value of the field. May be a simple value or a `WSStructure` for structure blob fields.

#### Example

```ruby
puts node['node_id']
# => 'Badger'
```

---

### 02. []= (Set Field)

```ruby
#[(field)]=(value) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the value of a field, using hash-like syntax. The value must be an appropriate type for the field. This cannot be used to set structure blobs.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `field` | `String` | The name of the field. |
| `value` | `Any` | The value, must be an appropriate type for the field. |

#### Returns

`void`

#### Example

```ruby
node['node_id'] = 'Badger'
```

---

### 03. _* (Get Tag)

```ruby
#_* ⇒ Any
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Reads the value of a tag. Tags are temporary values added to the object during the script. The `*` in the method name is replaced with the tag name (e.g. `_badger`).

#### Returns

`Any` — The value of the tag.

#### Example

```ruby
puts mo._badger
# => 'Penguin'
```

---

### 04. _*= (Set Tag)

```ruby
#_*=(value) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the value of a tag. Tags are user-defined temporary values added to the object during the script. Tag names can contain only alphanumeric characters (letters and numbers).

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `value` | `Any` | The value to assign to the tag. |

#### Returns

`void`

#### Example

```ruby
mo._badger = 'Penguin'
```

---

### 05. autoname

```ruby
#autoname ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the ID of this object using the current network autoname convention.

#### Returns

`void`

---

### 06. category

```ruby
#category ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the category name of the object, e.g. `_nodes`, `_links`.

#### Returns

`String` — The category name of the object.

---

### 07. contains?

```ruby
#contains(other) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

If this object is a polygon, checks if another `WSRowObject` is inside it. This is effectively the inverse of the `#is_inside?` method.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `other` | `WSRowObject` | The other object. |

#### Returns

`Boolean` — `true` if the other object is inside this polygon.

---

### 08. delete

```ruby
#delete ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Deletes the row object. This is immediate and does not require the `#write` method.

#### Returns

`void`

---

### 09. field

```ruby
#field(name) ⇒ WSFieldInfo?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the `WSFieldInfo` object for a given field name. This only returns information about the named field such as its data type, not any data associated with this particular object.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `name` | `String` | The name of the field. |

#### Returns

`WSFieldInfo?` — The field info object, or `nil` if not found.

---

### 10. gauge_results

```ruby
#gauge_results(field) ⇒ Array<Float>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns an array of values for the given results field name, at all gauge time-steps. The field must have time-varying results.

If the object or field does not have gauge results it will return the regular results. If the simulation results time-step multiplier is 0, this method will return no results, even if gauge results are available in the user interface.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `field` | `String` | The name of the results field. |

#### Returns

`Array<Float>` — An array of result values at all gauge time-steps.

---

### 11. id

```ruby
#id ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the ID of the object. If the object has a multi-part primary key (such as a link) then the key will be output with parts separated by a `.` character, similar to accessing the OID field in SQL.

#### Returns

`String` — The ID of the object.

#### Example

```ruby
puts node.id
# => "ST39469"

puts link.id
# => "ST41337.ST34322.1"
```

---

### 12. id= (Set)

```ruby
#id=(new_id) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the ID of the object. Will raise an exception if the ID cannot be set, e.g. if it is a duplicate.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `new_id` | `String` | The new ID, which must be unique and formatted the same way as an ID retrieved from the `#id` method. |

#### Returns

`void`

#### Exceptions

Raises an exception if the new ID is a duplicate or otherwise invalid.

---

### 13. is_inside?

```ruby
#is_inside?(other) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Checks if this object is inside a polygon.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `other` | `WSRowObject` | The other object, which should be a polygon. |

#### Returns

`Boolean` — `true` if this object is inside the other `WSRowObject`.

---

### 14. navigate

```ruby
#navigate(type) ⇒ Array<WSRowObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Navigates between objects and other objects based on their relationship. Supports one-to-one and one-to-many relationships, and returns an array of objects.

See also: [`#navigate1`](#15-navigate1)

#### Navigation Types

| Name | Has Results | One to Many |
|------|-------------|-------------|
| `alt_demand` | No | No |
| `cctv_surveys` | No | Yes |
| `custom` | No | No |
| `data_logger` | No | No |
| `drain_tests` | No | Yes |
| `ds_flow_links` | Yes | Yes |
| `ds_links` | Yes | Yes |
| `ds_node` | Yes | No |
| `dye_tests` | No | Yes |
| `gps_surveys` | No | Yes |
| `hydrant_tests` | No | Yes |
| `incidents` | No | Yes |
| `joined` | No | No |
| `joined_pipes` | No | Yes |
| `lateral_pipe` | No | No |
| `maintenance_records` | No | Yes |
| `manhole_repairs` | No | Yes |
| `manhole_surveys` | No | Yes |
| `meter_tests` | No | Yes |
| `meters` | No | Yes |
| `monitoring_surveys` | No | Yes |
| `node` | Yes | No |
| `pipe` | Yes | No |
| `pipe_cleans` | No | Yes |
| `pipe_repairs` | No | Yes |
| `pipe_samples` | No | Yes |
| `properties` | No | Yes |
| `property` | No | No |
| `sanitary_manhole` | No | No |
| `sanitary_pipe` | No | No |
| `smoke_defects` | No | Yes |
| `smoke_test` | No | No |
| `smoke_tests` | No | Yes |
| `storm_manhole` | No | No |
| `storm_pipe` | No | No |
| `us_flow_links` | Yes | Yes |
| `us_links` | Yes | Yes |
| `us_node` | Yes | No |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `type` | `String` | The navigation type. See navigation types table above. |

#### Returns

`Array<WSRowObject>` — An array of related objects.

---

### 15. navigate1

```ruby
#navigate1(type) ⇒ WSRowObject?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Navigates between objects and other objects based on their relationship. Supports one-to-one relationships, and returns a single object if found.

See also: [`#navigate`](#14-navigate)

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `type` | `String` | The navigation type. See navigation types table in [`#navigate`](#14-navigate). |

#### Returns

`WSRowObject?` — The related object, or `nil` if not found.

---

### 16. objects_in_polygon

```ruby
#objects_in_polygon(type) ⇒ Array<WSRowObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

If this object is a polygon, returns an array of the `WSRowObject` objects inside it, matching the type parameter.

When using an array of strings as the `type`, all values must be unique (no duplicates) and cannot contain a category and a table within the same category. This is similar to the `WSNumbatNetworkObject.search_at_point` method.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `type` | `String`, `Array<String>`, `nil` | The name(s) of a type or category of object. `nil` will search all tables. |

#### Returns

`Array<WSRowObject>` — An array of objects inside this polygon matching the given type.

---

### 17. result

```ruby
#result(field) ⇒ Float
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the value for the given results field, at the current time-step.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `field` | `String` | The name of the results field. |

#### Returns

`Float` — The result value at the current time-step.

---

### 18. results

```ruby
#results(field) ⇒ Array<Float>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns an array of values for the given results field name, at all timesteps. The field must have time-varying results.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `field` | `String` | The name of the results field. |

#### Returns

`Array<Float>` — An array of result values at all timesteps.

---

### 19. selected= (Set)

```ruby
#selected=(bool) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets whether this object is selected or deselected. This does not need to occur within a transaction.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `bool` | `Boolean` | If the object is selected. Can be an explicit `true` or `false`, or a statement that evaluates to `true` or `false`. |

#### Returns

`void`

---

### 20. selected?

```ruby
#selected? ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns whether the object is currently selected.

#### Returns

`Boolean` — `true` if the object is currently selected.

---

### 21. table

```ruby
#table ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the object's table name.

#### Returns

`String` — The table name of the object.

---

### 22. table_info

```ruby
#table_info ⇒ WSTableInfo
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns a `WSTableInfo` for this object's table, which contains metadata about the table structure.

#### Returns

`WSTableInfo` — The table info object for this object's table.

---

### 23. write

```ruby
#write ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Writes any changes to the object, such as modified field values.

#### Returns

`void`

---

*Documentation generated from the official Autodesk InfoWorks ICM 2025 help pages.*
