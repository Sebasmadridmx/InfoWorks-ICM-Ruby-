# WSApplication

The top-level class in InfoWorks ICM Ruby scripting. Used in scripts run from both the **User Interface (UI)** and **Exchange**.

This is a static class, meaning methods are called directly with `WSApplication.method_name` syntax. Most methods get/set global application settings or create/open databases.

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
| 01 | [add_ons_folder](#01-add_ons_folder) | `String` | EXCHANGE, UI |
| 02 | [background_network](#02-background_network) | `WSOpenNetwork?` | UI |
| 03 | [cancel_job](#03-cancel_job) | `void` | EXCHANGE |
| 04 | [choose_selection](#04-choose_selection) | `WSModelObject?` | UI |
| 05 | [color](#05-color) | `Integer` | UI |
| 06 | [connect_local_agent](#06-connect_local_agent) | `Boolean` | EXCHANGE |
| 07 | [create](#07-create) | `void` | EXCHANGE |
| 08 | [create_transportable](#08-create_transportable) | `void` | EXCHANGE |
| 09 | [current_database](#09-current_database) | `WSDatabase` | UI |
| 10 | [current_network](#10-current_network) | `WSOpenNetwork` | UI |
| 11 | [file_dialog](#11-file_dialog) | `String?` | UI |
| 12 | [folder_dialog](#12-folder_dialog) | `String?` | UI |
| 13 | [graph](#13-graph) | `void` | UI |
| 14 | [input_box](#14-input_box) | `String?` | UI |
| 15 | [launch_sims](#15-launch_sims) | `Array<String>` | EXCHANGE |
| 16 | [launch_sims_ex](#16-launch_sims_ex) | `Array<String>` | EXCHANGE |
| 17 | [local_root](#17-local_root) | `String` | EXCHANGE, UI |
| 18 | [map_component](#18-map_component) | `String?` | EXCHANGE |
| 19 | [map_component_set](#19-map_component_set) | `void` | EXCHANGE |
| 20 | [message_box](#20-message_box) | `String?` | UI |
| 21 | [open](#21-open) | `WSDatabase` | EXCHANGE |
| 22 | [open_text_view](#22-open_text_view) | `void` | UI |
| 23 | [override_user_unit](#23-override_user_unit) | `Boolean` | EXCHANGE |
| 24 | [override_user_units](#24-override_user_units) | `String` | EXCHANGE |
| 25 | [prompt](#25-prompt) | `Array<Any>?` | UI |
| 26 | [results_folder](#26-results_folder) | `String` | EXCHANGE, UI |
| 27 | [rpa_export](#27-rpa_export) | `void` | EXCHANGE, UI |
| 28 | [scalars](#28-scalars) | `void` | UI |
| 29 | [script_file](#29-script_file) | `String` | EXCHANGE, UI |
| 30 | [set_exit_code](#30-set_exit_code) | `void` | EXCHANGE |
| 31 | [set_results_folder](#31-set_results_folder) | `void` | EXCHANGE |
| 32 | [set_working_folder](#32-set_working_folder) | `void` | EXCHANGE |
| 33 | [ui](#33-ui) | `Boolean` | EXCHANGE, UI |
| 34 | [use_arcgis_desktop_licence](#34-use_arcgis_desktop_licence) | `void` | EXCHANGE |
| 35 | [use_user_units_set](#35-use_user_units_set) | `void` | EXCHANGE, UI |
| 36 | [use_user_units](#36-use_user_units) | `Boolean` | EXCHANGE, UI |
| 37 | [use_utf8_set](#37-use_utf8_set) | `void` | EXCHANGE, UI |
| 38 | [use_utf8](#38-use_utf8) | `Boolean` | EXCHANGE, UI |
| 39 | [version](#39-version) | `String` | EXCHANGE, UI |
| 40 | [wait_for_jobs](#40-wait_for_jobs) | `Integer?` | EXCHANGE |
| 41 | [wds_query_databases](#41-wds_query_databases) | `Hash` | EXCHANGE, UI |
| 42 | [working_folder](#42-working_folder) | `String` | EXCHANGE, UI |

---

## Method Details

### 01 add_ons_folder
```ruby
WSApplication.add_ons_folder => String
```
`EXCHANGE` `UI`

Returns the full path of the add-ons folder.

> Note: the folder will not exist unless manually created. Its parent folder will almost certainly exist.

```ruby
puts WSApplication.add_ons_folder
# => "C:\Users\badger\AppData\Roaming\Innovyze\WorkgroupClient\scripts"
```

---

### 02 background_network
```ruby
WSApplication.background_network => WSOpenNetwork?
```
`UI`

Returns the active background network from the GeoPlan that currently has focus.

---

### 03 cancel_job
```ruby
WSApplication.cancel_job(id) => void
```
`EXCHANGE`

Cancels a job being run by the agent.

| Parameter | Type | Description |
|---|---|---|
| `id` | Integer | Job id retrieved from `launch_sims` |

---

### 04 choose_selection
```ruby
WSApplication.choose_selection(title) => WSModelObject?
```
`UI`

Displays a prompt allowing the user to choose a selection list object from the current database.

| Parameter | Type | Description |
|---|---|---|
| `title` | String | Text displayed on the prompt title bar |
| **Returns** | WSModelObject, nil | nil if user cancels |

---

### 05 color
```ruby
WSApplication.color(r, g, b) => Integer
```
`UI`

Converts RGB values to an integer format for use with the `graph` method.

| Parameter | Type | Description |
|---|---|---|
| `r` | Numeric | Red value (0-255) |
| `g` | Numeric | Green value (0-255) |
| `b` | Numeric | Blue value (0-255) |
| **Returns** | Integer | RGB as integer |

```ruby
WSApplication.color(0, 0, 0)         # black
WSApplication.color(255, 0, 0)       # red
WSApplication.color(255, 255, 255)   # white
```

---

### 06 connect_local_agent
```ruby
WSApplication.connect_local_agent(timeout) => Boolean
```
`EXCHANGE`

Connects to the local agent. Required before calling `launch_sims` or `launch_sims_ex`.

| Parameter | Type | Description |
|---|---|---|
| `timeout` | Numeric | Milliseconds to wait (1000ms = 1s) |
| **Returns** | Boolean | true if connection successful |

---

### 07 create
```ruby
WSApplication.create(path, version) => void
```
`EXCHANGE`

Creates a new standalone or workgroup database. Use absolute paths for standalone databases.

| Parameter | Type | Description |
|---|---|---|
| `path` | String | Filepath or connection string |
| `version` | String | e.g. `"2024.0"` (optional) |

```ruby
WSApplication.create('C:/Badger/MyNewDatabase.icmm')
WSApplication.create('localhost:40000/Badger/MyNewDatabase', "2024.0")
```

---

### 08 create_transportable
```ruby
WSApplication.create_transportable(path, version) => void
```
`EXCHANGE`

Creates a transportable database. Use absolute paths.

| Parameter | Type | Description |
|---|---|---|
| `path` | String | Absolute path including filename and extension |
| `version` | String | e.g. `"2024.0"` (optional) |

```ruby
WSApplication.create_transportable('C:/Temp/Badger.wspt')
```

---

### 09 current_database
```ruby
WSApplication.current_database => WSDatabase
```
`UI`

Returns the current database when running from the UI. Limited functionality available.

---

### 10 current_network
```ruby
WSApplication.current_network => WSOpenNetwork
```
`UI`

Returns the active network from the GeoPlan that currently has focus. May have results loaded and/or be read only.

---

### 11 file_dialog
```ruby
WSApplication.file_dialog(open, extension, description, default, multiple, hard_wire_cancel) => String? or Array<String>?
```
`UI`

Displays a file open or save dialog.

| Parameter | Type | Description |
|---|---|---|
| `open` | Boolean | true for open dialog, false for save dialog |
| `extension` | String | File extension without period e.g. `csv` |
| `description` | String | File type description |
| `default` | String | Default file name (no path) |
| `multiple` | Boolean | Allow multiple selection (open only) |
| `hard_wire_cancel` | Boolean | Script exits on cancel if true |
| **Returns** | String, Array\<String\>, nil | |

---

### 12 folder_dialog
```ruby
WSApplication.folder_dialog(title, hard_wire_cancel) => String?
```
`UI`

Displays a dialog allowing the user to select a folder.

| Parameter | Type | Description |
|---|---|---|
| `title` | String | Dialog title |
| `hard_wire_cancel` | Boolean | Script exits on cancel if true |
| **Returns** | String, nil | |

---

### 13 graph
```ruby
WSApplication.graph(options) => void
```
`UI`

Displays a graph. The `options` parameter is a hash with the following keys:

| Key | Type | Description |
|---|---|---|
| `WindowTitle` | String | Title of the window |
| `GraphTitle` | String | Title of the graph |
| `XAxisLabel` | String | X axis label |
| `YAxisLabel` | String | Y axis label |
| `IsTime` | Boolean | true if X axis is time-based |
| `Traces` | Array\<Hash\> | Array of trace hashes |

Each trace hash:

| Key | Type | Description |
|---|---|---|
| `Title` | String | Trace name |
| `TraceColour` | Integer | RGB integer via `color` method |
| `SymbolColour` | Integer | RGB integer via `color` method |
| `Marker` | String | `None`, `Cross`, `XCross`, `Star`, `Circle`, `Triangle`, `Diamond`, `Square`, `FCircle`, `FTriangle`, `FDiamond`, `FSquare` |
| `LineType` | String | `None`, `Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot` |
| `XArray` | Array | X coordinate values |
| `YArray` | Array | Y coordinate values |

---

### 14 input_box
```ruby
WSApplication.input_box(prompt, title, default) => String?
```
`UI`

Displays a dialog prompting the user for a text value.

| Parameter | Type | Description |
|---|---|---|
| `prompt` | String | Text displayed on the dialog |
| `title` | String, nil | Window title, nil for default |
| `default` | String | Initial value |
| **Returns** | String, nil | nil if user cancels |

```ruby
distance = WSApplication.input_box('Distance in Meters (1-100m)', 'Enter A Distance', '50.0')
```

---

### 15 launch_sims
```ruby
WSApplication.launch_sims(sims, server, results_on_server, max_threads, after) => Array<String>
```
`EXCHANGE`

Launches one or more simulations. Requires `connect_local_agent` first.

| Parameter | Type | Description |
|---|---|---|
| `sims` | Array\<WSModelObject\> | Array of simulations |
| `server` | String | Server name, `'.'` for local, `'*'` for any |
| `results_on_server` | Boolean | |
| `max_threads` | Integer | 0 to let agent choose |
| `after` | Integer | time_t time to run after, 0 for now |
| **Returns** | Array\<String\> | Job ids, nil for any that failed to launch |

---

### 16 launch_sims_ex
```ruby
WSApplication.launch_sims_ex(sims, options) => Array<String>
```
`EXCHANGE`

Launches simulations with extended options. Requires `connect_local_agent` first.

| Parameter | Type | Description |
|---|---|---|
| `sims` | Array\<WSModelObject\> | Array of simulations |
| `options` | Hash | See below |
| **Returns** | Array\<String\> | Job ids |

Options hash:

| Key | Type | Default | Description |
|---|---|---|---|
| `RunOn` | String | `'.'` | Server name |
| `ResultsOnServer` | Boolean | false | |
| `MaxThreads` | Integer | 0 | |
| `After` | Integer | 0 | |
| `SU` | Boolean | false | Use ICMOne license |
| `DownloadSelection` | String | `'ALL_RESULTS'` | `NO_RESULTS`, `SUMMARY_RESULTS`, `ALL_RESULTS` |

---

### 17 local_root
```ruby
WSApplication.local_root => String
```
`EXCHANGE` `UI`

Returns the working folder path.

```ruby
puts WSApplication.local_root
```

---

### 18 map_component
```ruby
WSApplication.map_component => String?
```
`EXCHANGE`

Returns the map component in use. Supported values: `mapxtreme`, `arcobjects`, `arcengine`.

---

### 19 map_component_set
```ruby
WSApplication.map_component=(component) => void
```
`EXCHANGE`

Sets the map component to use.

| Parameter | Type | Description |
|---|---|---|
| `component` | String | `mapxtreme`, `arcobjects`, or `arcengine` |

---

### 20 message_box
```ruby
WSApplication.message_box(text, buttons, icon, hard_wire_cancel) => String?
```
`UI`

Displays a message box.

| Parameter | Type | Description |
|---|---|---|
| `text` | String | Text displayed in the prompt |
| `buttons` | String, nil | `ok`, `okcancel`, `yesno`, `yesnocancel`, nil defaults to `okcancel` |
| `icon` | String, nil | `!`, `?`, `information`, `stop`, nil defaults to `!` |
| `hard_wire_cancel` | Boolean, nil | Script exits on cancel if true |
| **Returns** | String, nil | `yes`, `no`, `ok`, or `cancel` |

---

### 21 open
```ruby
WSApplication.open(path, update) => WSDatabase
WSApplication.open(path, version) => WSDatabase
```
`EXCHANGE`

Opens a database and returns it as a WSDatabase object.

| Parameter | Type | Description |
|---|---|---|
| `path` | String | Filepath, connection string, or cloud path |
| `update` | Boolean | Update to current version, default false |
| `version` | String | Update to specific version e.g. `"2024.0"` |
| **Returns** | WSDatabase | |

---

### 22 open_text_view
```ruby
WSApplication.open_text_view(title, filename, delete_on_exit) => void
```
`UI`

Opens a text file in a dialog. Does not block the current thread.

| Parameter | Type | Description |
|---|---|---|
| `title` | String | Window title |
| `filename` | String | Path to the text file |
| `delete_on_exit` | Boolean | Delete file when dialog is closed |

---

### 23 override_user_unit
```ruby
WSApplication.override_user_unit(code, value) => Boolean
```
`EXCHANGE`

Overrides a single user unit for the duration of the script.

| Parameter | Type | Description |
|---|---|---|
| `code` | String | Unit code e.g. `'xy'` |
| `value` | String | Unit value e.g. `'us survey ft'` |
| **Returns** | Boolean | false if code or value invalid |

```ruby
success = WSApplication.override_user_unit('X', 'ft')
raise "Failed to set user unit X" unless success
```

---

### 24 override_user_units
```ruby
WSApplication.override_user_units(file) => String
```
`EXCHANGE`

Overrides user units in bulk using a CSV file. Format: `unit_code, unit_value` with no header.

| Parameter | Type | Description |
|---|---|---|
| `file` | String | Filepath to units CSV |
| **Returns** | String | Any errors, or empty string if successful |

---

### 25 prompt
```ruby
WSApplication.prompt(title, layout, hard_wire_cancel) => Array<Any>?
```
`UI`

Displays a window with a grid of editable values.

| Parameter | Type | Description |
|---|---|---|
| `title` | String | Window title |
| `layout` | Array\<Array\> | Each row: `[description, type, default, decimals, subtype, ...]` |
| `hard_wire_cancel` | Boolean, nil | Script exits on cancel if true |
| **Returns** | Array\<Any\>, nil | |

Types: `NUMBER`, `STRING`, `DATE`, `BOOLEAN`, `READONLY`
Subtypes: `RANGE`, `LIST`, `MONTH`, `FILE`, `FOLDER`

---

### 26 results_folder
```ruby
WSApplication.results_folder => String
```
`EXCHANGE` `UI`

Returns the current results folder path.

---

### 27 rpa_export
```ruby
WSApplication.rpa_export(sim_ids, return_per, output_file) => void
```
`EXCHANGE` `UI`

Performs a Return Period Analysis and exports results to CSV.

| Parameter | Type | Description |
|---|---|---|
| `sim_ids` | Array | Integer ids of successful sims |
| `return_per` | Integer | Return period in years |
| `output_file` | String | Output CSV path |

---

### 28 scalars
```ruby
WSApplication.scalars(title, layout, hard_wire_cancel) => void
```
`UI`

Displays a grid of key/value pairs. Each item in layout: `[description, value, decimal_places]`.

| Parameter | Type | Description |
|---|---|---|
| `title` | String | Window title |
| `layout` | Array\<Array\> | Array of rows |
| `hard_wire_cancel` | Boolean | Script exits on cancel if true |

---

### 29 script_file
```ruby
WSApplication.script_file => String
```
`EXCHANGE` `UI`

Returns the absolute path of the first Ruby script file.

```ruby
script_file = WSApplication.script_file
File.dirname(script_file)  # get containing folder
```

---

### 30 set_exit_code
```ruby
WSApplication.set_exit_code(code) => void
```
`EXCHANGE`

Sets the exit code returned to the OS when Exchange finishes. Default is 0 (success).

| Parameter | Type | Description |
|---|---|---|
| `code` | Integer | Positive integer exit code |

---

### 31 set_results_folder
```ruby
WSApplication.set_results_folder(path) => void
```
`EXCHANGE`

Sets the results folder for this Exchange instance. Not persisted after process ends.

| Parameter | Type | Description |
|---|---|---|
| `path` | String | Path to results folder |

---

### 32 set_working_folder
```ruby
WSApplication.set_working_folder(path) => void
```
`EXCHANGE`

Sets the working folder for this Exchange instance. Not persisted after process ends.

| Parameter | Type | Description |
|---|---|---|
| `path` | String | Path to working folder |

---

### 33 ui
```ruby
WSApplication.ui? => Boolean
```
`EXCHANGE` `UI`

Returns whether the script is running in the UI.

```ruby
raise "Must be run from UI" unless WSApplication.ui?
raise "Cannot be run from UI" if WSApplication.ui?
```

---

### 34 use_arcgis_desktop_licence
```ruby
WSApplication.use_arcgis_desktop_licence(bool) => void
```
`EXCHANGE`

Sets whether Open Data Import/Export methods should use an ArcGIS desktop license.

| Parameter | Type | Description |
|---|---|---|
| `bool` | Boolean | |

---

### 35 use_user_units_set
```ruby
WSApplication.use_user_units=(bool) => void
```
`EXCHANGE` `UI`

Sets whether the application should use user units. Default is false in Exchange, true in UI.

| Parameter | Type | Description |
|---|---|---|
| `bool` | Boolean | |

---

### 36 use_user_units
```ruby
WSApplication.use_user_units? => Boolean
```
`EXCHANGE` `UI`

Returns whether the application is using user units.

---

### 37 use_utf8_set
```ruby
WSApplication.use_utf8=(flag) => void
```
`EXCHANGE` `UI`

Sets whether the application should use UTF8 in string handling. Default is false.

| Parameter | Type | Description |
|---|---|---|
| `flag` | Boolean | Whether to use UTF8 |

---

### 38 use_utf8
```ruby
WSApplication.use_utf8? => Boolean
```
`EXCHANGE` `UI`

Returns whether the application is using UTF8 in string handling. Default is false.

---

### 39 version
```ruby
WSApplication.version => String
```
`EXCHANGE` `UI`

Returns the software version number.

```ruby
puts WSApplication.version
# => '26.0.162'
```

---

### 40 wait_for_jobs
```ruby
WSApplication.wait_for_jobs(jobs, wait_for_all, timeout) => Integer?
```
`EXCHANGE`

Waits for one or all jobs to complete, or for timeout. Blocks the current thread.

| Parameter | Type | Description |
|---|---|---|
| `jobs` | Array\<Integer, nil\> | Job ids from `launch_sims` |
| `wait_for_all` | Boolean | true to wait for all, false for any |
| `timeout` | Numeric | Timeout in milliseconds |
| **Returns** | Integer, nil | Index of job that ended wait, nil if timeout |

---

### 41 wds_query_databases
```ruby
WSApplication.wds_query_databases(server, port) => Hash
```
`EXCHANGE` `UI`

Queries a Workgroup Data Server.

| Parameter | Type | Description |
|---|---|---|
| `server` | String | Server address, `localhost` for local |
| `port` | Integer | Server port, default `40000` |
| **Returns** | Hash | `response`, `databases`, `allowDatabaseCreation` |

---

### 42 working_folder
```ruby
WSApplication.working_folder => String
```
`EXCHANGE` `UI`

Returns the current working folder path.
