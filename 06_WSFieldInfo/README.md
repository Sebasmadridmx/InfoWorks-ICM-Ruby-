# WSFieldInfo

Metadata for a field in a network table. This only contains information about the table structure, not the current values for any particular object.

---

## Availability

| Tag | Meaning |
|---|---|
| `EXCHANGE` | Available in Exchange scripts |
| `UI` | Available in UI scripts |

---

## Methods

| # | Method | Returns | Available |
|---|---|---|---|
| 01 | [data_type](#01-data_type) | `String` | EXCHANGE, UI |
| 02 | [description](#02-description) | `String` | EXCHANGE, UI |
| 03 | [fields](#03-fields) | `Array<WSFieldInfo>?` | EXCHANGE, UI |
| 04 | [has_time_varying_results](#04-has_time_varying_results) | `Boolean` | EXCHANGE, UI |
| 05 | [name](#05-name) | `String` | EXCHANGE, UI |
| 06 | [read_only](#06-read_only) | `Boolean` | EXCHANGE, UI |
| 07 | [size](#07-size) | `Integer` | EXCHANGE, UI |

---

## Method Details

### 01 data_type
```ruby
field_info.data_type => String
```
`EXCHANGE` `UI`

Returns the data type of the field as a string. This is the InfoWorks type, not the Ruby type.

**Type mapping:**

| WS Type | Ruby Type |
|---|---|
| `Flag` | String |
| `Boolean` | Boolean |
| `Single` | Float |
| `Double` | Float |
| `Short` | Integer |
| `Long` | Integer |
| `Date` | DateTime |
| `String` | String |
| `Array:Long` | Array\<Integer\> |
| `Array:Double` | Array\<Float\> |
| `WSStructure` | WSStructure |
| `GUID` | String |

> Note: Ruby does not have specific types for Single/Double floating point numbers or Short/Long integers.

---

### 02 description
```ruby
field_info.description => String
```
`EXCHANGE` `UI`

Returns the field description, which is the name of the field as it appears in the UI.

---

### 03 fields
```ruby
field_info.fields => Array<WSFieldInfo>?
```
`EXCHANGE` `UI`

Returns an array of fields if the field is a structure blob, i.e. it contains rows of structured data. Returns nil if the field is not a structure blob.

| **Returns** | Array\<WSFieldInfo\>, nil | nil if not a structure blob |
|---|---|---|

---

### 04 has_time_varying_results
```ruby
field_info.has_time_varying_results? => Boolean
```
`EXCHANGE` `UI`

Returns whether the field has time varying results. Will always be false for network fields. See `WSTableInfo.results_fields` for result fields.

---

### 05 name
```ruby
field_info.name => String
```
`EXCHANGE` `UI`

Returns the database name of the field, i.e. the name used with Ruby methods.

---

### 06 read_only
```ruby
field_info.read_only? => Boolean
```
`EXCHANGE` `UI`

Returns whether the field is read only.

---

### 07 size
```ruby
field_info.size => Integer
```
`EXCHANGE` `UI`

Returns the maximum length of a string field. Flag fields will always be length 4. Any field that is not a string type will return 0.
