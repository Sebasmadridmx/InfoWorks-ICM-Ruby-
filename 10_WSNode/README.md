# WSNode

**Inherits from:** `WSRowObject` > `WSNode`

A node object.

## Availability

| Context | Available |
|---------|-----------|
| EXCHANGE | Yes |
| UI | Yes |

---

## Methods Summary

| # | Method | Return Type | Availability |
|---|--------|-------------|--------------|
| 01 | [ds_links](#01-ds_links) | `WSRowObjectCollection<WSLink>` | EXCHANGE, UI |
| 02 | [us_links](#02-us_links) | `WSRowObjectCollection<WSLink>` | EXCHANGE, UI |

---

## Method Details

### 01. ds_links

```ruby
#ds_links ⇒ WSRowObjectCollection<WSLink>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns a collection of the node's downstream links. If there are no downstream links the collection will be empty.

#### Return Value

`WSRowObjectCollection<WSLink>`

---

### 02. us_links

```ruby
#us_links ⇒ WSRowObjectCollection<WSLink>
```

![EXCHANGE](https://img.shields.io/badge/EXCHANGE-blue) ![UI](https://img.shields.io/badge/UI-green)

Returns a collection of the node's upstream links. If there are no upstream links the collection will be empty.

#### Return Value

`WSRowObjectCollection<WSLink>`
