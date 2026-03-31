# WSOpenNetwork

An open network. An open network allows access to the network contents, similar to opening the network as a grid or GeoPlan in the UI.

> **Note:** a network in this context is not the same as a 'network' in the user interface.

## Availability

| Context | Available |
|---------|-----------|
| EXCHANGE | Yes |
| UI | Partial (see individual methods) |

---

## Methods Summary

| # | Method | Return Type | Availability |
|---|--------|-------------|--------------|
| 01 | [add_scenario](#01-add_scenario) | `void` | EXCHANGE, UI |
| 02 | [cancel_mesh_job](#02-cancel_mesh_job) | `void` | EXCHANGE |
| 03 | [clear_selection](#03-clear_selection) | `void` | EXCHANGE, UI |
| 04 | [csv_export](#04-csv_export) | `void` | EXCHANGE, UI |
| 05 | [csv_import](#05-csv_import) | `void` | EXCHANGE, UI |
| 06 | [current_scenario](#06-current_scenario) | `String` | EXCHANGE, UI |
| 07 | [current_scenario=](#07-current_scenario-set) | `void` | EXCHANGE, UI |
| 08 | [current_timestep](#08-current_timestep) | `Integer` | EXCHANGE, UI |
| 09 | [current_timestep=](#09-current_timestep-set) | `void` | EXCHANGE |
| 10 | [current_timestep_time](#10-current_timestep_time) | `DateTime` | EXCHANGE, UI |
| 11 | [delete_scenario](#11-delete_scenario) | `void` | EXCHANGE, UI |
| 12 | [delete_selection](#12-delete_selection) | `void` | EXCHANGE, UI |
| 13 | [download_mesh_job_log](#13-download_mesh_job_log) | `void` | EXCHANGE |
| 14 | [each](#14-each) | `WSRowObject` | EXCHANGE, UI |
| 15 | [each_selected](#15-each_selected) | `WSRowObject` | EXCHANGE, UI |
| 16 | [export_ids](#16-export_ids) | `void` | EXCHANGE, UI |
| 17 | [field_names](#17-field_names) | `Array<String>` | EXCHANGE, UI |
| 18 | [gauge_timestep_count](#18-gauge_timestep_count) | `Integer` | EXCHANGE, UI |
| 19 | [gauge_timestep_time](#19-gauge_timestep_time) | `DateTime` | EXCHANGE, UI |
| 20 | [gis_export](#20-gis_export) | `void` | EXCHANGE, UI |
| 21 | [infodrainage_import](#21-infodrainage_import) | `void` | EXCHANGE |
| 22 | [list_gauge_timesteps](#22-list_gauge_timesteps) | `Array<DateTime>` | EXCHANGE, UI |
| 23 | [list_gis_export_tables](#23-list_gis_export_tables) | `Array<String>` | EXCHANGE |
| 24 | [list_timesteps](#24-list_timesteps) | `Array<DateTime>` | EXCHANGE, UI |
| 25 | [load_mesh_job](#25-load_mesh_job) | `void` | EXCHANGE |
| 26 | [load_selection](#26-load_selection) | `void` | EXCHANGE, UI |
| 27 | [mesh](#27-mesh) | `Hash<String, Boolean>` | EXCHANGE |
| 28 | [mesh_async](#28-mesh_async) | `Array<Integer>` | EXCHANGE |
| 29 | [mesh_job_status](#29-mesh_job_status) | `String` | EXCHANGE |
| 30 | [model_object](#30-model_object) | `WSModelObject` | EXCHANGE, UI |
| 31 | [mscc_export_cctv_surveys](#31-mscc_export_cctv_surveys) | `Boolean` | EXCHANGE, UI |
| 32 | [mscc_export_manhole_surveys](#32-mscc_export_manhole_surveys) | `Boolean` | EXCHANGE, UI |
| 33 | [mscc_import_cctv_surveys](#33-mscc_import_cctv_surveys) | | EXCHANGE, UI |
| 34 | [mscc_import_manhole_surveys](#34-mscc_import_manhole_surveys) | | EXCHANGE, UI |
| 35 | [network_model_object](#35-network_model_object) | `WSModelObject` | EXCHANGE, UI |
| 36 | [new_row_object](#36-new_row_object) | `WSRowObject` | EXCHANGE, UI |
| 37 | [objects_in_polygon](#37-objects_in_polygon) | `Array<WSRowObject>` | EXCHANGE, UI |
| 38 | [odec_export_ex](#38-odec_export_ex) | `void` | EXCHANGE, UI |
| 39 | [odic_import_ex](#39-odic_import_ex) | `Array<WSRowObject>` | EXCHANGE, UI |
| 40 | [ribx_export_surveys](#40-ribx_export_surveys) | `Boolean` | EXCHANGE, UI |
| 41 | [ribx_import_surveys](#41-ribx_import_surveys) | | EXCHANGE, UI |
| 42 | [row_object](#42-row_object) | `WSRowObject?` | EXCHANGE, UI |
| 43 | [row_object_collection](#43-row_object_collection) | `WSRowObjectCollection` | EXCHANGE, UI |
| 44 | [row_object_collection_selection](#44-row_object_collection_selection) | `WSRowObjectCollection` | EXCHANGE, UI |
| 45 | [row_objects](#45-row_objects) | `Array<WSRowObject>` | EXCHANGE, UI |
| 46 | [row_objects_from_asset_id](#46-row_objects_from_asset_id) | `Array<WSRowObject>` | EXCHANGE, UI |
| 47 | [row_objects_selection](#47-row_objects_selection) | `Array<WSRowObject>` | EXCHANGE, UI |
| 48 | [run_sql](#48-run_sql) | `void` | EXCHANGE, UI |
| 49 | [run_inference](#49-run_inference) | `void` | EXCHANGE, UI |
| 50 | [run_stored_query_object](#50-run_stored_query_object) | `void` | EXCHANGE, UI |
| 51 | [save_selection](#51-save_selection) | `void` | EXCHANGE, UI |
| 52 | [scenarios](#52-scenarios) | `String` | EXCHANGE, UI |
| 53 | [search_at_point](#53-search_at_point) | `Array<WSRowObject>` | EXCHANGE, UI |
| 54 | [selection_size](#54-selection_size) | `Integer` | EXCHANGE, UI |
| 55 | [set_projection_string](#55-set_projection_string) | `void` | EXCHANGE |
| 56 | [snapshot_export](#56-snapshot_export) | `void` | EXCHANGE, UI |
| 57 | [snapshot_export_ex](#57-snapshot_export_ex) | `void` | EXCHANGE, UI |
| 58 | [snapshot_import_ex](#58-snapshot_import_ex) | `void` | EXCHANGE, UI |
| 59 | [snapshot_scan](#59-snapshot_scan) | `Hash<String, Any>` | EXCHANGE, UI |
| 60 | [table](#60-table) | `WSTableInfo` | EXCHANGE, UI |
| 61 | [table_names](#61-table_names) | `Array<String>` | EXCHANGE, UI |
| 62 | [tables](#62-tables) | `Array<WSTableInfo>` | EXCHANGE, UI |
| 63 | [timestep_count](#63-timestep_count) | `Integer` | EXCHANGE, UI |
| 64 | [timestep_time](#64-timestep_time) | `DateTime` | EXCHANGE, UI |
| 65 | [transaction_begin](#65-transaction_begin) | `void` | EXCHANGE, UI |
| 66 | [transaction_commit](#66-transaction_commit) | `void` | EXCHANGE, UI |
| 67 | [transaction_rollback](#67-transaction_rollback) | `void` | EXCHANGE, UI |
| 68 | [update_cctv_scores](#68-update_cctv_scores) | `void` | EXCHANGE, UI |
| 69 | [xprafts_import](#69-xprafts_import) | `void` | EXCHANGE |

---

## Method Details

### 01. add_scenario

```ruby
#add_scenario(name, based_on, notes) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Adds a new scenario to the network.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | Name of the new scenario. |
| based_on | `String`, `nil` | The name of the scenario to use as a base, if any. |
| notes | `String` | Notes or description for this scenario. |

#### Return Value

`void`

#### Example

```ruby
network.add_scenario('MyNewScenario', nil, 'Some notes...')
```

---

### 02. cancel_mesh_job

```ruby
#cancel_mesh_job(job_id) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Cancels a mesh job.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| job_id | `Integer` | The job id from the [`#mesh_async`](#28-mesh_async) method. |

#### Return Value

`void`

---

### 03. clear_selection

```ruby
#clear_selection ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Clears the current selection. Any `WSRowObject` objects that are currently selected will be deselected.

#### Return Value

`void`

---

### 04. csv_export

```ruby
#csv_export(filename, options) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports data to CSV. See `WSBaseNetworkObject.csv_export` for full parameter details.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| filename | `String` | Path to the output CSV file. |
| options | `Hash` | Export options. |

#### Return Value

`void`

---

### 05. csv_import

```ruby
#csv_import(filename, options) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Imports data from CSV. See `WSBaseNetworkObject.csv_import` for full parameter details.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| filename | `String` | Path to the CSV file to import. |
| options | `Hash` | Import options. |

#### Return Value

`void`

---

### 06. current_scenario

```ruby
#current_scenario ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the current scenario of the network. If the current scenario is the base scenario, returns the string `Base` (in English).

#### Return Value

`String`

---

### 07. current_scenario= (Set)

```ruby
#current_scenario=(name) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Sets the current scenario of the network. The scenario must exist.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String`, `nil` | The name of the scenario. If `nil`, the scenario is set to the base scenario. |

#### Return Value

`void`

---

### 08. current_timestep

```ruby
#current_timestep ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the index of the current timestep. The `WSOpenNetwork` has a current timestep corresponding to the timestep results when opened in the UI. It determines the timestep for which the `result` method of `WSRowObject` returns its value.

The first timestep is index `0`, the final timestep is `timestep_count - 1`. A value of `-1` represents the 'maximum' timestep. The initial value when a sim is opened in ICM Exchange is `0` if there are time varying results, otherwise `-1`.

#### Return Value

`Integer`

---

### 09. current_timestep= (Set)

```ruby
#current_timestep=(index) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Sets the current network timestep.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| index | `Integer` | The timestep index. `0` sets to the first timestep, `-1` returns the maximum timestep. |

#### Return Value

`void`

---

### 10. current_timestep_time

```ruby
#current_timestep_time ⇒ DateTime
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the actual time of the current timestep.

#### Return Value

`DateTime`

---

### 11. delete_scenario

```ruby
#delete_scenario(name) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Deletes a named scenario from the network. If the deleted scenario is the current scenario, the network will switch to the base scenario.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | The name of the scenario to delete. |

#### Return Value

`void`

#### Example

```ruby
puts network.current_scenario
# => 'ScenarioBadger'
network.delete_scenario('ScenarioBadger')
puts network.current_scenario
# => 'Base'
```

---

### 12. delete_selection

```ruby
#delete_selection ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Deletes the currently selected objects from the network, in the current scenario.

#### Return Value

`void`

---

### 13. download_mesh_job_log

```ruby
#download_mesh_job_log(job_id, path) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Copies the log output from a [`#mesh_async`](#28-mesh_async) job to a new file.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| job_id | `Integer` | The job id from the [`#mesh_async`](#28-mesh_async) method. |
| path | `String` | Path to the new file, including extension (`.txt`). |

#### Return Value

`void`

---

### 14. each

```ruby
#each { |ro| ... } ⇒ WSRowObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Iterates through each object in the network.

#### Return Value

`WSRowObject`

---

### 15. each_selected

```ruby
#each_selected { |ro| ... } ⇒ WSRowObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Iterates through each selected object in the network.

#### Return Value

`WSRowObject`

---

### 16. export_ids

```ruby
#export_ids(filename, options) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports the IDs of `WSRowObject` objects to a file, grouped by table.

> **Note:** This method previously included capitalization. The new lower case method name is recommended.

**`options` hash keys:**

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `Selection Only` | `Boolean` | `false` | If `true`, only currently selected `WSRowObject` objects are exported. |
| `UTF8` | `Boolean` | `false` | If `true`, saves the file with UTF8 encoding, otherwise uses current locale. |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| filename | `String` | Path to the file, including extension (`.txt`). |
| options | `Hash`, `nil` | See description. |

#### Return Value

`void`

---

### 17. field_names

```ruby
#field_names(table) ⇒ Array<String>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the field names for a given table.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| table | `String` | The name of the table (type) of `WSRowObject`. |

#### Return Value

`Array<String>`

#### Example

```ruby
network.field_names('wn_node').each { |s| puts s }
```

---

### 18. gauge_timestep_count

```ruby
#gauge_timestep_count ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the number of gauge timesteps. Returns `0` if there are no gauge timesteps (e.g. no objects are gauged, or the gauge timestep multiplier is 0).

#### Return Value

`Integer`

---

### 19. gauge_timestep_time

```ruby
#gauge_timestep_time(index) ⇒ DateTime
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the actual time of the gauge timestep at the given index.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| index | `Integer` | The gauge timestep index. |

#### Return Value

`DateTime`

#### Example

```ruby
puts network.gauge_timestep_time(0)
```

---

### 20. gis_export

```ruby
#gis_export(format, options, location) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports the network data to GIS format. See [`WSNumbatNetworkObject.gis_export`](../11_WSNumbatNetworkObject/README.md#07-gis_export) for full options details.

> **Note:** This method previously included capitalization. The new lower case method name is recommended.

#### Return Value

`void`

---

### 21. infodrainage_import

```ruby
#infodrainage_import(filename, log) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Imports an InfoDrainage model into the network.

> **Note:** This method previously included capitalization. The new lower case method name is recommended.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| filename | `String` | Filepath to the InfoDrainage file including extension `.iddx`. |
| log | `String` | Filepath to save the import log including extension `.txt`, which will be in rich text format. |

#### Return Value

`void`

---

### 22. list_gauge_timesteps

```ruby
#list_gauge_timesteps ⇒ Array<DateTime>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the times of all gauge timesteps, in order.

#### Return Value

`Array<DateTime>`

---

### 23. list_gis_export_tables

```ruby
#list_gis_export_tables ⇒ Array<String>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the tables that can be exported using the [`#gis_export`](#20-gis_export) method.

> **Note:** This method previously included capitalization. The new lower case method name is recommended.

#### Return Value

`Array<String>`

---

### 24. list_timesteps

```ruby
#list_timesteps ⇒ Array<DateTime>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the times of all timesteps, in order.

#### Return Value

`Array<DateTime>`

---

### 25. load_mesh_job

```ruby
#load_mesh_job(job_id) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Loads the completed mesh from a [`#mesh_async`](#28-mesh_async) job into the network.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| job_id | `Integer` | The job id from the [`#mesh_async`](#28-mesh_async) method. |

#### Return Value

`void`

---

### 26. load_selection

```ruby
#load_selection(selection_list) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Selects objects in the network from the selection list object.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| selection_list | `Integer`, `String`, `WSModelObject` | The selection list. Can be the id, scripting path, or a `WSModelObject` of the correct type. |

#### Return Value

`void`

---

### 27. mesh

```ruby
#mesh(options) ⇒ Hash<String, Boolean>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Meshes one or more 2D zones synchronously (blocks the script thread). To mesh asynchronously, see [`#mesh_async`](#28-mesh_async).

**`options` hash keys:**

| Key | Type | Required | Description |
|-----|------|----------|-------------|
| `GroundModel` | `Integer`, `String`, `WSModelObject` | Yes | The ground model. Negative ID represents a TIN ground model (e.g. `-7` = TIN with ID 7). Positive ID represents a gridded ground model. |
| `VoidsFile` | `String` | No | Path to a GIS file containing the voids. |
| `VoidsFeatureClass` | `String` | No | For GeoDatabases, the feature class within the GeoDatabase for the voids. |
| `VoidsCategory` | `String` | No | The category of polygon within the network used for voids. |
| `BreakLinesFile` | `String` | No | Path to a GIS file containing the break lines. |
| `BreakLinesFeatureClass` | `String` | No | For GeoDatabases, the feature class for the break lines. |
| `BreakLinesCategory` | `String` | No | The category of polyline within the network used for break lines. |
| `WallsFile` | `String` | No | Path to a GIS file containing the walls. |
| `WallsFeatureClass` | `String` | No | For GeoDatabases, the feature class for the walls. |
| `WallsCategory` | `String` | No | The category of polyline within the network used for walls. |
| `2DZones` | `String`, `Array<String>` | Yes* | Name(s) of 2D zones to mesh. If absent or `nil` (and `2DZonesSelectionList` also absent), all zones are meshed. |
| `2DZonesSelectionList` | `Integer`, `String`, `WSModelObject` | No | A selection list of 2D zones to mesh. |
| `LowerElementGroundLevels` | `Boolean` | No | If `true`, lowers 2D mesh elements with ground levels higher than adjacent bank levels. |
| `RunOn` | `String` | No | The computer to run on: `.` for this computer, `*` for any computer. |
| `LogFile` | `String` | No | Path to log file with `.HTML` extension. Only usable when meshing a single 2D zone. |
| `LogPath` | `String` | No | Path to a folder for log files. Usable for multiple zones. Files are named by zone name with `.HTML` extension. |

**Constraints:**
- For voids, break lines, and walls: only one of `File`, `FeatureClass`, or `Category` may be set per pair.
- If any `VoidsFile`, `WallsFile`, or `BreakLinesFile` are set, `WSApplication.map_component=` must be set and the user must have the GIS component selected.
- `FeatureClass` keys can only be set if the corresponding `File` key is set and the map control is not MapXTreme.
- Only one of `2DZones` and `2DZonesSelectionList` may be present.
- Only one of `LogFile` and `LogPath` may be present.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| options | `Hash` | Options hash. See description. |

#### Return Value

`Hash<String, Boolean>` — A hash with 2D zone names as keys and a boolean indicating success or failure for each.

---

### 28. mesh_async

```ruby
#mesh_async(options) ⇒ Array<Integer>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Meshes one or more 2D zones asynchronously (does not block the script thread). Similar to [`#mesh`](#27-mesh), except each 2D zone gets a unique job ID returned in the array.

Job IDs can be used with [`#load_mesh_job`](#25-load_mesh_job), [`#cancel_mesh_job`](#02-cancel_mesh_job), [`#download_mesh_job_log`](#13-download_mesh_job_log), [`#mesh_job_status`](#29-mesh_job_status), and `WSApplication.wait_for_jobs`.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| options | `Hash` | Identical to [`#mesh`](#27-mesh) options, except `LogFile` and `LogPath` keys are not available. |

#### Return Value

`Array<Integer>` — An array of job ids.

---

### 29. mesh_job_status

```ruby
#mesh_job_status(job_id) ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the current status of a mesh job identified by a job ID from [`#mesh_async`](#28-mesh_async).

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| job_id | `Integer` | The job id from the [`#mesh_async`](#28-mesh_async) method. |

#### Return Value

`String`

---

### 30. model_object

```ruby
#model_object ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns a `WSModelObject` (or derived class) associated with this network.

If the network was loaded from a sim, the model object of that sim is returned. This differs from [`#network_model_object`](#35-network_model_object), which always returns the network.

#### Return Value

`WSModelObject`

---

### 31. mscc_export_cctv_surveys

```ruby
#mscc_export_cctv_surveys(export_file, export_images, selection_only, log_file) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports CCTV survey data from a Collection Network to the MSCC4 XML format.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| export_file | `String` | Path to the output XML file. |
| export_images | `Boolean` | Whether to export defect images. |
| selection_only | `Boolean` | If `true`, limits the export to selected objects. |
| log_file | `String` | Path to a text file for errors. |

#### Return Value

`Boolean`

---

### 32. mscc_export_manhole_surveys

```ruby
#mscc_export_manhole_surveys(export_file, export_images, selection_only, log_file) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports manhole survey data from a Collection Network to the MSCC5 XML format.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| export_file | `String` | Path to the output XML file. |
| export_images | `Boolean` | Whether to export defect images. |
| selection_only | `Boolean` | If `true`, limits the export to selected objects. |
| log_file | `String` | Path to a text file for errors. |

#### Return Value

`Boolean`

---

### 33. mscc_import_cctv_surveys

```ruby
#mscc_import_cctv_surveys(import_file, import_flag, import_images, id_gen, overwrite, log_file)
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Imports CCTV survey data into a Collection Network from the MSCC4 XML format.

**`id_gen` values:**

| Value | Description |
|-------|-------------|
| `1` | StartNodeRef, Direction, Date and Time |
| `2` | StartNodeRef, Direction and an index for uniqueness |
| `3` | US node ID, Direction, Date and Time |
| `4` | US node ID, Direction and an index for uniqueness |
| `5` | ClientDefined1 |
| `6` | ClientDefined2 |
| `7` | ClientDefined3 |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| import_file | `String` | Path to the XML file. |
| import_flag | `String` | The data flag for imported fields. |
| import_images | `Boolean` | Whether to import defect images. |
| id_gen | `Integer` | ID generation method. See values above. |
| overwrite | `Boolean` | If `false`, prevents overwriting existing surveys on name clashes. |
| log_file | `String` | Path to a text file for errors. |

---

### 34. mscc_import_manhole_surveys

```ruby
#mscc_import_manhole_surveys(import_file, import_flag, import_images, id_gen, overwrite, log_file)
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Imports manhole survey data into a Collection Network from the MSCC5 XML format.

**`id_gen` values:**

| Value | Description |
|-------|-------------|
| `1` | Manhole/Node reference, Date and Time |
| `2` | Manhole/Node reference and an index for uniqueness |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| import_file | `String` | Path to the XML file. |
| import_flag | `String` | The data flag for imported fields. |
| import_images | `Boolean` | Whether to import defect images. |
| id_gen | `Integer` | ID generation method. See values above. |
| overwrite | `Boolean` | If `false`, prevents overwriting existing surveys on name clashes. |
| log_file | `String` | Path to a text file for errors. |

---

### 35. network_model_object

```ruby
#network_model_object ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the `WSModelObject` (or derived class) associated with this network.

If the network was loaded from a sim, the model object of the network (not the sim) is returned. This differs from [`#model_object`](#30-model_object), which would return the sim.

#### Return Value

`WSModelObject`

---

### 36. new_row_object

```ruby
#new_row_object(type) ⇒ WSRowObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Creates a new object in this network. Must be called within a network transaction, and a primary ID must be set for the object before writing changes.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | The object type. |

#### Return Value

`WSRowObject`

---

### 37. objects_in_polygon

```ruby
#objects_in_polygon(polygon, type) ⇒ Array<WSRowObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns an array of `WSRowObject` objects inside the polygon geometry, matching the type parameter.

When using an array of strings as the type, all values must be unique and cannot contain a category and a table within the same category.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| polygon | `WSRowObject` | An object containing polygon geometry. |
| type | `String`, `Array<String>`, `nil` | The name(s) of a type or category of object. `nil` searches all tables. |

#### Return Value

`Array<WSRowObject>`

---

### 38. odec_export_ex

```ruby
#odec_export_ex(format, config, options, table, *args) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports network data using the Open Data Export Centre. See `WSBaseNetworkObject.odec_export_ex` for full parameter details.

#### Return Value

`void`

---

### 39. odic_import_ex

```ruby
#odic_import_ex(format, config, options, table, *args) ⇒ Array<WSRowObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Imports and updates network data using the Open Data Import Centre, returning an array of the objects created or updated. Objects may also be deleted, but these are not returned. See `WSBaseNetworkObject.odec_import_ex` for full parameter details.

#### Return Value

`Array<WSRowObject>`

---

### 40. ribx_export_surveys

```ruby
#ribx_export_surveys(export_file, selection_only, log_file) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports manhole survey and CCTV survey data from a Collection Network to the RIBX XML format.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| export_file | `String` | Path to the output XML file. |
| selection_only | `Boolean` | If `true`, limits the export to selected objects. |
| log_file | `String` | Path to a text file for errors. |

#### Return Value

`Boolean`

---

### 41. ribx_import_surveys

```ruby
#ribx_import_surveys(import_file, import_flag, id_gen, overwrite, log_file)
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Imports CCTV survey and manhole survey data into a Collection Network from the RIBX XML format.

**`id_gen` values:**

| Value | Description |
|-------|-------------|
| `1` | StartNodeRef, Direction, Date and Time |
| `2` | StartNodeRef, Direction and an index for uniqueness |
| `3` | US node ID, Direction, Date and Time |
| `4` | US node ID, Direction and an index for uniqueness |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| import_file | `String` | Path to the XML file. |
| import_flag | `String` | The data flag for imported fields. |
| id_gen | `Integer` | ID generation method. See values above. |
| overwrite | `Boolean` | If `false`, prevents overwriting existing surveys on name clashes. |
| log_file | `String` | Path to a text file for errors. |

---

### 42. row_object

```ruby
#row_object(type, id) ⇒ WSRowObject?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns a specific row object by type and ID.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | The object type. |
| id | `String` | The object id, e.g. `'st543643'` or `st543643.st543473.1`. |

#### Return Value

`WSRowObject`, `nil` — The object found, or `nil` if no such object exists in the network.

#### Example

```ruby
node = network.row_object('wn_node', 'ST543643')
raise "Could not get node" if node.nil?
```

---

### 43. row_object_collection

```ruby
#row_object_collection(type) ⇒ WSRowObjectCollection
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns all row objects of a given type as a `WSRowObjectCollection`. Will be empty if there are none of this type.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | The object type. |

#### Return Value

`WSRowObjectCollection`

---

### 44. row_object_collection_selection

```ruby
#row_object_collection_selection(type) ⇒ WSRowObjectCollection
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns all selected row objects of a given type as a `WSRowObjectCollection`. Will be empty if none of this type are selected.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | The object type. |

#### Return Value

`WSRowObjectCollection`

---

### 45. row_objects

```ruby
#row_objects(type) ⇒ Array<WSRowObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns all row objects of a given type in an Array. Will be empty if there are none.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | The object type. |

#### Return Value

`Array<WSRowObject>`

---

### 46. row_objects_from_asset_id

```ruby
#row_objects_from_asset_id(type, id) ⇒ Array<WSRowObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns all row objects of a given type with the specified Asset ID. Useful when working with imported link objects where the multi-part ID may not be known.

Asset IDs are not guaranteed to be unique, so there may be multiple results. Use the `Array#first` method to access the first object.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | The object type. Cannot be `_nodes` or `_links`. |
| id | `String` | The object's asset id, e.g. `'st543643'`. |

#### Return Value

`Array<WSRowObject>` — Will be an empty array if none are found.

#### Example

```ruby
nodes = network.row_objects_from_asset_id('wn_node', 'ST543643')
puts nodes.first['asset_id']
# => 'ST543643'

# Helper to enforce uniqueness
def unique_row_object_from_asset_id(network, type, id)
  nodes = network.row_objects_from_asset_id(type, id)
  return (nodes.size != 1) ? nil : nodes.first
end
```

---

### 47. row_objects_selection

```ruby
#row_objects_selection(type) ⇒ Array<WSRowObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns all selected row objects of a given type in an Array. Will be empty if none of this type are selected.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `String` | The object type. |

#### Return Value

`Array<WSRowObject>`

---

### 48. run_sql

```ruby
#run_sql(table, query) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Runs a SQL query on this network. The SQL query can include multiple clauses, including saving results to a file, but cannot use any options that open results or prompt grids.

> **Note:** This method previously included capitalization. The new lower case method name is recommended.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| table | `String` | The table name. `_nodes` or `_links` are equivalent to 'all nodes' and 'all links' in SQL. |
| query | `String` | The SQL query. |

#### Return Value

`void`

---

### 49. run_inference

```ruby
#run_inference(inference, ground_model, mode, zone, error_file) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Runs the inference object on this network, which must be a collection asset network or a distribution asset network.

**Supported modes:**
- `nil`, `false`, or `'Network'` — run on the whole network.
- `true` or `'Selection'` — run on the current selection.
- `'Zone'` — run for the zone specified in the `zone` parameter.
- `'Category'` — run for zones with the zone category specified in the `zone` parameter.

The ground model parameter must be `nil` when used from the UI. If a ground model is loaded into the network (either TIN or grid), it will be used instead.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| inference | `Integer`, `String`, `WSModelObject` | The inference object. Can be the id, scripting path, or a `WSModelObject` of the correct type. |
| ground_model | `Integer`, `String`, `WSModelObject`, `nil` | Optional ground model (Exchange only). Can be the id (grid ground model only), scripting path, or a `WSModelObject` of the correct type. |
| mode | `String`, `Boolean`, `nil` | See supported modes above. |
| zone | `String`, `nil` | If mode is `'Zone'` or `'Category'`, the name of the zone or zone category. |
| error_file | `String`, `nil` | Path to an error file. |

#### Return Value

`void`

---

### 50. run_stored_query_object

```ruby
#run_stored_query_object(stored_query) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Runs a stored query on this network.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| stored_query | `Integer`, `String`, `WSModelObject` | The stored query object. Can be the id, scripting path, or a `WSModelObject` of the correct type. |

#### Return Value

`void`

---

### 51. save_selection

```ruby
#save_selection(selection_list) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Saves the current selection (in the current scenario) to an already existing selection list model object.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| selection_list | `Integer`, `String`, `WSModelObject` | The selection list object. Can be the id, scripting path, or a `WSModelObject` of the correct type. |

#### Return Value

`void`

---

### 52. scenarios

```ruby
#scenarios { |s| ... } ⇒ String
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Iterates through the scenarios, yielding a `String` of each scenario name. The base scenario is included as the string `Base` in English.

#### Return Value

`String`

#### Example

```ruby
network.scenarios { |scenario| puts scenario }

network.scenarios do |scenario|
  puts scenario
end
```

---

### 53. search_at_point

```ruby
#search_at_point(x, y, distance, types) ⇒ Array<WSRowObject>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Finds all objects within a given distance of a point.

When using an array of strings as the type, all values must be unique and cannot contain a category and a table within that category.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| x | `Numeric` | X coordinate. |
| y | `Numeric` | Y coordinate. |
| distance | `Numeric` | Search radius around the point. |
| type | `String`, `Array<String>`, `nil` | The name of a table or category, an array of names, or `nil` to search all tables. |

#### Return Value

`Array<WSRowObject>`

---

### 54. selection_size

```ruby
#selection_size ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the number of objects currently selected.

#### Return Value

`Integer`

---

### 55. set_projection_string

```ruby
#set_projection_string(string) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Sets the map projection string. The format depends on the current map control. Compatible projection strings for MapXTreme can be found in `C:\Program Files\Common Files\MapInfo\MapXtreme\VERSION\MapInfoCoordinateSystemSet.xml`.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| string | `String` | The projection string. |

#### Return Value

`void`

#### Example

```ruby
# British National Grid (EPSG:27700)
network.set_projection_string('8,79,7,-2,49,0.9996012717,400000,-100000')
```

---

### 56. snapshot_export

```ruby
#snapshot_export(file) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports a snapshot of the network to the given file. All objects are exported from all tables, but image files and GeoPlan properties and themes are not exported.

Snapshots cannot be exported from networks with uncommitted changes.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Path to the file. |

#### Return Value

`void`

---

### 57. snapshot_export_ex

```ruby
#snapshot_export_ex(file, options) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Exports a snapshot of the network to the given file with additional options. If no options hash is provided, all objects are exported from all tables, but image files and GeoPlan properties and themes are not exported.

Snapshots cannot be exported from networks with uncommitted changes.

> **Note:** `SelectedOnly` must not be mixed with `Tables` or `ChangesFromVersion`.

**`options` hash keys:**

| Key | Type | Description |
|-----|------|-------------|
| `SelectedOnly` | `Boolean` | If `true`, only currently selected objects are exported. |
| `IncludeImageFiles` | `Boolean` | If `true`, includes image file data. |
| `IncludeGeoPlanPropertiesAndThemes` | `Boolean` | If `true`, includes GeoPlan properties and themes. |
| `ChangesFromVersion` | `Integer` | If present, exports the diff from the network's version with this commit ID. |
| `Tables` | `Array<String>` | Internal table names to export (as returned by [`#table_names`](#61-table_names)). If absent, all tables are exported. |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Path to the file. |
| options | `Hash` | See description. |

#### Return Value

`void`

---

### 58. snapshot_import_ex

```ruby
#snapshot_import_ex(file, options) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Imports a snapshot file into the network from a file with the provided options.

**`options` hash keys:**

| Key | Type | Description |
|-----|------|-------------|
| `Tables` | `Array<String>` | Network table names to import. If not provided, all tables are imported. |
| `AllowDeletes` | `Boolean` | |
| `ImportGeoPlanPropertiesAndThemes` | `Boolean` | |
| `UpdateExistingObjectsFoundByID` | `Boolean` | |
| `UpdateExistingObjectsFoundByUID` | `Boolean` | |
| `ImportImageFiles` | `Boolean` | |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Path to the file. |
| options | `Hash` | See description. |

#### Return Value

`void`

---

### 59. snapshot_scan

```ruby
#snapshot_scan(file) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Scans a snapshot file and returns a hash of details about it.

**Return hash keys:**

| Key | Type | Description |
|-----|------|-------------|
| `NetworkGUID` | `String` | GUID of the network from which the snapshot was exported. |
| `CommitGUID` | `String` | GUID of the commit from which the snapshot was exported. |
| `CommitID` | `Integer` | ID of the commit from which the snapshot was exported. |
| `NetworkTypeCode` | `String` | Type of network, e.g. `'Collection Network'`. |
| `DatabaseGUID` | `String` | GUID of the database version from which the snapshot was exported. |
| `DatabaseSubVersion` | `Integer` | Subversion of the database version. |
| `UnknownTableCount` | `Integer` | Number of tables in the snapshot not recognised by the software (only greater than 0 if exported from a newer version). |
| `FileCount` | `Integer` | Number of image files contained in the snapshot. |
| `ContainsGeoPlanPropertiesAndThemes` | `Boolean` | `true` if exported with GeoPlan properties and themes. |
| `Tables` | `Hash` | Hash with per-table info: `ObjectCount`, `ObjectsWithOldVersionsCount`, `ObjectsFoundByUID`, `ObjectsFoundByID`, `DeleteRecordsCount`, `UnknownFieldCount`. |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Path to the snapshot file. |

#### Return Value

`Hash<String, Any>`

---

### 60. table

```ruby
#table(name) ⇒ WSTableInfo
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns a `WSTableInfo` object for a specific table in this network.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | Name of the table. |

#### Return Value

`WSTableInfo`

---

### 61. table_names

```ruby
#table_names ⇒ Array<String>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the names of all tables in this network.

#### Return Value

`Array<String>`

---

### 62. tables

```ruby
#tables ⇒ Array<WSTableInfo>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns an array of `WSTableInfo` objects for the tables in this network.

#### Return Value

`Array<WSTableInfo>`

---

### 63. timestep_count

```ruby
#timestep_count ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the number of result timesteps, not including the maximum timestep.

#### Return Value

`Integer`

---

### 64. timestep_time

```ruby
#timestep_time(timestep_no) ⇒ DateTime
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns the actual time of the given timestep index.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| timestep_no | `Integer` | The timestep index. |

#### Return Value

`DateTime`

---

### 65. transaction_begin

```ruby
#transaction_begin ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Begins a transaction, during which network data can be modified (adding/removing objects or changing fields). Most changes to a network must be within a transaction.

A transaction can be ended with [`#transaction_commit`](#66-transaction_commit) to save changes, or [`#transaction_rollback`](#67-transaction_rollback) to abandon them.

#### Return Value

`void`

---

### 66. transaction_commit

```ruby
#transaction_commit ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Commits any changes to the network since [`#transaction_begin`](#65-transaction_begin).

#### Return Value

`void`

---

### 67. transaction_rollback

```ruby
#transaction_rollback ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Rolls back (ends) the transaction, reverting any changes made since [`#transaction_begin`](#65-transaction_begin).

Use with caution if storing references to `WSRowObject` objects or associated data, as this may break references and cause exceptions when attempting to access or work with them.

#### Return Value

`void`

---

### 68. update_cctv_scores

```ruby
#update_cctv_scores ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Calculates CCTV scores for all surveys in the network using the current standard.

#### Return Value

`void`

---

### 69. xprafts_import

```ruby
#xprafts_import(file, use_large_size, split_on_lag_links, combine_subcatchments, log) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Updates the network from an XPRAFTS `.xpx` file.

> **Note:** This method previously included capitalization. The new lower case method name is recommended.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | Absolute path to the XPRAFTS model, including extension (`.xpx`). |
| use_large_size | `Boolean` | If the XPRAFTS model is configured to use the large unit size. |
| split_on_lag_links | `Boolean` | If `true`, networks are split downstream of channel links and maintain lag link data. If `false`, network connectivity is maintained by converting downstream lag links to channel links. |
| combine_subcatchments | `Boolean` | If `true`, combines the 1st and 2nd subcatchment as a single subcatchment polygon, setting the per-surface rafts b option and the rafts adapt factor and Manning's roughness at the runoff surface level. |
| log | `String` | Path to save the import log including extension (`.txt`). |

#### Return Value

`void`

#### Example

```ruby
model_group.xprafts_import('C:/temp/1.xpx', true, false, true, 'C:/temp/log.txt')
```
