# WSDatabase

A database, including cloud databases and transportable databases.

The majority of these methods are only available in Exchange, with limited functionality in the UI. A database can be accessed from:
- `WSApplication.open` (Exchange)
- `WSApplication.current_database` (UI)

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
| 01 | [copy_into_root](#01-copy_into_root) | `WSModelObject` | EXCHANGE |
| 02 | [file_root](#02-file_root) | `String` | EXCHANGE, UI |
| 03 | [find_root_model_object](#03-find_root_model_object) | `WSModelObject?` | EXCHANGE, UI |
| 04 | [guid](#04-guid) | `String` | EXCHANGE, UI |
| 05 | [list_read_write_run_fields](#05-list_read_write_run_fields) | `Array<String>` | EXCHANGE, UI |
| 06 | [model_object](#06-model_object) | `WSModelObject?` | EXCHANGE, UI |
| 07 | [model_object_collection](#07-model_object_collection) | `WSModelObjectCollection` | EXCHANGE, UI |
| 08 | [model_object_from_type_and_guid](#08-model_object_from_type_and_guid) | `WSModelObject?` | EXCHANGE, UI |
| 09 | [model_object_from_type_and_id](#09-model_object_from_type_and_id) | `WSModelObject?` | EXCHANGE, UI |
| 10 | [new_model_object](#10-new_model_object) | `WSModelObject` | EXCHANGE |
| 11 | [new_network_name](#11-new_network_name) | `String` | EXCHANGE, UI |
| 12 | [path](#12-path) | `String` | EXCHANGE, UI |
| 13 | [result_root](#13-result_root) | `String` | EXCHANGE |
| 14 | [root_model_objects](#14-root_model_objects) | `WSModelObjectCollection` | EXCHANGE, UI |

---

## Method Details

### 01 copy_into_root
```ruby
database.copy_into_root(object, copy_results, copy_ground_models) => WSModelObject
```
`EXCHANGE`

Copies a `WSModelObject` and any children into the database root, returning the new model object. The object being copied can be from the same database or another database such as a transportable database.

| Parameter | Type | Description |
|---|---|---|
| `object` | WSModelObject | The model object to copy |
| `copy_results` | Boolean | Whether to copy simulation results |
| `copy_ground_models` | Boolean | Whether to copy ground models |
| **Returns** | WSModelObject | The newly copied object in this database |

---

### 02 file_root
```ruby
database.file_root => String
```
`EXCHANGE` `UI`

Returns the path used by this database for files such as GIS layers, also known as the Remote Files Root.

Shown in the UI under `File > Database Settings > Set Remote Roots > Remote Files Root`.

> If this is a standalone database with "force all remote roots to be below the database" enabled, the path will be the folder containing the database.

---

### 03 find_root_model_object
```ruby
database.find_root_model_object(type, name) => WSModelObject?
```
`EXCHANGE` `UI`

Returns the `WSModelObject` at the root (top level) of the database. Model objects at this level have unique names.

Valid types at root level: `Asset Group`, `Model Group`, `Master Group`.

| Parameter | Type | Description |
|---|---|---|
| `type` | String | The scripting type of the object |
| `name` | String | The name of the object (case sensitive) |
| **Returns** | WSModelObject, nil | nil if not found |

---

### 04 guid
```ruby
database.guid => String
```
`EXCHANGE` `UI`

Returns the GUID for the database, also called the database identifier in the UI.

```ruby
puts database.guid
# => 'CEB7E8B9-D383-485C-B085-19F6E3E3C8CD'
```

---

### 05 list_read_write_run_fields
```ruby
database.list_read_write_run_fields => Array<String>
```
`EXCHANGE` `UI`

Returns the field names in run objects that are read-write, i.e. fields that can be set from Exchange scripts.

```ruby
database.list_read_write_run_fields.each { |field| puts field }
```

---

### 06 model_object
```ruby
database.model_object(path) => WSModelObject?
```
`EXCHANGE` `UI`

Finds a `WSModelObject` in the database using its scripting path.

| Parameter | Type | Description |
|---|---|---|
| `path` | String | The scripting path to the object |
| **Returns** | WSModelObject, nil | nil if not found |

```ruby
network = database.model_object('>MODG~My Root Model Group')
raise "Could not find network" if network.nil?
```

---

### 07 model_object_collection
```ruby
database.model_object_collection(type) => WSModelObjectCollection
```
`EXCHANGE` `UI`

Finds all `WSModelObject`s in the database of a given type.

| Parameter | Type | Description |
|---|---|---|
| `type` | String | The scripting type of the object |
| **Returns** | WSModelObjectCollection | Empty collection if no objects of this type exist |

```ruby
database.model_object_collection('Rainfall Event').each do |model_object|
  puts model_object.name
end
```

---

### 08 model_object_from_type_and_guid
```ruby
database.model_object_from_type_and_guid(type, guid) => WSModelObject?
```
`EXCHANGE` `UI`

Finds a `WSModelObject` in the database using its scripting type and GUID. The GUID can be found in the UI via the properties dialog.

| Parameter | Type | Description |
|---|---|---|
| `type` | String | The scripting type of the object |
| `guid` | String | The creation GUID |
| **Returns** | WSModelObject, nil | nil if not found |

```ruby
rainfall = database.model_object_from_type_and_guid('Rainfall Event', '{CEB7E8B9-D383-485C-B085-19F6E3E3C8CD}')
raise "Could not find rainfall" if rainfall.nil?
```

---

### 09 model_object_from_type_and_id
```ruby
database.model_object_from_type_and_id(type, id) => WSModelObject?
```
`EXCHANGE` `UI`

Finds a `WSModelObject` in the database using its scripting type and ID. The ID can be found in the UI via the properties dialog.

| Parameter | Type | Description |
|---|---|---|
| `type` | String | The scripting type of the object |
| `id` | Integer | The model ID |
| **Returns** | WSModelObject, nil | nil if not found |

```ruby
rainfall = database.model_object_from_type_and_id('Rainfall Event', 1)
raise "Could not find rainfall" if rainfall.nil?
```

---

### 10 new_model_object
```ruby
database.new_model_object(type, name) => WSModelObject
```
`EXCHANGE`

Creates a `WSModelObject` in the root of the database.

Valid object types at root level: `Asset Group`, `Model Group`, `Master Group`.

| Parameter | Type | Description |
|---|---|---|
| `type` | String | The scripting type, must be valid for root level |
| `name` | String | The name of the new object, must be unique |
| **Returns** | WSModelObject | |

**Exceptions:**

| Error | Cause |
|---|---|
| `unrecognised type` | Object type is not valid |
| `invalid object type for the root of a database` | Type is valid but not allowed at root level |
| `an object of this type and name already exists in root of database` | Name must be unique |
| `licence and/or permissions do not permit creation` | Licence or permission restriction |
| `unable to create object` | Creation failed for another reason |

---

### 11 new_network_name
```ruby
database.new_network_name(type, name, branch, add) => String
```
`EXCHANGE` `UI`

Generates a new unique network name based on an existing name. Intended for use when creating a new network model object.

| Parameter | Type | Description |
|---|---|---|
| `type` | String | The scripting type of the object |
| `name` | String | The base name |
| `branch` | Boolean | If true, uses underscore e.g. `mynetwork_1`, if false uses hash e.g. `mynetwork#1` |
| `add` | Boolean | If true, always appends `#1` or `_1` instead of incrementing |
| **Returns** | String | The new unique name |

```ruby
new_name = database.new_network_name('Model Network', 'Badger', false, false)
# => 'Badger#1'
```

---

### 12 path
```ruby
database.path => String
```
`EXCHANGE` `UI`

Returns the path of the database. This is the same path used by `WSApplication.open`.

| Database type | Example path |
|---|---|
| Transportable | `'C:/Badger/MyDatabase.icmt'` |
| Standalone | `'C:/Badger/MyDatabase.icmm'` |
| Workgroup | `'localhost:40000/Badger/MyDatabase'` |

---

### 13 result_root
```ruby
database.result_root => String
```
`EXCHANGE`

Returns the path used by this database for results files when results are stored on server, also known as the Remote Results Root.

Shown in the UI under `File > Database Settings > Set Remote Roots > Remote Results Root`.

> If this is a standalone database with "force all remote roots to be below the database" enabled, the path will be the folder containing the database.

---

### 14 root_model_objects
```ruby
database.root_model_objects => WSModelObjectCollection
```
`EXCHANGE` `UI`

Finds all objects at the root (top level) of the database.

| **Returns** | WSModelObjectCollection | All root-level model objects |
|---|---|---|
