# S03: CONTRACTS - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Creation Contracts

### make_from_file (a_path: READABLE_STRING_GENERAL; a_writable: BOOLEAN)
```eiffel
require
  path_not_empty: not a_path.is_empty
```

### make_anonymous (a_size: INTEGER)
```eiffel
require
  positive_size: a_size > 0
```

### make_shared (a_name: READABLE_STRING_GENERAL; a_size: INTEGER)
```eiffel
require
  name_not_empty: not a_name.is_empty
  positive_size: a_size > 0
```

### open_shared (a_name: READABLE_STRING_GENERAL)
```eiffel
require
  name_not_empty: not a_name.is_empty
```

## Read Operation Contracts

### read_byte (a_offset: INTEGER): NATURAL_8
```eiffel
require
  valid: is_valid
  valid_offset: a_offset >= 0 and a_offset < size
```

### read_integer (a_offset: INTEGER): INTEGER
```eiffel
require
  valid: is_valid
  valid_offset: a_offset >= 0 and a_offset + 4 <= size
```

### read_bytes (a_offset, a_count: INTEGER): ARRAY [NATURAL_8]
```eiffel
require
  valid: is_valid
  valid_offset: a_offset >= 0
  positive_count: a_count > 0
  in_bounds: a_offset + a_count <= size
```

### read_string (a_offset, a_max_length: INTEGER): STRING_8
```eiffel
require
  valid: is_valid
  valid_offset: a_offset >= 0
  positive_length: a_max_length > 0
```

## Write Operation Contracts

### write_byte (a_offset: INTEGER; a_value: NATURAL_8)
```eiffel
require
  valid: is_valid
  writable: is_writable
  valid_offset: a_offset >= 0 and a_offset < size
```

### write_integer (a_offset: INTEGER; a_value: INTEGER)
```eiffel
require
  valid: is_valid
  writable: is_writable
  valid_offset: a_offset >= 0 and a_offset + 4 <= size
```

### write_bytes (a_offset: INTEGER; a_bytes: ARRAY [NATURAL_8])
```eiffel
require
  valid: is_valid
  writable: is_writable
  valid_offset: a_offset >= 0
  bytes_not_empty: not a_bytes.is_empty
  in_bounds: a_offset + a_bytes.count <= size
```

### write_string (a_offset: INTEGER; a_string: READABLE_STRING_8)
```eiffel
require
  valid: is_valid
  writable: is_writable
  valid_offset: a_offset >= 0
  string_not_empty: not a_string.is_empty
  in_bounds: a_offset + a_string.count + 1 <= size
```

## Other Contracts

### flush
```eiffel
require
  valid: is_valid
```

### close
```eiffel
ensure
  closed: handle = default_pointer
```

## Class Invariant

```eiffel
invariant
  handle_default_implies_invalid: handle = default_pointer implies not is_valid
```
