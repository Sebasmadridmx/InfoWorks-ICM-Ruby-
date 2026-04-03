# WSOpenTSD

An open TSD object, allowing access to the timeseries data, similar to opening the TSD as a grid in the UI.

> **Note:** Dates and times in TSD are handled using the `DateTime` class provided by the Ruby standard library, if it is defined in the script. If `DateTime` is not available, the built-in `Time` class is used. Note that `DateTime` is deprecated in modern Ruby.

## Availability

| Context | Available |
|---------|-----------|
| EXCHANGE | Yes |
| UI | No |

---

## TSD Hashes

Several TSD objects are implemented as hashes of their properties. Conventions:

- `*` — Property must be set by the user when creating a new object.
- `+` — Property is set by the software and cannot be updated.
- Boolean, integer, and string values default to `false`, `0`, and `''` respectively and are not included in the returned hash if they have a default value.
- Properties omitted when updating an existing object retain their existing values after the update.

### Data Source

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `+dataSourceId` | `Integer` | | The data source ID. Only present if there is an ID (i.e. the data source has been saved). |
| `+index` | `Integer` | | The index of the data source. Only present if there is no ID (i.e. not yet saved). |
| `*streamName` | `String` | | The data source name. |
| `filename` | `String` | | Path to the telemetry database or folder. |
| `timeZone` | `String` | | Time zone of the data. |
| `+lastTimeSeriesUpdate` | `Time` | | UTC time that the data source was last updated. |
| `autoUpdateEnabled` | `Boolean` | | Not used in InfoWorks ICM. |
| `autoUpdateStartAt` | `Integer` | | Not used in InfoWorks ICM. |
| `autoUpdateInterval` | `Integer` | | Not used in InfoWorks ICM. |
| `autoUpdateTriggerFile` | `String` | | Not used in InfoWorks ICM. |
| `script` | `String` | | Absolute path and name of the script file, plus any script parameters, run at the start of the data update process. |
| `scriptTimeout` | `Integer` | | Interval after which the script is deemed to have failed (seconds). |
| `+lastModified` | `Time` | | Time that the data source was last modified. |
| `srcGeomMetadata` | `String` | | Spatial TSD only. |
| `fileCount` | `Integer` | | Spatial TSD only. |
| `projection` | `String` | | Spatial TSD only. |
| `areaOfInterest` | `Array` | | Spatial TSD only. Array of four Floats. |
| `logonType` | `Integer` | | Scalar TSD only. `0` = trusted, `1` = username/password. |
| `username` | `String` | | Scalar TSD only. Username for connecting to telemetry. |
| `password` | `String` | | Scalar TSD only. Password for connecting to telemetry. |
| `server` | `String` | | Scalar TSD only. Name of the server on which the telemetry database is stored. |
| `database` | `String` | | Scalar TSD only. Telemetry database, data server or URL. |
| `provider` | `Integer` | | Scalar TSD only. Database type: `-1` = Unknown, `0` = JET, `1` = Oracle, `2` = SQL Server 7, `3` = SQL Server, `4` = ODBC, `5` = PI, `6` = Simple CSV, `7` = SOPHIE (Pre), `8` = SANDRE (XMO), `9` = iHistorian, `10` = ClearSCADA, `11` = SQL Server (ODBC), `12` = JET (ACE), `13` = SCADAWatch, `14` = PI WebAPI, `15` = EA REST API, `16` = ADS Rest, `17` = Info360.com, `18` = Generic REST. |
| `netServiceName` | `String` | | Scalar TSD only. Net service name. |
| `creationUser` | `String` | | Scalar TSD only. Creation user. |
| `connectionString` | `String` | | Scalar TSD only. Connection string. |
| `commandTimeout` | `Integer` | | Scalar TSD only. Command timeout. |

