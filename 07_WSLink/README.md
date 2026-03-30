# WSLink

Inherits from: `WSRowObject`

A link object, i.e. a `WSRowObject` with a `category` type of `link`.

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
| 01 | [ds_node](#01-ds_node) | `WSNode?` | EXCHANGE, UI |
| 02 | [us_node](#02-us_node) | `WSNode?` | EXCHANGE, UI |

---

## Method Details

### 01 ds_node
```ruby
link.ds_node => WSNode?
```
`EXCHANGE` `UI`

Returns the link's downstream node, or nil if it doesn't have one.

```ruby
node = link.ds_node
puts node.id unless node.nil?
```

---

### 02 us_node
```ruby
link.us_node => WSNode?
```
`EXCHANGE` `UI`

Returns the link's upstream node, or nil if it doesn't have one.

```ruby
node = link.us_node
puts node.id unless node.nil?
```
