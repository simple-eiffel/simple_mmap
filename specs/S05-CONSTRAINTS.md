# S05: CONSTRAINTS - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Technical Constraints

### Platform
- **OS**: Windows only (currently)
- **Future**: POSIX for Linux/macOS
- **Compiler**: EiffelStudio 25.02+
- **Concurrency**: SCOOP compatible

### Dependencies
- Eiffel base library
- Windows kernel32.dll
- C header (simple_mmap.h)

## Design Constraints

### Single Mapping Per Object
- One SIMPLE_MMAP instance = one mapping
- Cannot resize after creation
- Must close and recreate for different file/size

### Sequential Access Pattern
- Thread-safe only with SCOOP coordination
- No built-in locking
- Caller responsible for synchronization

### Memory Model
- Mapping size limited by available address space
- 32-bit: ~2GB max per mapping
- 64-bit: Limited by file/memory size

## API Constraints

### Offset Validation
- All offsets must be non-negative
- All offsets must be within mapping size
- Integer operations require 4-byte alignment recommended

### String Operations
- Null terminator required for strings
- Read string stops at null or max length
- Write string adds null terminator

### Error Handling
- Failed operations set last_error
- is_valid returns False on failure
- No exceptions thrown

## Operational Constraints

### Resource Management
- **Critical**: Must call close to release resources
- Handle leak if close not called
- OS cleans up on process exit (not recommended)

### File Locking
- File mapped for write is locked
- Other processes cannot write to file
- Read-only mapping allows shared access

## Known Limitations

1. **Windows Only**
   - No POSIX implementation yet
   - Needs mmap wrapper for Linux/macOS

2. **No Resize**
   - Cannot change mapping size
   - Must recreate for different size

3. **No Async I/O**
   - All operations are synchronous
   - Flush may block on large mappings
