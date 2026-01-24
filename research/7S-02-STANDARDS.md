# 7S-02: STANDARDS - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Applicable Standards

### Win32 Memory Mapping API
- **Source**: Microsoft Win32 API
- **Functions Used**:
  - CreateFileMapping
  - MapViewOfFile
  - UnmapViewOfFile
  - FlushViewOfFile
  - OpenFileMapping
- **Relevance**: Core implementation basis

### POSIX Memory Mapping (Future)
- **Source**: POSIX.1-2008
- **Functions**: mmap, munmap, msync
- **Relevance**: Future Linux/macOS support

## Implementation Pattern

### C Wrapper Library
- **Header**: simple_mmap.h
- **Pattern**: Eric Bezault inline C style
- **Functions**: smm_* prefix for all operations

### Exposed Operations

| C Function | Purpose |
|------------|---------|
| smm_create_file_mapping | Map existing file |
| smm_create_anonymous_mapping | Create pagefile-backed region |
| smm_create_shared_mapping | Create named shared memory |
| smm_open_shared_mapping | Open existing shared memory |
| smm_read / smm_write | Bulk data transfer |
| smm_read_byte / smm_write_byte | Single byte access |
| smm_read_int32 / smm_write_int32 | Integer access |
| smm_flush | Sync to disk |
| smm_close | Release mapping |
| smm_is_valid / smm_is_writable | Status queries |
| smm_get_size / smm_get_error | Metadata queries |

## Coding Standards

- Design by Contract throughout
- SCOOP compatibility (separate-safe design)
- C wrapper via inline C externals
- Proper resource cleanup (close on dispose)
