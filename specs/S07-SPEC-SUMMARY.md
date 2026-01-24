# S07: SPECIFICATION SUMMARY - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Library Identity

- **Name**: simple_mmap
- **Version**: 1.0
- **Category**: System / Low-Level I/O
- **Status**: Production (Windows)

## Purpose Statement

simple_mmap provides memory-mapped file access and shared memory IPC for Eiffel applications, wrapping Win32 memory mapping APIs in a clean, contract-enabled interface.

## Key Capabilities

1. **File Mapping**
   - Map files for read-only or read-write access
   - Efficient random access to large files
   - OS-managed caching and paging

2. **Anonymous Mapping**
   - Pagefile-backed memory regions
   - Useful for temporary large allocations

3. **Shared Memory IPC**
   - Named shared mappings
   - Inter-process communication
   - Create or open existing mappings

4. **Typed Access**
   - Byte-level read/write
   - Integer read/write
   - String read/write
   - Bulk byte array operations

## Architecture Summary

- **Pattern**: Facade with C wrapper
- **Handle**: Opaque pointer to C structure
- **Dependencies**: base library, Win32 API

## Quality Attributes

| Attribute | Target |
|-----------|--------|
| Performance | Near memory speed |
| Reliability | Resource cleanup required |
| Portability | Windows only (POSIX future) |
| Safety | Contract-enforced bounds |

## API Surface

### Primary API
- Creation: make_from_file, make_anonymous, make_shared, open_shared
- Read: read_byte, read_integer, read_bytes, read_string
- Write: write_byte, write_integer, write_bytes, write_string
- Control: flush, close
- Status: is_valid, is_writable, size, last_error
