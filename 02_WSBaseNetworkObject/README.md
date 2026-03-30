# WSBaseNetworkObject

Inherits from: `WSModelObject`

A base class for network objects in InfoWorks ICM. Provides methods for importing and exporting network data in a variety of formats.

---

## Availability

| Tag | Meaning |
|---|---|
| `EXCHANGE` | Available in Exchange scripts |

---

## Methods

| # | Method | Returns | Available |
|---|---|---|---|
| 01 | [csv_export](#01-csv_export) | `void` | EXCHANGE |
| 02 | [csv_import](#02-csv_import) | `void` | EXCHANGE |
| 03 | [odec_export_ex](#03-odec_export_ex) | `void` | EXCHANGE |
| 04 | [odic_import_ex](#04-odic_import_ex) | `void` | EXCHANGE |
| 05 | [remove_local](#05-remove_local) | `void` | EXCHANGE |

---

## Method Details

### 01 csv_export
```ruby
network.csv_export(file, options) => void
```
`EXCHANGE`

Exports the network to a CSV file, with options similar to those in the user interface.

| Parameter | Type | Description |
|---|---|---|
| `file` | String | Path to the CSV file |
| `options` | Hash, nil | Options hash (see below), or nil for defaults |

**Options hash:**

| Key | Type | Default | Notes |
|---|---|---|---|
| `Use Display Precision` | Boolean | true | |
| `Field Descriptions` | Boolean | false | |
| `Field Names` | Boolean | true | |
| `Flag Fields` | Boolean | true | |
| `Multiple Files` | Boolean | false | true to export to different files |
| `Native System Types` | Boolean | false | |
| `User Units` | Boolean | false | |
| `Object Types` | Boolean | false | |
| `Selection Only` | Boolean | false | |
| `Units Text` | Boolean | false | |
| `Triangles` | Boolean | false | |
| `Coordinate Arrays Format` | String | `'Packed'` | `'Packed'`, `'None'`, or `'Separate'` |
| `Other Arrays Format` | String | `'Packed'` | `'Packed'`, `'None'`, or `'Unpacked'` |
| `WGS84` | Boolean | false | Export coordinates as WGS84 |

```ruby
options = {
  'Multiple Files' => true,
  'Coordinate Arrays Format' => 'None'
}
network.csv_export('C:/Badger/my_csv.csv', options)
```

---

### 02 csv_import
```ruby
network.csv_import(file, options) => void
```
`EXCHANGE`

Updates the network from a CSV file, with options similar to those in the user interface.

| Parameter | Type | Description |
|---|---|---|
| `file` | String | Path to the CSV file |
| `options` | Hash, nil | Options hash (see below), or nil for defaults |

**Options hash:**

| Key | Type | Default | Notes |
|---|---|---|---|
| `Force Link Rename` | Boolean | true | |
| `Flag Genuine Only` | Boolean | false | |
| `Load Null Fields` | Boolean | true | |
| `Update With Any Flag` | Boolean | true | false to only update fields with the update flag |
| `Use Asset ID` | Boolean | false | |
| `User Units` | Boolean | true | false for Native Units |
| `UK Dates` | Boolean | false | Import using UK date format |
| `Action` | String | `'Mixed'` | `'Mixed'`, `'Update And Add'`, `'Update Only'`, or `'Delete'` |
| `Header` | String | `'ID'` | `'ID'`, `'ID Description'`, `'ID Description Units'`, or `'ID Units'` |
| `New Flag` | String | nil | Flag used for new and updated data |
| `Update Flag` | String | nil | Only update fields with this flag if `Update With Any Flag` is false |

```ruby
options = {
  'Use Asset ID' => true,
  'New Flag' => 'NEW'
}
network.csv_import('C:/Badger/my_csv.csv', options)
```

---

### 03 odec_export_ex
```ruby
network.odec_export_ex(format, config, options, table, *args) => void
```
`EXCHANGE`

Exports network data using the Open Data Export Centre. The number of additional arguments depends on the format used.

Supported formats: `CSV`, `TSV`, `XML`, `MDB`, `SHP`, `TAB`, `GDB`, `ORACLE`, `SQLSERVER`

**Options hash:**

| Key | Type | Default | Notes |
|---|---|---|---|
| `Error File` | String | nil | |
| `Image Folder` | String | `''` | Asset Networks only |
| `Units Behaviour` | String | `'Native'` | `'Native'` or `'User'` |
| `Report Mode` | Boolean | false | Export in report mode |
| `Append` | Boolean | false | Append to existing data |
| `Export Selection` | Boolean | false | Export selected objects only |
| `Previous Version` | Integer | 0 | If not zero, exports differences |
| `Callback Class` | Ruby Class | nil | |
| `Create Primary Key` | Boolean | false | |
| `WGS84` | Boolean | false | Shapefile only |
| `Don't Update Geometry` | Boolean | false | |

---

#### 03a CSV (Comma Separated Values)
```ruby
network.odec_export_ex('CSV', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'CSV'` |
| `config` | String | Absolute path to field config file e.g. `'C:/Temp/ExportFields.cfg'` |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed e.g. `'CCTVSurvey'` |
| `file` | String | Absolute path to export file e.g. `'C:/Temp/Badger.csv'` |

---

#### 03b TSV (Tab Separated Values)
```ruby
network.odec_export_ex('TSV', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'TSV'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed |
| `file` | String | Absolute path to export file e.g. `'C:/Temp/Badger.tsv'` |

---

#### 03c XML (Extensible Markup Language)
```ruby
network.odec_export_ex('XML', config, options, table, feature_class, feature_dataset, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'XML'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed |
| `feature_class` | String | Name of the root element |
| `feature_dataset` | String | Name used for each data element |
| `file` | String | Absolute path to export file e.g. `'C:/Temp/Badger.xml'` |

---

#### 03d MDB (Jet / Microsoft Access Database)
```ruby
network.odec_export_ex('MDB', config, options, table, destination, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'MDB'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed |
| `destination` | String | Destination table in the database |
| `file` | String | Absolute path to database e.g. `'C:/Temp/Badger.mdb'` |

---

#### 03e SHP (ESRI Shapefile)
```ruby
network.odec_export_ex('SHP', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'SHP'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed |
| `file` | String | Absolute path to export file e.g. `'C:/Temp/Badger.shp'` |

---

#### 03f TAB (MapInfo TAB)
```ruby
network.odec_export_ex('TAB', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'TAB'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed |
| `file` | String | Absolute path to export file e.g. `'C:/Temp/Badger.tab'` |

---

#### 03g GDB (ESRI GeoDatabase)
```ruby
network.odec_export_ex('GDB', config, options, table, feature_class, feature_dataset, update, keyword, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'GDB'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed |
| `feature_class` | String | Name of the root element |
| `feature_dataset` | String | Name used for each data element |
| `update` | Boolean | If true the feature class must already exist |
| `keyword` | String, nil | ArcSDE configuration keyword, nil for personal or File GeoDatabases |
| `file` | String | Absolute path to export file e.g. `'C:/Temp/Badger.gdb'` |

---

#### 03h ORACLE (Oracle Database)
```ruby
network.odec_export_ex('ORACLE', config, options, table, destination, owner, update, username, password, connection_string)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'ORACLE'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed |
| `destination` | String | Destination table name |
| `owner` | String | Owner of the destination table |
| `update` | Boolean | |
| `username` | String | |
| `password` | String | |
| `connection_string` | String | |

---

#### 03i SQLSERVER (Microsoft SQL Server)
```ruby
network.odec_export_ex('SQLSERVER', config, options, table, destination, server, instance, database, update, trusted, username, password)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'SQLSERVER'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Table name with spaces removed |
| `destination` | String | Destination table in SQL Server |
| `server` | String | Server address e.g. `'localhost//SQLEXPRESS'` |
| `instance` | String, nil | SQL Server instance name, or nil |
| `database` | String | Name of the database |
| `update` | String | |
| `trusted` | Boolean | Use trusted connection / integrated security |
| `username` | String, nil | nil if using trusted connection |
| `password` | String, nil | nil if using trusted connection |

---

### 04 odic_import_ex
```ruby
network.odic_import_ex(format, config, options, table, *args) => void
```
`EXCHANGE`

Imports and updates network data using the Open Data Import Centre. The number of additional arguments depends on the format used.

Supported formats: `CSV`, `TSV`, `XML`, `MDB`, `SHP`, `TAB`, `GDB`, `ORACLE`, `SQLSERVER`

**Options hash:**

| Key | Type | Default | Notes |
|---|---|---|---|
| `Allow Multiple Asset IDs` | Boolean | false | |
| `Blob Merge` | Boolean | false | |
| `Callback Class` | Ruby Class | nil | |
| `Default Value Flag` | String | nil | Flag for fields set from default value |
| `Delete Missing Objects` | Boolean | false | |
| `Duplication Behaviour` | String | `'Merge'` | `'Overwrite'`, `'Merge'`, or `'Ignore'` |
| `Error File` | String | nil | Path of error file |
| `Group Name` | String | nil | Asset networks only |
| `Group Type` | String | nil | Asset networks only |
| `Image Folder` | String | nil | Asset networks only |
| `Import Images` | Boolean | false | Asset networks only |
| `Set Value Flag` | String | nil | Flag for fields set from data |
| `Units Behaviour` | String | `'Native'` | `'Native'`, `'User'`, or `'Custom'` |
| `Update Based On Asset ID` | Boolean | false | |
| `Update Links From Points` | Boolean | false | |
| `Update Only` | Boolean | false | |
| `Use Network Naming Conventions` | Boolean | false | |
| `Don't Update Geometry` | Boolean | false | |

> Note: when importing an RTK Hydrograph table, the destination table must be specified as `UnitHydrograph` not `RTKHydrograph`.

---

#### 04a CSV (Comma Separated Values)
```ruby
network.odic_import_ex('CSV', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'CSV'` |
| `config` | String | Absolute path to field config file e.g. `'C:/Temp/ImportFields.cfg'` |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed e.g. `'CCTVSurvey'` |
| `file` | String | Absolute path to import file e.g. `'C:/Badger/MyNodes.csv'` |

```ruby
network.odic_import_ex('CSV', 'C:/Badger/Config.cfg', nil, 'Node', 'C:/Badger/MyNodes.csv')
```

---

#### 04b TSV (Tab Separated Values)
```ruby
network.odic_import_ex('TSV', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'TSV'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed |
| `file` | String | Absolute path to import file e.g. `'C:/Badger/MyNodes.tsv'` |

```ruby
network.odic_import_ex('TSV', 'C:/Badger/Config.cfg', nil, 'Node', 'C:/Badger/MyNodes.tsv')
```

---

#### 04c XML (Extensible Markup Language)
```ruby
network.odic_import_ex('XML', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'XML'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed |
| `file` | String | Absolute path to import file e.g. `'C:/Badger/MyNodes.xml'` |

```ruby
network.odic_import_ex('XML', 'C:/Badger/Config.cfg', nil, 'Node', 'C:/Badger/MyNodes.xml')
```

---

#### 04d MDB (Jet / Microsoft Access Database)
```ruby
network.odic_import_ex('MDB', config, options, table, database, source)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'MDB'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed |
| `database` | String | Absolute path to the database |
| `source` | String | Table or stored SQL query in the database |

```ruby
network.odic_import_ex('MDB', 'C:/Badger/Config.cfg', nil, 'Node', 'C:/Badger/MyDatabase.mdb', 'MyNodes')
```

---

#### 04e SHP (ESRI Shapefile)
```ruby
network.odic_import_ex('SHP', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'SHP'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed |
| `file` | String | Absolute path to import file e.g. `'C:/Badger/MyNodes.shp'` |

```ruby
network.odic_import_ex('SHP', 'C:/Badger/Config.cfg', nil, 'Node', 'C:/Badger/MyNodes.shp')
```

---

#### 04f TAB (MapInfo TAB)
```ruby
network.odic_import_ex('TAB', config, options, table, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'TAB'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed |
| `file` | String | Absolute path to import file e.g. `'C:/Badger/MyNodes.tab'` |

```ruby
network.odic_import_ex('TAB', 'C:/Badger/Config.cfg', nil, 'Node', 'C:/Badger/MyNodes.tab')
```

---

#### 04g GDB (ESRI GeoDatabase)
```ruby
network.odic_import_ex('GDB', config, options, table, feature, file)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'GDB'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed |
| `feature` | String | Feature class to import from |
| `file` | String | Absolute path to import file e.g. `'C:/Badger/MyMap.gdb'` |

```ruby
network.odic_import_ex('GDB', 'C:/Badger/Config.cfg', nil, 'Node', 'GISNodes', 'C:/Badger/MyMap.gdb')
```

---

#### 04h ORACLE (Oracle Database)
```ruby
network.odic_import_ex('ORACLE', config, options, table, source, connection, owner, username, password)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'ORACLE'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed |
| `source` | String | Source table in the Oracle database |
| `connection` | String | Connection string e.g. `'//power/orcl'` |
| `owner` | String | Owner of the table being imported from |
| `username` | String | |
| `password` | String | |

```ruby
network.odic_import_ex('ORACLE', 'C:/Badger/Config.cfg', nil, 'Node', 'MyNodes', 'localhost/orcl', nil, 'username', 'badger1234')
```

---

#### 04i SQLSERVER (Microsoft SQL Server)
```ruby
network.odic_import_ex('SQLSERVER', config, options, table, source, server, instance, database, trusted, username, password)
```

| Parameter | Type | Description |
|---|---|---|
| `format` | String | `'SQLSERVER'` |
| `config` | String | Absolute path to field config file |
| `options` | Hash, nil | Options hash or nil |
| `table` | String | Destination table with spaces removed |
| `source` | String | Source table in SQL Server |
| `server` | String | Server address e.g. `'localhost//SQLEXPRESS'` |
| `instance` | String, nil | SQL Server instance name, or nil |
| `database` | String | Name of the database |
| `trusted` | Boolean | Use trusted connection / integrated security |
| `username` | String, nil | nil if using trusted connection |
| `password` | String, nil | nil if using trusted connection |

```ruby
network.odic_import_ex('SQLSERVER', 'C:/Badger/Config.cfg', nil, 'Node', 'MyNodes', 'localhost//SQLEXPRESS', nil, 'dbo.MyDatabase', nil, 'username', 'badger1234')
```

---

### 05 remove_local
```ruby
network.remove_local => void
```
`EXCHANGE`

Removes any local working copy of this network. Use this to free space in the working directory after processing is complete.
