# 7S-04: SIMPLE-STAR - simple_mmap


**Date**: 2026-01-23

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Ecosystem Dependencies

### Required simple_* Libraries

| Library | Purpose | Version |
|---------|---------|---------|
| (none) | Self-contained | - |

### ISE Base Libraries Used

| Library | Purpose |
|---------|---------|
| base | ARRAY, MANAGED_POINTER, C_STRING |

### External Dependencies

| Dependency | Purpose |
|------------|---------|
| simple_mmap.h | C wrapper for Win32 API |
| Windows kernel32 | CreateFileMapping, etc. |

## Integration Points

### C Wrapper Integration
- Header file included via inline C
- Functions called via C inline externals
- Handle passed between Eiffel and C

### Memory Management
- MANAGED_POINTER for buffer operations
- C_STRING for path/name parameters
- Proper cleanup in close feature

## Ecosystem Fit

### Category
System / Low-Level I/O

### Phase
Phase 3 - Core functionality complete

### Maturity
Production-ready for Windows

### Consumers
- simple_db (potential future use)
- High-performance file processing
- IPC applications

## Usage Patterns

### File Mapping
```eiffel
mmap: SIMPLE_MMAP
create mmap.make_from_file ("data.bin", True)
if mmap.is_valid then
  value := mmap.read_integer (offset)
  mmap.write_integer (offset, new_value)
  mmap.flush
  mmap.close
end
```

### Shared Memory IPC
```eiffel
-- Process 1: Create
create mmap.make_shared ("my_channel", 4096)

-- Process 2: Open
create mmap.open_shared ("my_channel")
```
