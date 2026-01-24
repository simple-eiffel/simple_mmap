# S02: CLASS CATALOG - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Core Classes

### SIMPLE_MMAP
- **Purpose**: Memory-mapped file and shared memory access
- **Role**: Single facade for all mapping operations
- **Key Features**:
  - File mapping (read-only or read-write)
  - Anonymous mapping (pagefile-backed)
  - Named shared memory (IPC)
  - Typed read/write operations
  - Flush and close operations

## Creation Procedures

| Procedure | Purpose |
|-----------|---------|
| make_from_file | Map existing file |
| make_anonymous | Create pagefile-backed region |
| make_shared | Create or open named shared mapping |
| open_shared | Open existing named shared mapping |

## Class Design

### Handle-Based Architecture
```
SIMPLE_MMAP
    |
    +-- handle: POINTER (C structure)
          |
          +-- smm_mapping (C struct)
                - file_handle
                - mapping_handle
                - data_pointer
                - size
                - is_writable
                - error_message
```

### C Wrapper Functions
All operations delegate to C functions via inline externals:
- smm_create_file_mapping
- smm_create_anonymous_mapping
- smm_create_shared_mapping
- smm_open_shared_mapping
- smm_read / smm_write
- smm_read_byte / smm_write_byte
- smm_read_int32 / smm_write_int32
- smm_flush
- smm_close
- smm_is_valid / smm_is_writable
- smm_get_size / smm_get_error

## Design Patterns

### Facade Pattern
- SIMPLE_MMAP hides C complexity
- Single class for all operations

### Handle Pattern
- Opaque handle to C structure
- All operations require valid handle
