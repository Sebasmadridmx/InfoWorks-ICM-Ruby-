# WSTableInfo

Metadata for a network table. This only contains information about the table structure, not the current values for any particular object.

## Availability

| Context | Available |
|---------|-----------|
| ![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) | Yes |
| ![UI](https://img.shields.io/badge/UI-green) | Yes |

---

## Methods Summary

| # | Method | Returns | Availability |
|---|--------|---------|--------------|
| 01 | [description](#01-description) | `String` | EXCHANGE, UI |
| 02 | [fields](#02-fields) | `Array<WSFieldInfo>` | EXCHANGE, UI |
| 03 | [name](#03-name) | `String` | EXCHANGE, UI |
| 04 | [results_fields](#04-results_fields) | `Array<WSFieldInfo>` | EXCHANGE, UI |
| 05 | [tableinfo_json](#05-tableinfo_json) | `String` | EXCHANGE, UI |

---

## Method Details

### 01. description

```ruby
#description ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the description of the table.

#### Returns

`String` — The description of the table.

---

### 02. fields

```ruby
#fields ⇒ Array<WSFieldInfo>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the fields of this table as an array of `WSFieldInfo` objects. Flags are treated as separate fields.

#### Returns

`Array<WSFieldInfo>` — An array of field info objects for all fields in the table.

---

### 03. name

```ruby
#name ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the internal name of the table.

#### Returns

`String` — The internal name of the table.

---

### 04. results_fields

```ruby
#results_fields ⇒ Array<WSFieldInfo>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the results fields of this table as an array of `WSFieldInfo` objects.

> **Note:** This method is only available when the `WSTableInfo` object was accessed from a network with simulation results available. The fields returned reflect the results in that simulation, including the values of their `#has_time_varying_results?` and `#has_max_results?` methods. This can vary considerably depending on the type of simulation, run configuration, results selector, etc.

#### Returns

`Array<WSFieldInfo>` — An array of field info objects for all results fields in the table.

---

### 05. tableinfo_json

```ruby
#tableinfo_json ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the table information as a JSON string.

#### Returns

`String` — A JSON representation of the table metadata.

---

*Documentation generated from the official Autodesk InfoWorks ICM 2025 help pages.*
