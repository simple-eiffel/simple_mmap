# S04: FEATURE SPECIFICATIONS - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## SIMPLE_MMAP Features

### Creation Features

| Feature | Type | Description |
|---------|------|-------------|
| make_from_file | Creation | Map file at path (read or read-write) |
| make_anonymous | Creation | Create pagefile-backed mapping |
| make_shared | Creation | Create/open named shared mapping |
| open_shared | Creation | Open existing shared mapping |

### Status Features

| Feature | Type | Description |
|---------|------|-------------|
| is_valid | Query | Is mapping valid and usable? |
| is_writable | Query | Is mapping writable? |
| size | Query | Size of mapping in bytes |
| last_error | Query | Error message from last failed operation |

### Read Features

| Feature | Type | Description |
|---------|------|-------------|
| read_byte | Query | Read single byte at offset |
| read_integer | Query | Read 32-bit integer at offset |
| read_bytes | Query | Read array of bytes |
| read_string | Query | Read null-terminated string |

### Write Features

| Feature | Type | Description |
|---------|------|-------------|
| write_byte | Command | Write single byte at offset |
| write_integer | Command | Write 32-bit integer at offset |
| write_bytes | Command | Write array of bytes |
| write_string | Command | Write null-terminated string |

### Operation Features

| Feature | Type | Description |
|---------|------|-------------|
| flush | Command | Flush changes to disk |
| close | Command | Close and release mapping |

### Status Report Features

| Feature | Type | Description |
|---------|------|-------------|
| last_write_count | Query | Bytes written in last write operation |
| last_flush_succeeded | Query | Did last flush succeed? |

## C External Features (Private)

| Feature | C Function | Purpose |
|---------|------------|---------|
| c_smm_create_file_mapping | smm_create_file_mapping | Create file mapping |
| c_smm_create_anonymous_mapping | smm_create_anonymous_mapping | Create anonymous mapping |
| c_smm_create_shared_mapping | smm_create_shared_mapping | Create shared mapping |
| c_smm_open_shared_mapping | smm_open_shared_mapping | Open shared mapping |
| c_smm_get_data | smm_get_data | Get data pointer |
| c_smm_get_size | smm_get_size | Get mapping size |
| c_smm_read | smm_read | Bulk read |
| c_smm_write | smm_write | Bulk write |
| c_smm_read_byte | smm_read_byte | Read single byte |
| c_smm_write_byte | smm_write_byte | Write single byte |
| c_smm_read_int32 | smm_read_int32 | Read 32-bit int |
| c_smm_write_int32 | smm_write_int32 | Write 32-bit int |
| c_smm_flush | smm_flush | Flush to disk |
| c_smm_is_valid | smm_is_valid | Check validity |
| c_smm_is_writable | smm_is_writable | Check writable |
| c_smm_get_error | smm_get_error | Get error message |
| c_smm_close | smm_close | Close mapping |
