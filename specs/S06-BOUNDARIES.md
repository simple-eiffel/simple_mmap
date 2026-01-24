# S06: BOUNDARIES - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## System Boundaries

```
+------------------+               +------------------+
|   Application    | <----------> |   SIMPLE_MMAP    |
|                  |   Eiffel API |                  |
+------------------+               +------------------+
                                          |
                                          v (inline C)
                                   +------------------+
                                   |   C Wrapper      |
                                   |   simple_mmap.h  |
                                   +------------------+
                                          |
                                          v
                                   +------------------+
                                   |   Win32 API      |
                                   |   kernel32.dll   |
                                   +------------------+
                                          |
                                          v
                                   +------------------+
                                   |   Operating      |
                                   |   System         |
                                   |   - File System  |
                                   |   - Virtual Mem  |
                                   +------------------+
```

## External Interfaces

### Input Boundaries

| Interface | Format | Source |
|-----------|--------|--------|
| File paths | String | Application |
| Shared memory names | String | Application |
| Data to write | Bytes/Integer/String | Application |

### Output Boundaries

| Interface | Format | Destination |
|-----------|--------|-------------|
| Read data | Bytes/Integer/String | Application |
| Status | Boolean | Application |
| Error messages | String | Application |

## Module Boundaries

### Public Module
- SIMPLE_MMAP class
- All creation procedures
- All public features

### Private Module
- C external declarations
- Handle management
- Internal state

## Inter-Process Boundary

### Shared Memory
```
+------------------+               +------------------+
|   Process A      | -- Named --> |   Shared Memory  |
|   (Creator)      |    Mapping   |   Region         |
+------------------+               +------------------+
                                          ^
                                          |
+------------------+               Named   |
|   Process B      | -- Mapping ----------+
|   (Consumer)     |
+------------------+
```

## Trust Boundaries

### Trusted
- Eiffel runtime
- C wrapper code
- Win32 API

### Untrusted
- File contents (may be corrupted)
- Shared memory contents (other process may write)
- Input parameters (validated by contracts)

## Versioning

- Library version: 1.0
- C wrapper version: 1.0
- Win32 API: Windows 10+
