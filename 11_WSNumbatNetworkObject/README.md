# WSNumbatNetworkObject

**Inherits from:** `WSModelObject` > `WSBaseNetworkObject` > `WSNumbatNetworkObject`

A network using merge version control.

> **Note:** a network in this context is not the same as a 'network' in the user interface.

## Availability

| Context | Available |
|---------|-----------|
| EXCHANGE | Yes |
| UI | No |

---

## Methods Summary

| # | Method | Return Type | Availability |
|---|--------|-------------|--------------|
| 01 | [branch](#01-branch) | `WSModelObject` | EXCHANGE |
| 02 | [commit](#02-commit) | `Integer` | EXCHANGE |
| 03 | [commit_reserve](#03-commit_reserve) | `Integer` | EXCHANGE |
| 04 | [commits](#04-commits) | `WSCommits` | EXCHANGE |
| 05 | [csv_changes](#05-csv_changes) | `void` | EXCHANGE |
| 06 | [current_commit_id](#06-current_commit_id) | `Integer` | EXCHANGE |
| 07 | [gis_export](#07-gis_export) | `void` | EXCHANGE |
| 08 | [latest_commit_id](#08-latest_commit_id) | `Integer` | EXCHANGE |
| 09 | [list_gis_export_tables](#09-list_gis_export_tables) | `Array<String>` | EXCHANGE |
| 10 | [open_version](#10-open_version) | `WSOpenNetwork` | EXCHANGE |
| 11 | [reserve](#11-reserve) | `void` | EXCHANGE |
| 12 | [revert](#12-revert) | `void` | EXCHANGE |
| 13 | [select_changes](#13-select_changes) | `void` | EXCHANGE |
| 14 | [select_clear](#14-select_clear) | `void` | EXCHANGE |
| 15 | [select_count](#15-select_count) | `Integer` | EXCHANGE |
| 16 | [select_sql](#16-select_sql) | `Integer` | EXCHANGE |
| 17 | [uncommitted_changes?](#17-uncommitted_changes) | `Boolean` | EXCHANGE |
| 18 | [unreserve](#18-unreserve) | `void` | EXCHANGE |
| 19 | [update](#19-update) | `Boolean` | EXCHANGE |
| 20 | [user_field_names](#20-user_field_names) | `void` | EXCHANGE |

---

## Method Details

### 01. branch

```ruby
#branch(commit_id, new_name) ⇒ WSModelObject
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Branches the network object, creating a new network object.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| commit_id | `Integer` | The branch is performed from this commit id. |
| new_name | `String` | The new network name. |

#### Return Value

`WSModelObject`

---

### 02. commit

```ruby
#commit(comment) ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Commits any changes to the network to the database. Returns the commit ID, or returns `nil` if there were no changes made and therefore no new commit.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| comment | `String` | The commit comment. |

#### Return Value

`Integer` — The new commit ID, or `nil` if there were no changes.

#### Example

```ruby
network.commit('This is the comment for my commit')
```

---

### 03. commit_reserve

```ruby
#commit_reserve(comment) ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Performs the same action as [`#commit`](#02-commit), but keeps the network reserved if it was already reserved.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| comment | `String` | The commit comment. |

#### Return Value

`Integer` — The new commit ID.

---

### 04. commits

```ruby
#commits ⇒ WSCommits
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the commit history for the network.

#### Return Value

`WSCommits`

#### Example

```ruby
# Print the number of commits
commits = network.commits
puts "There have been #{commits.length} commits to this network!"

# Print all comments from user 'Badger'
network.commits.each do |commit|
  puts "#{commit.commit_id}: #{commit.comment}" if commit.user == 'Badger'
end
```

---

### 05. csv_changes

```ruby
#csv_changes(commit_id_1, commit_id_2, file) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Outputs the differences between `commit_id_1` and `commit_id_2` of this network to the specified CSV file. The CSV file output is the same as the 'compare network' tool in the user interface, and can be used to apply the changes to another network via the 'Import/Update from CSV files' function.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| commit_id_1 | `Integer` | The first commit ID to compare from. |
| commit_id_2 | `Integer` | The second commit ID to compare to. |
| file | `String` | Path to the CSV file, including extension. |

#### Return Value

`void`

---

### 06. current_commit_id

```ruby
#current_commit_id ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the commit ID of the local copy of the network. This may not be the most recent commit ID on the server, which is returned by [`#latest_commit_id`](#08-latest_commit_id).

#### Return Value

`Integer`

---

### 07. gis_export

```ruby
#gis_export(format, options, destination) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Exports the network data to a GIS format.

> **Note:** This method previously included capitalization in its name. The new lower case method name is recommended.

**`options` hash keys:**

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `ExportFlags` | `Boolean` | `true` | If `true`, field flags are exported along with the data. |
| `Feature Dataset` | `String` | `""` | Only relevant for GeoDatabases. The name of the feature dataset. |
| `SkipEmptyTables` | `Boolean` | `false` | If `true`, will skip empty tables. |
| `Tables` | `Array<String>` | all tables | Table names to export, as returned by [`#list_gis_export_tables`](#09-list_gis_export_tables). Does not allow duplicates or unrecognized tables. |
| `UseArcGISCompatability` | `Boolean` | `false` | |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| format | `String` | Either `shp` (ESRI shapefile), `tab` (MapInfo TAB), `mif` (MapInfo MIF), or `gdb` (ESRI geodatabase). |
| options | `Hash`, `nil` | Options hash as described above. If `nil` or a key is missing, default behaviour applies. |
| destination | `String` | The folder for exported files, except for a geodatabase where it is the name of the geodatabase file with `.gdb` extension. |

#### Return Value

`void`

---

### 08. latest_commit_id

```ruby
#latest_commit_id ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the latest commit ID for the network from the server. This may not be the same commit ID as the local copy, which is returned by [`#current_commit_id`](#06-current_commit_id).

#### Return Value

`Integer`

---

### 09. list_gis_export_tables

```ruby
#list_gis_export_tables ⇒ Array<String>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the tables that will be exported using the [`#gis_export`](#07-gis_export) method.

> **Note:** This method previously included capitalization in its name. The new lower case method name is recommended.

#### Return Value

`Array<String>`

---

### 10. open_version

```ruby
#open_version(commit_id) ⇒ WSOpenNetwork
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Opens a specific version of the network from its commit ID.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| commit_id | `Integer` | The commit ID of the version to open. |

#### Return Value

`WSOpenNetwork`

---

### 11. reserve

```ruby
#reserve ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Reserves the network so no one else can edit it, and also updates the local copy to the latest version.

#### Return Value

`void`

---

### 12. revert

```ruby
#revert ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Reverts any changes to the network that have not yet been committed. This does not guarantee that the network is up to date, only that any changes made to the local copy have been abandoned.

#### Return Value

`void`

---

### 13. select_changes

```ruby
#select_changes(commit_id) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Selects all objects added or changed between the provided commit ID and the current network. Deleted objects cannot be selected. The network must have no outstanding changes, or an exception will be raised.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| commit_id | `Integer` | The commit ID to compare changes from. |

#### Return Value

`void`

---

### 14. select_clear

```ruby
#select_clear ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Deselects all objects in the network.

#### Return Value

`void`

---

### 15. select_count

```ruby
#select_count ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the number of selected objects in the network.

#### Return Value

`Integer`

---

### 16. select_sql

```ruby
#select_sql(table, query) ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Runs a SQL select query. A SQL query can further qualify the table name in the query or work with multiple tables.

The SQL query can include multiple clauses, including saving results to a file, but cannot use any options that open results or prompt grids.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| table | `String` | The table name. `_nodes` or `_links` are equivalent to 'all nodes' and 'all links' in SQL. |
| query | `String` | The SQL query. |

#### Return Value

`Integer` — The number of objects selected in the last clause, or `0`.

#### Example

```ruby
# Select all nodes above 40m elevation
count = network.select_sql('_nodes', 'z > 40')
puts format("There are %i nodes above 40m in this network!", count)

# Select node IDs into a file
network.select_sql('hw_node', "SELECT oid INTO FILE 'C:\Export\Distinct.csv'")
```

---

### 17. uncommitted_changes?

```ruby
#uncommitted_changes? ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns whether there are uncommitted changes to the network.

#### Return Value

`Boolean`

---

### 18. unreserve

```ruby
#unreserve ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Cancels any reservation of the network.

#### Return Value

`void`

---

### 19. update

```ruby
#update ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Updates the local copy of the network to the latest version from the server. Not relevant for standalone databases.

#### Return Value

`Boolean` — `true` if successful, `false` if there are conflicts.

---

### 20. user_field_names

```ruby
#user_field_names(file, string) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Exports a CSV file containing the user field names for all object types in the network, including any network or database customisations.

The CSV file has no header. The first column is the provided string, the second column is the internal user field table name, and the third column is the user field name as shown in the user interface including customisations.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| file | `String` | The file to export, including extension (`.csv`). |
| string | `String` | An arbitrary string value output as the first column. |

#### Return Value

`void`

#### Example

```ruby
network.user_field_names('C:/Temp/Badger.csv', 'x')
# Produces:
# x, user_text_1, Badger
# x, user_text_2, Penguin
```
