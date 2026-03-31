# WSModelObject

An object that exists in the database tree such as model groups, networks, selection lists, and stored queries.

Methods that return a `WSModelObject` may return a derived class, for example a `WSNumbatNetworkObject` for network types, or `WSSimObject` for simulations.

## Availability

| Context | Available |
|---------|-----------|
| EXCHANGE | Yes |
| UI | Partial (see individual methods) |

---

## Methods Summary

| # | Method | Return Type | Availability |
|---|--------|-------------|--------------|
| 01 | [!=](#01-does-not-equal) | `Boolean` | EXCHANGE, UI |
| 02 | [==](#02-equals) | `Boolean` | EXCHANGE, UI |
| 03 | [[]](#03--get-field) | `Any` | EXCHANGE, UI |
| 04 | [[]=](#04--set-field) | `void` | EXCHANGE, UI |
| 05 | [bulk_delete](#05-bulk_delete) | `void` | EXCHANGE, UI |
| 06 | [children](#06-children) | `WSModelObjectCollection` | EXCHANGE, UI |
| 07 | [comment](#07-comment) | `String` | EXCHANGE |
| 08 | [comment=](#08-comment-set) | `void` | EXCHANGE |
| 09 | [compare](#09-compare) | `Boolean` | EXCHANGE |
| 10 | [copy_here](#10-copy_here) | `WSModelObject` | EXCHANGE, UI |
| 11 | [csv_import_tvd](#11-csv_import_tvd) | `Array` | EXCHANGE |
| 12 | [deletable?](#12-deletable) | `Boolean` | EXCHANGE |
| 13 | [delete](#13-delete) | `void` | EXCHANGE, UI |
| 14 | [delete_results](#14-delete_results) | `void` | EXCHANGE |
| 15 | [export](#15-export) | `void` | EXCHANGE |
| 16 | [find_child_model_object](#16-find_child_model_object) | `WSModelObject?` | EXCHANGE, UI |
| 17 | [id](#17-id) | `Integer` | EXCHANGE, UI |
| 18 | [import_all_sw_model_objects](#18-import_all_sw_model_objects) | `Array<WSModelObject>` | EXCHANGE |
| 19 | [import_data](#19-import_data) | `void` | EXCHANGE |
| 20 | [import_grid_ground_model](#20-import_grid_ground_model) | `void` | EXCHANGE |
| 21 | [import_infodrainage_object](#21-import_infodrainage_object) | `WSModelObject` | EXCHANGE |
| 22 | [import_new_model_object](#22-import_new_model_object) | `WSModelObject` | EXCHANGE |
| 23 | [import_new_model_object_from_generic_csv_files](#23-import_new_model_object_from_generic_csv_files) | `Array<WSModelObject, String>` | EXCHANGE |
| 24 | [import_new_sw_model_object](#24-import_new_sw_model_object) | `WSModelObject` | EXCHANGE |
| 25 | [import_tvd](#25-import_tvd) | `void` | EXCHANGE |
| 26 | [modified_by](#26-modified_by) | `String` | EXCHANGE, UI |
| 27 | [name](#27-name) | `String` | EXCHANGE, UI |
| 28 | [name=](#28-name-set) | `void` | EXCHANGE, UI |
| 29 | [new_model_object](#29-new_model_object) | `WSModelObject` | EXCHANGE, UI |
| 30 | [new_risk_analysis_run](#30-new_risk_analysis_run) | `WSRiskAnalysisRunObject` | EXCHANGE |
| 31 | [new_run](#31-new_run) | `WSModelObject` | EXCHANGE |
| 32 | [new_synthetic_rainfall](#32-new_synthetic_rainfall) | `void` | EXCHANGE |
| 33 | [open](#33-open) | `WSModelObject` | EXCHANGE, UI |
| 34 | [parent_id](#34-parent_id) | `Integer` | EXCHANGE, UI |
| 35 | [parent_type](#35-parent_type) | `String` | EXCHANGE, UI |
| 36 | [path](#36-path) | `String` | EXCHANGE, UI |
| 37 | [type](#37-type) | `String` | EXCHANGE, UI |
| 38 | [update_to_latest](#38-update_to_latest) | `void` | EXCHANGE |

---

## Method Details

### 01. != (Does Not Equal)

```ruby
#!=(other_mo) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Checks if this model object is not the same as another model object (inequality check).

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| other_mo | `WSModelObject` | The model object to compare against. |

#### Return Value

`Boolean` — `true` if the objects are not the same, `false` if they are.

---

### 02. == (Equals)

```ruby
#==(other_mo) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Checks if this model object is the same as another model object (equality check).

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| other_mo | `WSModelObject` | The model object to compare against. |

#### Return Value

`Boolean` — `true` if the objects are the same, `false` otherwise.

---

### 03. [] (Get Field)

```ruby
#[](field) ⇒ Any
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the value of a field.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| field | `String` | Name of the field. |

#### Return Value

`Any` — The value of the specified field.

---

### 04. []= (Set Field)

```ruby
#[]=(field, value) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the value of a field.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| field | `String` | Name of the field. |
| value | `Any` | Value to set. If this field references a database object the value can be the id, scripting path, or a `WSModelObject` of the correct type. |

#### Return Value

`void`

---

### 05. bulk_delete

```ruby
#bulk_delete ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Permanently deletes the object and all of its children, skipping the recycle bin.

This method works even if the object has children or is used in a simulation, which does not follow the user interface convention. For a safer version of this method, see [`#delete`](#13-delete).

#### Return Value

`void`

---

### 06. children

```ruby
#children ⇒ WSModelObjectCollection
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the children of the object.

#### Return Value

`WSModelObjectCollection`

---

### 07. comment

```ruby
#comment ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the comment, also known as the description in the user interface.

#### Return Value

`String`

---

### 08. comment= (Set)

```ruby
#comment=(text) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Sets the comment, also known as the description in the user interface.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| text | `String` | The comment text. |

#### Return Value

`void`

---

### 09. compare

```ruby
#compare(other) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Compares this model object to another. Both model objects must be the same type of version controlled object or simulation results.

Simulation results can only be compared if they are both from the current database.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| other | `WSModelObject` | The object to compare. |

#### Return Value

`Boolean` — `true` if the objects are identical.

#### Example

```ruby
if mo.compare(mo2)
  puts 'Networks are the same!'
else
  puts 'Networks are not the same!'
end
```

---

### 10. copy_here

```ruby
#copy_here(object, copy_results, copy_ground_models) ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Copies a model object and any children as a child of this object, returning the new model object. The model object being copied can be from the same database or another database such as a transportable database.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| object | `WSModelObject` | The model object to copy. |
| copy_results | `Boolean` | Whether to copy simulation results, if the model object (or its children) have simulations with results. |
| copy_ground_models | `Boolean` | Whether to copy ground models. |

#### Return Value

`WSModelObject` — The newly copied object in this database.

---

### 11. csv_import_tvd

```ruby
#csv_import_tvd(file, name, config_file) ⇒ Array
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Performs an import of time varying data into an asset group, creating one or more time varying data objects in the same manner as the user interface when the import time varying data from generic CSV option is used.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Path to the file. |
| name | `String` | Root name of the new object. |
| config_file | `String` | Path to the config file, saved from the UI. |

#### Return Value

`Array`

---

### 12. deletable?

```ruby
#deletable? ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns whether this model object can be deleted using the [`#delete`](#13-delete) method, which follows user interface rules: the object must have no children and must not be used in a simulation.

#### Return Value

`Boolean`

---

### 13. delete

```ruby
#delete ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Deletes the object, provided it meets the user interface rules: has no children, and is not used in a simulation.

This is a safer alternative to [`#bulk_delete`](#05-bulk_delete), which ignores these rules.

#### Return Value

`void`

---

### 14. delete_results

```ruby
#delete_results ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Deletes the results, if this object is a simulation.

#### Return Value

`void`

---

### 15. export

```ruby
#export(path, format) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Exports the model object in the appropriate format. The formats permitted depend on the object type. The format string may affect both the data exported and the format in which it is exported.

**InfoWorks text file format** (empty string `""`): Used for Inflow, Level, Infiltration, Waste Water, Trade Waste, Rainfall Event (non-synthetic), Pipe Sediment Data, Observed Flow/Depth/Velocity Events, Layer List, Regulator.

**Rainfall event format codes** (text file output):

| Code | Description |
|------|-------------|
| `CRD` | Catchment Runoff Data |
| `CSD` | Catchment Sediment Data |
| `EVP` | Evaporation |
| `ISD` | Initial Snow Data |
| `TEM` | Temperature Data |
| `WND` | Wind Data |

**CSV format** (`"CSV"`): Used for Level, Infiltration, Inflow, Observed Flow/Depth/Velocity, Rainfall Event (synthetic), Regulator, Damage Function, Waste Water, Trade Waste.

**Risk Analysis Results** export format strings:

- `"Receptor Damages"`
- `"Component Damages"`
- `"Code Damages"`
- `"Impact Zone Damages"`
- `"Category Damages"`
- `"Inundation Depth Results"`

**Risk Analysis Sim** export format strings:

- `"Receptor vs Code"`
- `"Receptor vs Component"`
- `"Code vs Component"`
- `"Impact Zone vs Code"`
- `"Impact Zone Code vs Component"`
- `"Category Code vs Component"`

**InfoAsset Manager dashboards**: Format must be `"html"`. Note that additional files are exported alongside the HTML file in the same folder; exporting the same dashboard to different filenames in the same folder will not give the intended results. Export to different folders instead.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| path | `String` | Path to the export file. |
| format | `String` | Export format string. See description for valid values. |

#### Return Value

`void`

---

### 16. find_child_model_object

```ruby
#find_child_model_object(type, name) ⇒ WSModelObject?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Finds a child model object of a given type and name.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | The type of the object. |
| name | `String` | The name of the object. |

#### Return Value

`WSModelObject?` — The matching child object, or `nil` if not found.

---

### 17. id

```ruby
#id ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the ID of this model object.

#### Return Value

`Integer`

---

### 18. import_all_sw_model_objects

```ruby
#import_all_sw_model_objects(file, format, scenario, logfile) ⇒ Array<WSModelObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports all SWMM model objects from a supported file. This `WSModelObject` must be of a suitable type to contain the model objects imported.

**Object types imported:** SWMM Network, Inflow, IWSW Run, IWSW Time Patterns, Selection List, Level, Rainfall Event, IWSW pollutograph, IWSW Climatology, Regulator.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Path to the file for import. |
| format | `String` | Object format to import: `inp` for swmm5, `xpx` for xpswmm/xpstorm, or `mxd` for infoswmm. |
| scenario | `String` | Scenario name, only used when importing an `mxd` file. |
| logfile | `String` | Path to a log file, ending with a `.txt` extension. |

#### Return Value

`Array<WSModelObject>`

---

### 19. import_data

```ruby
#import_data(format, file) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports data into this object. This is only relevant for rainfall events and pollutographs, as they contain multiple pages of data which must be imported and exported separately.

Options for populating an object:
- Create an empty object and import all data items using this method.
- Import the first data item using [`#import_new_model_object`](#22-import_new_model_object) and import subsequent items using this method. For rainfall events the first item must be the rainfall; for pollutographs it can be any item.

Both InfoWorks CSV and InfoWorks file formats are supported. Use `'CSV'` for CSV files, or another string for InfoWorks files.

**Rainfall event format codes:** `SMD`, `EVP`, `SOL`, `WND`, `TEM`, `CSD`, `ISD`, `CRD`, `RED` (for RED, `nil` or `''` is also accepted).

**CSV files for rainfall events** may only be used for time varying data: Rainfall, Temperature, Wind, Evaporation, Solar Radiation, Soil Moisture Deficit.

**Pollutograph format:** The pollutograph code.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| format | `String` | File format. Use `'CSV'` for CSV, or the appropriate format code. |
| file | `String` | Path to the file. |

#### Return Value

`void`

#### Example

```ruby
mo_rain.import_data('CSV', 'C:/temp/MyRain_EVP.csv')
mo_rain.import_data('SMD', 'C:/temp/MyRain.smd')
mo_pollutograph.import_data('CSV', 'C:/temp/P.csv')
```

---

### 20. import_grid_ground_model

```ruby
#import_grid_ground_model(polygon, files, options) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports a gridded ground model. This `WSModelObject` must be a model group or asset group.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| polygon | `WSRowObject`, `nil` | An object with polygon geometry from a currently open `WSOpenNetwork`. Only used if `use_polygon` is `true` in options. |
| files | `Array<String>` | Array of file paths. |
| options | `Hash` | Options hash. See table below. |

**Options hash keys:**

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `ground_model_name` | `String` | | Must be non-empty and unique in group. |
| `data_type` | `String` | | Displayed in the UI. |
| `cell_size` | `Float` | `1` | Must be non-zero. |
| `unit_multiplier` | `Float` | `0.001` | Must be non-zero. |
| `xy_unit_multiplier` | `Float` | `1` | Must be non-zero. |
| `systematic_error` | `Float` | `0` | |
| `use_polygon` | `Boolean` | `false` | If `true`, polygon must be non-nil. |
| `integer_format` | `Boolean` | `true` | |

#### Return Value

`void`

#### Example

```ruby
model_group = database.model_object_from_type_and_id('Model Group', 2)
files = ['C:/temp/small_grid.asc']
options = {
  'ground_model_name' => 'my_ground_model',
  'data_type' => 'badger',
  'cell_size' => 5.0,
  'unit_multiplier' => 1.0,
  'xy_multiplier' => 1.0,
  'integer_format' => false,
  'use_polygon' => false
}
model_group.import_grid_ground_model(nil, files, options)
```

---

### 21. import_infodrainage_object

```ruby
#import_infodrainage_object(file, type, log) ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports an InfoDrainage object. This `WSModelObject` must be a model group.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Path to the InfoDrainage file to import, with `.idxx` extension. |
| type | `String` | Type of object to import. The only accepted value is `inflow`. |
| log | `String` | Path to save the import log. |

#### Return Value

`WSModelObject`

---

### 22. import_new_model_object

```ruby
#import_new_model_object(type, name, format, file, event) ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports a new model object from a file, as a child of this `WSModelObject`. This must be a suitable type to contain the new model object.

**Permitted types:** Inflow, Level, Ground Infiltration, Waste Water, Trade Waste, Rainfall Event (non-synthetic), Pipe Sediment Data, Observed Flow Event, Observed Depth Event, Observed Velocity Event, Layer List, Regulator, Damage Function, Pollutograph.

**Permitted formats:**
- `""` (empty string) for InfoWorks format files.
- `"CSV"` for InfoWorks CSV format (not available for layer lists or damage functions).
- `"CSV"` for Pollutographs (data imported depends on the CSV file).
- The 3-letter pollutograph code (only one pollutant can be imported; use [`#import_data`](#19-import_data) for additional pollutants or rainfall data items).

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | See supported types in method description. |
| name | `String` | Name of the imported object. |
| format | `String` | See supported formats in method description. |
| file | `String` | Path to the file. |
| event | `Integer` | Optional from version 11.5; should be set to `0` if used. |

#### Return Value

`WSModelObject`

#### Example

```ruby
rainfall = model_group.import_new_model_object('Rainfall Event', 'The Rainfall', '', 'C:/temp/1.red')
```

---

### 23. import_new_model_object_from_generic_csv_files

```ruby
#import_new_model_object_from_generic_csv_files(type, name, file, config) ⇒ Array<WSModelObject, String>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports a new model object using the generic CSV importer, as a child of this `WSModelObject`. Requires a config file previously set up in the UI.

**Permitted types:** Inflow, Level, Infiltration, Rainfall Event (non-synthetic), Pipe Sediment Data, Observed Flow Event, Observed Depth Event, Observed Velocity Event, Regulator.

The return value is an array with 2 elements: the `WSModelObject` created, and either `nil` or a string of the warning message that would appear in the UI.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | See supported types in method description. |
| name | `String` | Used as a prefix for the event name (ignored for multiple rainfall events). |
| file | `String`, `Array<String>` | A single file path, or an array of file paths matching the UI behaviour of 'import multiple files into an event'. |
| config | `String` | Path to the config file. |

#### Return Value

`Array<WSModelObject, String>` — `[new_object, warning_string_or_nil]`

---

### 24. import_new_sw_model_object

```ruby
#import_new_sw_model_object(type, format, file, scenario, log) ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports a new SWMM model object as a child of this `WSModelObject`. This must be a suitable type to contain the new model object.

**Permitted types:** Inflow, IWSW Run, IWSW Time Patterns, Selection List, Level, Rainfall Event, IWSW pollutograph, IWSW Climatology, Regulator.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | See supported types in method description. |
| format | `String` | Object format to import: `inp` for swmm5, `xpx` for xpswmm/xpstorm, or `mxd` for infoswmm. |
| file | `String` | Path to the file for import. |
| scenario | `String` | Scenario name, only used when importing an `mxd` file. |
| log | `String` | Path to a log file, ending with a `.txt` extension. |

#### Return Value

`WSModelObject`

#### Example

```ruby
new_swmm = model_group.import_new_sw_model_object('Rainfall Event', 'INP', 'C:/temp/1.inp', '', 'C:/temp/log.txt')
```

---

### 25. import_tvd

```ruby
#import_tvd(file, format, event) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports event data into an existing object.

- If format is `'CSV'`: expects the InfoWorks CSV file format and imports into an existing event, overwriting any existing data.
- If format is `'RED'` and the object is a rainfall event: imports data in event file format into an existing event, overwriting any existing data.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Path to the file to be imported. |
| format | `String` | Either `csv` or `red`. |
| event | `Integer` | Must be present but is ignored. |

#### Return Value

`void`

---

### 26. modified_by

```ruby
#modified_by ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the username which last modified the object. This may differ from the user of the latest commit of a version controlled network.

#### Return Value

`String`

---

### 27. name

```ruby
#name ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the name of this object.

#### Return Value

`String`

---

### 28. name= (Set)

```ruby
#name=(new_name) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the name of this object.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| new_name | `String` | The new name for this object. |

#### Return Value

`void`

---

### 29. new_model_object

```ruby
#new_model_object(type, name) ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Creates a new model object as a child of this object. The type must be valid for this object.

Scripts running in the user interface can only create Selection Lists and Selection List Groups. Full functionality is only available in Exchange.

Runs cannot be created using this method; use [`#new_run`](#31-new_run) or [`#new_risk_analysis_run`](#30-new_risk_analysis_run) instead.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | Type of the new model object. |
| name | `String` | Name of the new model object. |

#### Return Value

`WSModelObject`

#### Exceptions

| Exception | Condition |
|-----------|-----------|
| `unrecognised type` | The type is not a valid scripting type. |
| `sims cannot be created directly` | An attempt was made to create a sim. |
| `invalid child type for this object` | The new type may not be a child of this object type. |
| `name already in use` | The name is in use by another model object (child of this object, or globally for version controlled types with a standalone database licence). |
| `licence and/or permissions do not permit creation of a child of this type for this object` | This type cannot be created for licensing or permissions reasons. |
| `unable to create object` | The call failed for some other reason. |

---

### 30. new_risk_analysis_run

```ruby
#new_risk_analysis_run(name, damage_function, runs, param) ⇒ WSRiskAnalysisRunObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new risk analysis run object.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | Name of the new object. |
| damage_function | `Integer`, `String`, `WSModelObject` | The damage function object. Can be the id, scripting path, or a `WSModelObject` of the correct type. |
| runs | `Integer`, `Array<Integer>`, `String`, `Array<String>`, `WSModelObject`, `Array<WSModelObject>` | The run object or array of run objects. Can be the id, scripting path, or a `WSModelObject` of the correct type. All elements in the array must be the same type. |
| param | `Numeric` | The numerical parameter. |

#### Return Value

`WSRiskAnalysisRunObject`

---

### 31. new_run

```ruby
#new_run(name, network, commit_id, rainfalls_and_flow_surveys, scenarios, options) ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new run. This `WSModelObject` must be a model group.

The method accepts arrays for both `rainfalls_and_flow_surveys` and `scenarios`. Multiple rainfall events, flow surveys, and scenarios yield multiple simulations for the run, analogous to the UI behaviour on the schedule run dialog.

To actually run simulations, use the `#run` method on the individual sim objects below the run, accessible via [`#children`](#06-children).

**`rainfalls_and_flow_surveys` parameter options:**
- `nil` — dry weather flow run.
- A `WSModelObject` that is a rainfall event or flow survey.
- The scripting path of a rainfall event or flow survey as a `String`.
- The `Integer` ID of a rainfall event.
- A negative number equal to `-1` times the ID of a flow survey (e.g. `-7` means Flow Survey with ID 7).
- An `Array` of any of the above (no duplicates; empty array yields a dry weather flow run).

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | The name of the new run. Must be unique within the model group. |
| network | `Integer`, `String`, `WSModelObject` | The network used for the run. Can be the id, scripting path, or a `WSModelObject` of the correct type. |
| commit_id | `Integer`, `nil` | The commit id to use, or `nil` for the latest commit. |
| rainfalls_and_flow_surveys | Multiple | See method description. |
| scenarios | `String`, `Array<String>`, `nil` | `nil` for the base scenario, a scenario name, or an array of scenario names (no duplicates, no non-existent scenarios). |
| options | `Hash` | A hash containing run options. |

#### Return Value

`WSModelObject`

#### Exceptions

| Exception | Condition |
|-----------|-----------|
| `new_run: runs may only be created in model groups` | This object is not a model group. |
| `new_run: name already in use` | The run name is already in use. |

---

### 32. new_synthetic_rainfall

```ruby
#new_synthetic_rainfall(name, type, params) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new synthetic rainfall model object as a child of this `WSModelObject`.

**Permitted generator types:** `UKRain`, `FEHRain`, `ReFHRain`, `GermanRain`, `HKRain`, `HK5thEdRain`, `AUSRain`, `FRQRain`, `FRRain`, `MYRain`, `MY2015Rain`, `USRain`, `ChineseRain`, `ChicagoRain`.

**Note:** The following types cannot be created by scripting as they require external software: `FEH2013`, `FEH2022`, `AUS2016Rain`, `NOAARain`.

**`params` hash keys by generator type (selection):**

| Key | Type | Generator(s) |
|-----|------|--------------|
| `Location` | `Integer` | UKRain, FRRain, MYRain, MY2015Rain |
| `Profile` | `Integer` | UKRain, FEHRain, ReFHRain, GermanRain, FRQRain |
| `WetnessIndex` | `Integer` | UKRain, FEHRain, ReFHRain, GermanRain, HKRain, HK5thEdRain, AUSRain, FRQRain, FRRain, MYRain, MY2015Rain, USRain |
| `ReturnPeriod` | `Float` | FEHRain, ReFHRain, GermanRain, HKRain, HK5thEdRain, FRRain, MYRain, MY2015Rain, ChineseRain, ChicagoRain |
| `Duration` | `Float` | FEHRain, ReFHRain, GermanRain, HKRain, HK5thEdRain, AUSRain, FRQRain, FRRain, MYRain, MY2015Rain, ChineseRain, ChicagoRain |
| `Antecedentdepth` | `Float` | FEHRain, ReFHRain, GermanRain, HKRain, HK5thEdRain, AUSRain, FRRain, MYRain, MY2015Rain, USRain |
| `UCWI` | `Float` | FEHRain, ReFHRain, GermanRain, HKRain, HK5thEdRain, AUSRain, FRQRain, FRRain, MYRain, MY2015Rain, USRain |
| `API30` | `Float` | Most generator types |
| `SMS` | `Float` | Most generator types |
| `SMD` | `Float` | Most generator types |
| `Cini` | `Float` | Most generator types |
| `BF0` | `Float` | Most generator types |
| `Evaporation` | `Float` | Most generator types |
| `5yr1hr` | `Float` | UKRain |
| `RainfallRatio` | `Float` | UKRain |
| `CatchmentArea` | `Float` | UKRain, MYRain, MY2015Rain |
| `Zone` | `Float` | AUSRain |
| `Latitude` | `Float` | AUSRain |
| `Longitude` | `Float` | AUSRain |
| `ARI` | `Float` | AUSRain |
| `Multiplying Factor` | `Float` | AUSRain |
| `PeakDuration` | `Float` | FRRain, FRQRain |
| `PeakPosition` | `Float` | FRRain, FRQRain |
| `Intensity` | `Float` | FRQRain |
| `PeakRainfall` | `Float` | FRQRain |
| `StormRainfall` | `Float` | FRQRain |
| `Timestep` | `Float` | FRQRain, ChineseRain, ChicagoRain |
| `SCSInPat` | `Integer` | USRain |
| `SCSDur` | `Integer` | USRain |
| `SCS24Rain` | `Float` | USRain |
| `SCSTS` | `Float` | USRain |
| `CalculationOfA` | `Integer` | ChineseRain |
| `PeakTimeRatio` | `Float` | ChineseRain, ChicagoRain |
| `BigA` | `Float` | ChineseRain |
| `A`, `B`, `C` | `Float` | HKRain, HK5thEdRain, FRRain, MYRain, MY2015Rain, ChineseRain, ChicagoRain |
| `D` | `Float` | MYRain, MY2015Rain |
| `2P24hr` | `Float` | MYRain |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | Name of the new model object. |
| type | `String` | Generator type of the new rainfall model object. |
| params | `Hash` | A hash containing rainfall parameters (see keys above). |

#### Return Value

`void`

#### Exceptions

| Exception | Condition |
|-----------|-----------|
| `synthetic rainfall events may only be created in model groups` | This object is not a model group. |
| `name already in use` | The rainfall event name is already in use. |
| `rainfall type XXXX cannot be created by scripting` | Type requires external software (FEH2013, FEH2022, AUS2016Rain, NOAARain). |
| `rainfall type XXXX not found` | Input type is not valid. |
| `parameter 3 is not a Hash` | `params` is not a valid hash. |
| `unable to load DLL` | Problem loading rainfall generator software. |

---

### 33. open

```ruby
#open ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Only available for model objects of a network type or sim.

Opens the network and returns a `WSOpenNetwork` object. When called on a sim, the network and results are opened. An exception is thrown if the simulation did not succeed or the results are inaccessible.

**When opening simulation results:**
- The network is opened as read only.
- The current scenario is set to the scenario used for the simulation and cannot be changed.
- The network opens at the first timestep (timestep 0), unless only maximum results are present, in which case it opens at the maximum results timestep.

#### Return Value

`WSModelObject` (specifically a `WSOpenNetwork`)

---

### 34. parent_id

```ruby
#parent_id ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the ID of this object's parent. Returns `0` if the object is in the root of the database.

#### Return Value

`Integer`

---

### 35. parent_type

```ruby
#parent_type ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the type of this object's parent. Returns `'Master Database'` if the object is in the root of the database.

#### Return Value

`String`

---

### 36. path

```ruby
#path ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the scripting path of this object.

#### Return Value

`String`

---

### 37. type

```ruby
#type ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the type of this model object.

#### Return Value

`String`

---

### 38. update_to_latest

```ruby
#update_to_latest ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Updates a run model object, equivalent to the 'update to latest version of network' button in the run view of the user interface.

**Conditions that must be met:**
- The `'Working'` field must be set to `true`.
- There must be no uncommitted changes for the network used in the run.
- All scenarios included in the scenarios list must be present and validated.

#### Return Value

`void`
