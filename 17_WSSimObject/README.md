# WSSimObject

**Inheritance:** `WSModelObject` > `WSBaseNetworkObject` > `WSNumbatNetworkObject` > `WSSimObject`

A read-only network with simulation results, representing an ICM Sim object, an ICM Risk Analysis Results object, or an ICM Risk Analysis Sim object. The Risk Analysis Results objects contain the results for a number of return periods and summary results. The Risk Analysis Sim objects contain only summary results.

The different return periods for the Risk Analysis Results objects correspond to the timesteps for regular simulations. The names of the methods reflect the usage for regular simulations, i.e. to list the return periods for a risk analysis results object, you should use the `list_timesteps` method.

## Availability

| Context | Available |
|---------|-----------|
| ![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) | Yes |
| ![UI](https://img.shields.io/badge/UI-green) | Partial (see individual methods) |

---

## Methods Summary

| # | Method | Returns | Availability |
|---|--------|---------|--------------|
| 01 | [list_max_results_attributes](#01-list_max_results_attributes) | `Array<Array>` | EXCHANGE |
| 02 | [list_results_attributes](#02-list_results_attributes) | `Array<Array>` | EXCHANGE |
| 03 | [list_results_gis_export_tables](#03-list_results_gis_export_tables) | `Array` | EXCHANGE |
| 04 | [list_timesteps](#04-list_timesteps) | `Array` | EXCHANGE |
| 05 | [max_flood_contours_export](#05-max_flood_contours_export) | `void` | EXCHANGE |
| 06 | [max_results_binary_export](#06-max_results_binary_export) | `void` | EXCHANGE |
| 07 | [max_results_csv_export](#07-max_results_csv_export) | `void` | EXCHANGE |
| 08 | [results_binary_export](#08-results_binary_export) | `void` | EXCHANGE |
| 09 | [results_csv_export](#09-results_csv_export) | `void` | EXCHANGE |
| 10 | [results_csv_export_ex](#10-results_csv_export_ex) | `void` | EXCHANGE |
| 11 | [results_gis_export](#11-results_gis_export) | `void` | EXCHANGE |
| 12 | [results_path](#12-results_path) | `String` | EXCHANGE |
| 13 | [run](#13-run) | `void` | EXCHANGE |
| 14 | [run_ex](#14-run_ex) | `void` | EXCHANGE |
| 15 | [status](#15-status) | `String` | EXCHANGE, UI |
| 16 | [success_substatus](#16-success_substatus) | `String` | EXCHANGE |
| 17 | [timestep_count](#17-timestep_count) | `Integer` | EXCHANGE |

---

## Method Details

### 01. list_max_results_attributes

```ruby
#list_max_results_attributes ⇒ Array<Array>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Results, Risk Analysis Sim

Returns attributes that can be exported using the `#max_results_binary_export` and `#max_results_csv_export` methods. Returns arrays corresponding to the tabs of the result export dialog in the UI.

#### Returns

`Array<Array>` — Nested arrays of export attribute groups and their field names.

#### Example

```ruby
[
  ['Scalar', ['totfl', 'totout', 'totr', ...]],
  ['Node', ['flooddepth', 'floodvolume', 'flvol', ...]]
]
```

---

### 02. list_results_attributes

```ruby
#list_results_attributes ⇒ Array<Array>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Results

Returns attributes that can be exported using the `#results_binary_export` and `#results_csv_export` methods. Returns arrays corresponding to the tabs of the result export dialog in the UI.

#### Returns

`Array<Array>` — Nested arrays of export attribute groups and their field names.

#### Example

```ruby
[
  ['Node', ['flooddepth', 'floodvolume', 'flvol', ...]],
  ['Link', ['ds_depth', 'ds_flow', 'ds_froude', ...]]
]
```

---

### 03. list_results_gis_export_tables

```ruby
#list_results_gis_export_tables ⇒ Array
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Results, Risk Analysis Sim

Returns an array of the tables that may be exported to GIS using the `#results_gis_export` method.

> **Notes:**
> - The results for 2D elements is `_2Delements`.
> - All links are combined into one GIS layer called `_links`.
> - This method previously included capitalisation. The lower case method name is now recommended.

#### Returns

`Array` — Array of table name strings available for GIS export.

---

### 04. list_timesteps

```ruby
#list_timesteps ⇒ Array
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Results, Risk Analysis Sim

For a normal simulation, returns an array of the results timesteps. For a risk analysis results object, returns an array of the return periods for the object.

#### Returns

`Array` — Array of timesteps (for simulations) or return periods (for risk analysis results objects).

---

### 05. max_flood_contours_export

```ruby
#max_flood_contours_export(format, ground_model, theme, filename) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim

Exports the flood contours to files (GIS or ASCII). The ASCII format is the same as produced via the user interface.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `format` | `String` | The format, one of `mif`, `tab`, `shp`, or `ascii`. Geodatabases are not supported. |
| `ground_model` | `Integer`, `String`, `WSModelObject` | The ground model. Must be a gridded ground model for ASCII export. Can be the ID, scripting path, or a `WSModelObject` of the correct type. A negative ID represents a TIN ground model (e.g. `-6` is the TIN with ID 6; `9` is a gridded ground model with ID 9). |
| `theme` | `Integer`, `String`, `WSModelObject` | The theme to use for contours. Can be the ID, scripting path, or a `WSModelObject` of the correct type. |
| `filename` | `String` | The file to export to. |

#### Returns

`void`

---

### 06. max_results_binary_export

```ruby
#max_results_binary_export(selection, attributes, file) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Results

Exports the maximum results (and other summary results) for the simulation in a binary file format. The format is documented separately.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `selection` | `WSModelObject`, `String`, `Integer`, `nil` | A selection list object as a `WSModelObject`, scripting path, or model ID. If `nil` the whole network is exported. |
| `attributes` | `Array<String>`, `nil` | Attributes to export, e.g. from `#list_results_attributes`. If `nil` all attributes are exported. |
| `file` | `String` | Filepath to export to. |

#### Returns

`void`

---

### 07. max_results_csv_export

```ruby
#max_results_csv_export(selection, attributes, folder) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim

Exports the maximum results (and other summary results) for the simulation to `.csv` files.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `selection` | `WSModelObject`, `String`, `Integer`, `nil` | A selection list object as a `WSModelObject`, scripting path, or model ID. If `nil` the whole network is exported. |
| `attributes` | `Array<String>`, `nil` | Attributes to export, e.g. from `#list_results_attributes`. If `nil` all attributes are exported. |
| `folder` | `String` | Folder to export the `.csv` files to. |

#### Returns

`void`

---

### 08. results_binary_export

```ruby
#results_binary_export(selection, attributes, file) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Results

Exports the results at each timestep of the simulation in a binary file format. The format is documented separately.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `selection` | `WSModelObject`, `String`, `Integer`, `nil` | A selection list object as a `WSModelObject`, scripting path, or model ID. If `nil` the whole network is exported. |
| `attributes` | `Array<String>`, `nil` | Attributes to export, e.g. from `#list_results_attributes`. If `nil` all attributes are exported. |
| `file` | `String` | Filepath to export to. |

#### Returns

`void`

---

### 09. results_csv_export

```ruby
#results_csv_export(selection, folder) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim

Exports the simulation results in CSV format, corresponding to the CSV results export in the user interface.

> **Note:** If the results multiplier is set to 0, the CSV will be empty.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `selection` | `WSModelObject`, `String`, `Integer`, `nil` | A selection list object as a `WSModelObject`, scripting path, or model ID. If `nil` the whole network is exported. |
| `folder` | `String` | Folder to export the `.csv` files to. |

#### Returns

`void`

---

### 10. results_csv_export_ex

```ruby
#results_csv_export_ex(selection, attributes, folder) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim

Similar to `#results_csv_export`, with an additional `attributes` parameter.

> **Note:** If the results multiplier is set to 0, the CSV will be empty.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `selection` | `WSModelObject`, `String`, `Integer`, `nil` | A selection list object as a `WSModelObject`, scripting path, or model ID. If `nil` the whole network is exported. |
| `attributes` | `Array<String>`, `nil` | Attributes to export, e.g. from `#list_results_attributes`. If `nil` all attributes are exported. |
| `folder` | `String` | Folder to export the `.csv` files to. |

#### Returns

`void`

---

### 11. results_gis_export

```ruby
#results_gis_export(format, timesteps, options, folder) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Results, Risk Analysis Sim

Exports simulation results to a GIS data format, similar to the equivalent options in the user interface.

> **Note:** This method previously included capitalisation. The lower case method name is now recommended.

#### Timesteps Parameter Options

| Value | Description |
|-------|-------------|
| `nil` | Equivalent to the `None` option in the UI. Only makes sense if the options hash exports maximum results. |
| `'All'` | All timesteps. Does not include maximum results unless included in the options hash. |
| `'Max'` | Maximum results only. Alternative to including maximum results in the options hash. |
| `Integer` | A single timestep index, where `0` is the first timestep. |
| `Array<Integer>` | Array of timestep indices. Must all be valid and cannot contain duplicates. |

#### Options Hash Keys

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `2DZoneSQL` | `Array<Array>` | | Array of arrays where each inner array contains: `[0]` field name (String), `[1]` SQL expression (String), `[2]` optional decimal places 0-9 (Integer, default 2). Default is not to export any extra fields for 2D elements. |
| `AlternativeNaming` | `Boolean` | | If set, subfolders use simpler names formatted as `<model_object_id>_<timestep>` (timesteps numbered from zero) and `<model_object_id>_Max` for maxima. Useful for programmatic processing rather than user-facing GIS. |
| `ExportMaxima` | `Boolean` | `false` | If `true`, maximum results are exported. |
| `FeatureDataset` | `String` | `''` | For GeoDatabases, the name of the feature dataset. |
| `Tables` | `Array<String>` | | Array of table names from `#list_results_gis_export_tables`. Must all be valid and cannot contain duplicates. |
| `Threshold` | `Float` | | Depth threshold below which a 2D element is not exported. Equivalent to checking the threshold checkbox in the UI. Default exports all elements. |
| `UseArcGISCompatibility` | `Boolean` | `false` | Equivalent to selecting the ArcGIS compatibility checkbox in the UI. |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `format` | `String` | Export format, one of `shp`, `tab`, `mif`, or `gdb`. |
| `timesteps` | `String`, `Integer`, `Array<Integer>`, `nil` | See timesteps options above. |
| `options` | `Hash`, `nil` | Hash of options (see above) or `nil` to use defaults. |
| `folder` | `String` | The base folder for exported files, or path to the `.gdb` if format is `gdb`. |

#### Returns

`void`

---

### 12. results_path

```ruby
#results_path ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the full file path for the simulation results.

#### Returns

`String` — The full path to the results.

---

### 13. run

```ruby
#run ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim

Runs (or re-runs) the simulation. This is a blocking operation, i.e. script execution will halt while the simulation finishes. The simulation will run on the current machine.

#### Returns

`void`

---

### 14. run_ex

```ruby
#run_ex(*args) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Sim

Similar to `#run`, and also a blocking operation. Supports two calling signatures.

#### Single Parameter (Options Hash)

```ruby
#run_ex(options) ⇒ void
```

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `Server` | `String` | `*` | Server name, or `.` for local machine, or `*` for any available server. |
| `Threads` | `Integer` | `0` | Number of threads to use. `0` means as many as possible. |
| `SU` | `Boolean` | `false` | Must be set to `true` if using InfoWorks One. |
| `ResultsOnServer` | `Boolean` | `true` | Whether to store results on the server. `false` stores results locally. |
| `DownloadSelection` | `String` | `ALL_RESULTS` | One of `NO_RESULTS`, `SUMMARY_RESULTS`, or `ALL_RESULTS`. Only applies to cloud databases. |

##### Parameters

| Name | Type | Description |
|------|------|-------------|
| `options` | `Hash` | Options hash. See keys above. |

#### Two Parameters

```ruby
#run_ex(server, number_of_threads) ⇒ void
```

##### Parameters

| Name | Type | Description |
|------|------|-------------|
| `server` | `String` | Server name, or `.` for local machine, or `*` for any available server. |
| `number_of_threads` | `Integer` | Number of threads to use. `0` means as many as possible. |

#### Returns

`void`

---

### 15. status

```ruby
#status ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

**Supported Types:** ICM Sim

Returns the status of a simulation.

> **Note:** To monitor for completion of a simulation, the recommended approach is to use the `#wait_for_jobs` method.

#### Returns

`String`, `nil` — Simulation status, one of `none`, `active`, `success`, or `fail`.

---

### 16. success_substatus

```ruby
#success_substatus ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim

Returns the simulation substatus, if the simulation was successful.

#### Returns

`String`, `nil` — Simulation substatus, one of `incomplete`, `warnings`, or `ok`. Returns `nil` if the simulation was not successful.

---

### 17. timestep_count

```ruby
#timestep_count ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

**Supported Types:** ICM Sim, Risk Analysis Results, Risk Analysis Sim

Returns the number of results timesteps in the simulation.

#### Returns

`Integer` — The number of results timesteps.

---

*Documentation generated from the official Autodesk InfoWorks ICM 2025 help pages.*
