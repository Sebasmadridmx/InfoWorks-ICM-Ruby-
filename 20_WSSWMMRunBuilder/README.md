# WSSWMMRunBuilder

Used to create and modify SWMM runs. Runs can be created using an existing run as a template, or created from scratch by setting all of the required parameters.

You can create an instance using the `#new` method and call the remaining methods.

## Availability

| Context | Available |
|---------|-----------|
| ![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) | Yes |
| ![UI](https://img.shields.io/badge/UI-green) | No |

---

## Methods Summary

| # | Method | Returns | Availability |
|---|--------|---------|--------------|
| 01 | [[] (Get Key)](#01-get-key) | `Any` | EXCHANGE |
| 02 | [[]= (Set Key)](#02-set-key) | `void` | EXCHANGE |
| 03 | [create_new_run](#03-create_new_run) | `Boolean` | EXCHANGE |
| 04 | [get_run_mo](#04-get_run_mo) | `WSRun?` | EXCHANGE |
| 05 | [list_parameters](#05-list_parameters) | `Array<String>` | EXCHANGE |
| 06 | [load](#06-load) | `Boolean` | EXCHANGE |
| 07 | [new](#07-new) | `WSSWMMRunBuilder` | EXCHANGE |
| 08 | [validate](#08-validate) | `Boolean` | EXCHANGE |

---

## Method Details

### 01. [] (Get Key)

```ruby
#[(key)] ⇒ Any
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Gets the value of a named run parameter.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `key` | `String` | The name of the run parameter. |

#### Returns

`Any` — The value of the named run parameter.

---

### 02. []= (Set Key)

```ruby
#[(key)]=(value) ⇒ void
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Sets the value of a named run parameter.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `key` | `String` | The name of the run parameter. |
| `value` | `Any` | The value to set for the parameter. |

#### Returns

`void`

---

### 03. create_new_run

```ruby
#create_new_run(run_group_id) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new run in the specified run group, using the currently set parameters.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `run_group_id` | `Integer` | The ID of a run group. |

#### Returns

`Boolean` — `true` if the run was created successfully.

---

### 04. get_run_mo

```ruby
#get_run_mo ⇒ WSRun?
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns the `WSModelObject` associated with the most recent call to either `#load`, `#create_new_run`, or `#save`.

#### Returns

`WSRun?` — The model object for the most recently loaded or created run, or `nil` if none.

---

### 05. list_parameters

```ruby
#list_parameters ⇒ Array<String>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Returns a list of available run parameters.

> **Note:** This is for information only. It does not return the current value of any parameter. The available parameters will be the same for all runs.

#### Returns

`Array<String>` — An array of available run parameter names.

---

### 06. load

```ruby
#load(run) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Loads the parameters from an existing run.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `run` | `Integer`, `String`, `WSModelObject` | The ID, scripting path, or a `WSModelObject` of the correct type (run). |

#### Returns

`Boolean` — `true` if the run was successfully loaded.

---

### 07. new

```ruby
#new ⇒ WSSWMMRunBuilder
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Creates a new instance of this class.

#### Returns

`WSSWMMRunBuilder` — A new instance of `WSSWMMRunBuilder`.

---

### 08. validate

```ruby
#validate(file) ⇒ Boolean
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue)

Validates the current run parameters, saving any validation errors to the specified file.

#### Parameters

| Name | Type | Description |
|------|------|-------------|
| `file` | `String` | Path to a text file where validation errors will be saved. |

#### Returns

`Boolean` — `true` if validation was successful with no errors.

---

*Documentation generated from the official Autodesk InfoWorks ICM 2025 help pages.*