### Data Stream

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `+streamId` | `Integer` | | The data stream ID. Only present if saved to the database. |
| `+index` | `Integer` | | The index of the stream. Only present if not yet saved. |
| `*streamType` | `Integer` | | `0` = observed, `1` = forecast, `2` = derived, `3` = stream type count. Cannot be changed after creation. |
| `*streamName` | `String` | | The stream name. |
| `+versionId` | `Integer` | | Version ID. |
| `dataInterval` | `Float` | | Data interval. |
| `+latestUpdate` | `Time` | | The time the stream was last updated. |
| `+latestData` | `Time` | | The time of the most recent data. |
| `exFactor` | `Float` | | Value factor. |
| `exTimeOffset` | `Float` | | Value offset. |
| `+isRefd` | `Boolean` | | Stream has been used in a simulation. |
| `+lastModified` | `Time` | | The time the stream was last modified. |
| `+recordCount` | `Integer` | | The number of entries on the stream. |
| `units` | `String` | | Scalar TSD only. Unit code for the physical quantity in the stream. |
| `exUpdateDisabled` | `Boolean` | | Scalar TSD only. External update disabled. |
| `exDataSourceId` | `Integer` | | Scalar TSD only. External data source. |
| `exUnits` | `String` | | Scalar TSD only. Units type. |
| `exOffset` | `Float` | | Scalar TSD only. Value offset. |
| `exMinThreshold` | `Float` | | Scalar TSD only. Min. threshold. |
| `exMaxThreshold` | `Float` | | Scalar TSD only. Max. threshold. |
| `exTable` | `String` | | Scalar TSD only. Name of the table in the telemetry database containing the live data feed. |
| `exDataColumn` | `String` | | Scalar TSD only. Data column. |
| `exTimeColumn` | `String` | | Scalar TSD only. Time column. |
| `exOriginTimeColumn` | `String` | | Scalar TSD only. Origin time column. |
| `exUserField1` | `String` | | Scalar TSD only. User field 1. |
| `exUserVal1` | `String` | | Scalar TSD only. User value 1. |
| `exUserField2` | `String` | | Scalar TSD only. User field 2. |
| `exUserVal2` | `String` | | Scalar TSD only. User value 2. |
| `exUserField3` | `String` | | Scalar TSD only. User field 3. |
| `exUserVal3` | `String` | | Scalar TSD only. User value 3. |
| `x` | `Float` | | Scalar TSD only. |
| `y` | `Float` | | Scalar TSD only. |
| `lookupId` | `Integer` | | Scalar TSD only. ID of lookup used to transform imported data. |
| `tagName` | `String` | | Scalar TSD only. Tag name. |
| `description` | `String` | | Scalar TSD only. Description. |

### Data Value

Time series data values are hashes containing the following properties. Note that existing properties are not preserved when updating a data value.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `*t` | `Time` | | Timestamp of the value, or of the forecast origin (for forecast series). |
| `+tOrigin` | `Time` | | Forecast value only. Timestamp of the origin of this forecast value. |
| `exclude` | `Boolean` | | Value is not to be used in simulation. |
| `readonly` | `Boolean` | | Value is not to be updated by automated update (not used in InfoWorks ICM). |
| `geomKey` | `String` | | Spatial TSD only. Uniquely identifies the geometry of the spatial data. |
| `flag` | `String` | | Flag. |
| `value` | `Double` | | Scalar TSD only. The value. Not present if this is a forecast origin. May be missing (null value). |
| `values` | `Array` | | Spatial TSD only. Array of values. May be missing (null value). |

### Lookup

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `+lookupId` | `Integer` | | The lookup ID. Only present if saved to the database. |
| `+index` | `Integer` | | The index of the lookup. Only present if not yet saved. |
| `*lookupName` | `String` | | The lookup name. |
| `+lastModified` | `Time` | | The time the lookup was last modified. |
| `map` | `Hash<String, String>` | | The lookup mapping. |

### User Edit

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `+userEditId` | `Integer` | | The user edit ID. |
| `*userEditName` | `String` | | The name of the user edit. |
| `+applied` | `Boolean` | | Whether the user edit has been permanently applied to the stream. |
| `shared` | `Boolean` | | Set if the user edit is available for use by other users (always `true` in InfoWorks ICM). |
| `+locked` | `Boolean` | | Set if the user edit has been used in a simulation. |
| `+userName` | `String` | | Name of the user who created the user edit. |
| `comment` | `String` | | Description or other comment on the user edit. |
| `*userEditStream` | `String` | | ID of the data stream to which the edit relates. Cannot be changed. |

