# WSCommits

A collection of `WSCommit` objects, representing the commit history of a `WSModelObject` using merge version control.

---

## Availability

| Tag | Meaning |
|---|---|
| `EXCHANGE` | Available in Exchange scripts |

---

## Methods

| # | Method | Returns | Available |
|---|---|---|---|
| 01 | [get_index](#01-get_index) | `WSCommit?` | EXCHANGE |
| 02 | [each](#02-each) | `WSCommit` | EXCHANGE |
| 03 | [length](#03-length) | `Integer` | EXCHANGE |

---

## Method Details

### 01 get_index
```ruby
commits[index] => WSCommit?
```
`EXCHANGE`

Returns the `WSCommit` from the collection at the specified index.

| Parameter | Type | Description |
|---|---|---|
| `index` | Integer | The index requested (zero-based) |
| **Returns** | WSCommit, nil | nil if there is no object at that index |

```ruby
commit = commits[0]
puts commit.branch_id
```

---

### 02 each
```ruby
commits.each { |c| ... } => WSCommit
```
`EXCHANGE`

Iterates through the collection, yielding each `WSCommit`.

```ruby
commits.each { |c| puts c.branch_id }

commits.each do |c|
  puts "#{c.branch_id} - User '#{c.user}' changed #{c.modified_count} objects!"
end
```

---

### 03 length
```ruby
commits.length => Integer
```
`EXCHANGE`

Returns the number of `WSCommit` objects in this collection.

```ruby
puts commits.length
```
