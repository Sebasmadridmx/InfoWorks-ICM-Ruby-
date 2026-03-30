# WSCommit

A single commit to a `WSModelObject` using merge version control.

All methods in this class are **read only** and return the value of one of the fields that appears in the commit grid.

---

## Availability

| Tag | Meaning |
|---|---|
| `EXCHANGE` | Available in Exchange scripts |

---

## Methods

| # | Method | Returns | Available |
|---|---|---|---|
| 01 | [branch_id](#01-branch_id) | `Integer` | EXCHANGE |
| 02 | [comment](#02-comment) | `String` | EXCHANGE |
| 03 | [commit_id](#03-commit_id) | `Integer` | EXCHANGE |
| 04 | [date](#04-date) | `DateTime` | EXCHANGE |
| 05 | [deleted_count](#05-deleted_count) | `Integer` | EXCHANGE |
| 06 | [inserted_count](#06-inserted_count) | `Integer` | EXCHANGE |
| 07 | [modified_count](#07-modified_count) | `Integer` | EXCHANGE |
| 08 | [setting_changed_count](#08-setting_changed_count) | `Integer` | EXCHANGE |
| 09 | [user](#09-user) | `String` | EXCHANGE |

---

## Method Details

### 01 branch_id
```ruby
commit.branch_id => Integer
```
`EXCHANGE`

Returns the branch ID.

---

### 02 comment
```ruby
commit.comment => String
```
`EXCHANGE`

Returns any comment associated with this commit. Comments are optional, so this may be an empty string.

---

### 03 commit_id
```ruby
commit.commit_id => Integer
```
`EXCHANGE`

Returns the commit ID.

---

### 04 date
```ruby
commit.date => DateTime
```
`EXCHANGE`

Returns the date of the commit.

---

### 05 deleted_count
```ruby
commit.deleted_count => Integer
```
`EXCHANGE`

Returns the number of objects that were deleted in this commit.

---

### 06 inserted_count
```ruby
commit.inserted_count => Integer
```
`EXCHANGE`

Returns the number of objects that were inserted in this commit.

---

### 07 modified_count
```ruby
commit.modified_count => Integer
```
`EXCHANGE`

Returns the number of objects that were modified in this commit.

---

### 08 setting_changed_count
```ruby
commit.setting_changed_count => Integer
```
`EXCHANGE`

Returns the number of settings that were changed in this commit.

> Note: the method name uses `setting` not `settings`.

---

### 09 user
```ruby
commit.user => String
```
`EXCHANGE`

Returns the username associated with this commit.