### Geometry

A geometry (Spatial TSD only) is a hash containing parameters and point coordinates relating to the geometry of spatial data. It can be copied, but is not intended for external construction or manipulation.

---

## Methods Summary

| # | Method | Return Type | Availability |
|---|--------|-------------|--------------|
| 01 | [data_sources_count](#01-data_sources_count) | `Integer` | EXCHANGE |
| 02 | [data_source_by_id](#02-data_source_by_id) | `Hash<String, Any>` | EXCHANGE |
| 03 | [data_source_by_index](#03-data_source_by_index) | `Hash<String, Any>` | EXCHANGE |
| 04 | [data_source_by_name](#04-data_source_by_name) | `Hash<String, Any>` | EXCHANGE |
| 05 | [data_source_delete](#05-data_source_delete) | `void` | EXCHANGE |
| 06 | [data_source_new](#06-data_source_new) | `Hash<String, Any>` | EXCHANGE |
| 07 | [data_source_update](#07-data_source_update) | `Hash<String, Any>` | EXCHANGE |
| 08 | [forecast_data_add](#08-forecast_data_add) | `void` | EXCHANGE |
| 09 | [forecast_data_get](#09-forecast_data_get) | `Array<String, Any>` | EXCHANGE |
| 10 | [forecast_origins_get](#10-forecast_origins_get) | `Array<String, Any>` | EXCHANGE |
| 11 | [geometry_get](#11-geometry_get) | `Hash` | EXCHANGE |
| 12 | [geometry_set](#12-geometry_set) | `void` | EXCHANGE |
| 13 | [lookups_count](#13-lookups_count) | `Integer` | EXCHANGE |
| 14 | [lookup_by_id](#14-lookup_by_id) | `Hash<String, Any>` | EXCHANGE |
| 15 | [lookup_by_index](#15-lookup_by_index) | `Hash<String, Any>` | EXCHANGE |
| 16 | [lookup_by_name](#16-lookup_by_name) | `Hash<String, Any>` | EXCHANGE |
| 17 | [lookup_delete](#17-lookup_delete) | `void` | EXCHANGE |
| 18 | [lookup_new](#18-lookup_new) | `Hash<String, Any>` | EXCHANGE |
| 19 | [lookup_update](#19-lookup_update) | `Hash<String, Any>` | EXCHANGE |
| 20 | [streams_count](#20-streams_count) | `Integer` | EXCHANGE |
| 21 | [streams_load](#21-streams_load) | `void` | EXCHANGE |
| 22 | [streams_save](#22-streams_save) | `void` | EXCHANGE |
| 23 | [stream_by_id](#23-stream_by_id) | `Hash<String, Any>` | EXCHANGE |
| 24 | [stream_by_index](#24-stream_by_index) | `Hash<String, Any>` | EXCHANGE |
| 25 | [stream_by_name](#25-stream_by_name) | `Hash<String, Any>` | EXCHANGE |
| 26 | [stream_delete](#26-stream_delete) | `void` | EXCHANGE |
| 27 | [stream_new](#27-stream_new) | `Hash<String, Any>` | EXCHANGE |
| 28 | [stream_update](#28-stream_update) | `Hash<String, Any>` | EXCHANGE |
| 29 | [time_series_data_add](#29-time_series_data_add) | `void` | EXCHANGE |
| 30 | [time_series_data_get](#30-time_series_data_get) | `Array<Data>` | EXCHANGE |
| 31 | [user_edit_data_get](#31-user_edit_data_get) | `Array<Data>` | EXCHANGE |
| 32 | [user_edit_data_update](#32-user_edit_data_update) | `void` | EXCHANGE |
| 33 | [user_edits](#33-user_edits) | `Array<Hash>` | EXCHANGE |
| 34 | [user_edit_apply](#34-user_edit_apply) | `void` | EXCHANGE |
| 35 | [user_edit_by_id](#35-user_edit_by_id) | `Hash` | EXCHANGE |
| 36 | [user_edit_by_name](#36-user_edit_by_name) | `Hash` | EXCHANGE |
| 37 | [user_edit_delete](#37-user_edit_delete) | `void` | EXCHANGE |
| 38 | [user_edit_new](#38-user_edit_new) | `void` | EXCHANGE |
| 39 | [user_edit_update](#39-user_edit_update) | `Hash` | EXCHANGE |

---

## Method Details

### 01. data_sources_count

```ruby
#data_sources_count(type) ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the number of data sources in the TSD.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | | Type of data source. |

#### Return Value

`Integer` — Number of data sources in the TSD.

---

### 02. data_source_by_id

```ruby
#data_source_by_id(ID) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the data source with the specified ID.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the data source to be returned. |

#### Return Value

`Hash` — The data source.

---

### 03. data_source_by_index

```ruby
#data_source_by_index(index) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the data source with the specified index.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| index | `Integer` | Index of the data source to be returned. |

#### Return Value

`Hash` — The data source.

---

### 04. data_source_by_name

```ruby
#data_source_by_name(name) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the data source with the specified name.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | Name of the data source to be returned. |

#### Return Value

`Hash` — The data source.

---

### 05. data_source_delete

```ruby
#data_source_delete(ID) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Deletes the data source with the specified ID.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the data source to be deleted. |

#### Return Value

`void`

---

### 06. data_source_new

```ruby
#data_source_new(Name) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new data source with the specified name.

An exception is thrown if the TSD is a spatial TSD and already has a data source, or if the TSD is a scalar TSD and a data source with the supplied name already exists.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Name | `String` | Name for the new data source. |

#### Return Value

`Hash` — The data source.

---

### 07. data_source_update

```ruby
#data_source_update(Source) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Finds the data source with the ID (or index if there is no ID) supplied in the Source hash, and updates it with the properties of the Source.

An exception is thrown if the name supplied in the hash is the same as the name of a different, existing data source.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Source | `Hash` | The new properties of the data source. |

#### Return Value

`Hash` — The updated data source.

---

### 08. forecast_data_add

```ruby
#forecast_data_add(ID, origin, flag, data, comment) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Adds forecast data to the specified data stream. The data should be passed as an array of Data Value hashes. Note that `tOrigin` must not be set in these hashes.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the data stream. |
| origin | `Time` | Forecast origin of the data. |
| flag | `String` | Flag to be assigned to all added data values. |
| data | `Array` | Array of data values to be added. |

#### Return Value

`void`

---

### 09. forecast_data_get

```ruby
#forecast_data_get(ID, origin) ⇒ Array<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Gets forecast data from the specified data stream as an array of Data Value hashes.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the data stream. |
| origin | `Time` | Forecast origin of the data. |

#### Return Value

`Array` — Forecast data values.

---

### 10. forecast_origins_get

```ruby
#forecast_origins_get(ID, from, to, options) ⇒ Array<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Gets forecast origins in the given period from the specified data stream.

**`options` hash keys:**

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `inclusive` | `Boolean` | `true` | Whether to include the `from` and `to` time points in the returned values, if present. |
| `limit` | `Integer` | `0` | Limit on number of values to be returned. `0` for no limit. |
| `versionId` | `Integer` | `0` | TSD version for which results are to be returned. `0` for latest. |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the data stream. |
| from | `Time`, `String` | From time, or string `'min'` for minimum possible time. |
| to | `Time`, `String` | To time, or string `'max'` for maximum possible time. |
| options | `Hash` | Hash of options. See description. |

#### Return Value

`Array` — Forecast origin data.

---

### 11. geometry_get

```ruby
#geometry_get(key) ⇒ Hash
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Gets a Geometry as a hash. Spatial TSD only.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| key | `String` | The geometry key. |

#### Return Value

`Hash` — Geometry hash.

---

### 12. geometry_set

```ruby
#geometry_set(key, geometry) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Sets geometry from a geometry hash. Spatial TSD only.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| key | `String` | The geometry key. |
| geometry | `Hash` | Geometry hash. |

#### Return Value

`void`

---

### 13. lookups_count

```ruby
#lookups_count() ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the number of lookups in the TSD.

#### Return Value

`Integer` — Number of lookups in the TSD.

---

### 14. lookup_by_id

```ruby
#lookup_by_id(id) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the lookup specified by the ID.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the lookup. |

#### Return Value

`Hash` — The lookup.

---

### 15. lookup_by_index

```ruby
#lookup_by_index(index) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the lookup with the specified index.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| index | `Integer` | Index of the lookup to be returned. |

#### Return Value

`Hash` — The lookup.

---

### 16. lookup_by_name

```ruby
#lookup_by_name(name) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the lookup with the specified name.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | Name of the lookup to be returned. |

#### Return Value

`Hash` — The lookup.

---

### 17. lookup_delete

```ruby
#lookup_delete(ID) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Deletes the lookup with the specified ID.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the lookup to be deleted. |

#### Return Value

`void`

---

### 18. lookup_new

```ruby
#lookup_new(Name) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new lookup with the specified name.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Name | `String` | Name for the new lookup. |

#### Return Value

`Hash` — The lookup.

---

### 19. lookup_update

```ruby
#lookup_update(Source) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Finds the lookup with the ID (or index if there is no ID) supplied in the Source hash, and updates it with the properties of the Source.

An exception is thrown if the name supplied in the hash is the same as the name of a different, existing lookup.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Source | `Hash` | The new properties of the lookup. |

#### Return Value

`Hash` — The updated lookup.

---

### 20. streams_count

```ruby
#streams_count(type) ⇒ Integer
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the number of data streams of the given type in the TSD.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| type | `Integer` | `0` = observed streams, `1` = forecast streams. |

#### Return Value

`Integer` — Number of streams.

---

### 21. streams_load

```ruby
#streams_load(version) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Loads the TSD at the specified version from the database. This is required before accessing or editing the data. A version of `0` indicates that the current version should be loaded.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| version | `Integer` | Database version, or `0` for latest. |

#### Return Value

`void`

---

### 22. streams_save

```ruby
#streams_save(comment) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Saves the updated data streams, sources, and lookups to the database.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| comment | `String` | Comment to attach. |

#### Return Value

`void`

---

### 23. stream_by_id

```ruby
#stream_by_id(id) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the properties of the data stream with the given ID as a hash.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| id | `Integer` | ID of the data stream. |

#### Return Value

`Hash` — The data stream.

---

### 24. stream_by_index

```ruby
#stream_by_index(index) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the data stream with the specified index.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| index | `Integer` | Index of the data stream to be returned. |

#### Return Value

`Hash` — The data stream.

---

### 25. stream_by_name

```ruby
#stream_by_name(name) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the data stream with the specified name.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| name | `String` | Name of the data stream to be returned. |

#### Return Value

`Hash` — The data stream.

---

### 26. stream_delete

```ruby
#stream_delete(ID) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Deletes the data stream with the specified ID.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the data stream to be deleted. |

#### Return Value

`void`

---

### 27. stream_new

```ruby
#stream_new(Name) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new data stream with the specified name.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Name | `String` | Name for the new data stream. |

#### Return Value

`Hash` — The data stream.

---

### 28. stream_update

```ruby
#stream_update(Source) ⇒ Hash<String, Any>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Finds the data stream with the ID (or index if there is no ID) supplied in the Source hash, and updates it with the properties of the Source.

An exception is thrown if the name supplied in the hash is the same as the name of a different, existing data source.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Source | `Hash` | The new properties of the data stream. |

#### Return Value

`Hash` — The updated data stream.

---

### 29. time_series_data_add

```ruby
#time_series_data_add(ID, data, comment) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Adds time series data to the specified data stream. The data should be passed as an array of Data Value hashes.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the data stream. |
| data | `Array` | Data values to be added. |
| comment | `String` | Comment to be associated with the data. |

#### Return Value

`void`

---

### 30. time_series_data_get

```ruby
#time_series_data_get(ID, from, to, options) ⇒ Array<Data>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Gets time series data from the specified data stream as an array of Data Value hashes. For forecast data, only one value is returned for any given timestamp, representing the value with the latest time origin (most recent forecast for that time).

**Range options:**

| Range | Description |
|-------|-------------|
| `"inside"` | Data at times strictly inside `from` and `to` (not including the endpoints). |
| `"between"` | Data at times between `from` and `to`, including those time points if they exist. |
| `"outside"` | Data between `from` and `to`, plus the time points immediately before the start and after the end, if they exist. |

**`options` hash keys:**

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `range` | `String` | `"between"` | One of `"between"`, `"inside"`, `"outside"`, or `nil`. |
| `limit` | `Integer` | `0` | Limit on the number of values to be returned. `0` for no limit. |
| `versionId` | `Integer` | `0` | Version of the TSD from which values are returned. `0` for latest. |
| `userEditIds` | `Array` | | Optional. User edits to apply to the returned values. |
| `futureExclude` | `Time` | | Optional. Exclude data values from the nominal future of the specified time. |
| `ref` | `String` | | Optional. Reference value for a simulation in which this data is to be used. Sets the `refd` property of the stream to `true`. |

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the data stream. |
| from | `Time`, `String` | From time, or string `'min'` for minimum possible time. |
| to | `Time`, `String` | To time, or string `'max'` for maximum possible time. |
| options | `Hash` | Optional hash of options. See description. |

#### Return Value

`Array<Data>` — Data values.

---

### 31. user_edit_data_get

```ruby
#user_edit_data_get(ID, from, to, options) ⇒ Array<Data>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Gets data from the specified user edit as an array of Data Value hashes.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the user edit. |
| from | `Time`, `String` | From time, or string `'min'` for minimum possible time. |
| to | `Time`, `String` | To time, or string `'max'` for maximum possible time. |

#### Return Value

`Array<Data>` — User edit data values.

---

### 32. user_edit_data_update

```ruby
#user_edit_data_update(ID, add, remove) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Adds data to or removes data from the specified user edit.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the user edit. |
| add | `Array` | Array of data values to be added. |
| remove | `Array` | Array of timestamps of data to be removed. |

#### Return Value

`void`

---

### 33. user_edits

```ruby
#user_edits(ID, from, to) ⇒ Array<Hash>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Gets the current user's user edits from the specified data stream as an array of user edit hashes, sorted by name.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the user edit. |
| from | `Time`, `String` | From time, or string `'min'` for minimum possible time. |
| to | `Time`, `String` | To time, or string `'max'` for maximum possible time. |

#### Return Value

`Array<Hash>` — Array of user edits.

---

### 34. user_edit_apply

```ruby
#user_edit_apply(ID, readonly) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Applies the specified user edit to the data stream that it is associated with.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the user edit. |
| readonly | `Boolean` | Whether to mark the edited data as readonly. |

#### Return Value

`void`

---

### 35. user_edit_by_id

```ruby
#user_edit_by_id(ID) ⇒ Hash
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Retrieves the specified user edit as a user edit hash.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the user edit. |

#### Return Value

`Hash` — The user edit.

---

### 36. user_edit_by_name

```ruby
#user_edit_by_name(Name) ⇒ Hash
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Retrieves the specified user edit as a user edit hash.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Name | `String` | Name of the user edit. |

#### Return Value

`Hash` — The user edit.

---

### 37. user_edit_delete

```ruby
#user_edit_delete(ID) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Deletes the specified user edit.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| ID | `Integer` | ID of the user edit. |

#### Return Value

`void`

---

### 38. user_edit_new

```ruby
#user_edit_new(Name, StreamID, shared) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new user edit. Throws an exception if an edit with the specified name already exists.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Name | `String` | Name for the user edit. |
| StreamID | `Integer` | ID of the data stream that the edit is to be associated with. |
| shared | `Boolean` | Whether the user edit should be shared for use by other users. Should be set to `true` to be consistent with normal InfoWorks ICM usage. |

#### Return Value

`void`

---

### 39. user_edit_update

```ruby
#user_edit_update(Edit) ⇒ Hash
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Updates the user edit with the name, comment, and shared properties from the hash.

Throws an exception if the ID is missing or invalid, doesn't match an existing edit, or if a different edit has the same name.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| Edit | `Hash` | The user edit hash with updated properties. |

#### Return Value

`Hash` — The updated user edit.
