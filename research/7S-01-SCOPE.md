# 7S-01: SCOPE - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Problem Statement

Eiffel applications need efficient access to large files and shared memory for inter-process communication. Traditional file I/O is inefficient for random access patterns, and Eiffel lacks native memory-mapped file support.

## Library Purpose

simple_mmap provides memory-mapped file access with:

1. **File Mapping** - Map files directly into memory for efficient access
2. **Anonymous Mapping** - Create memory regions backed by pagefile
3. **Shared Memory** - Named shared mappings for IPC
4. **SCOOP Compatibility** - Safe for concurrent access patterns

## Target Users

- Developers working with large data files
- Applications needing inter-process communication
- Database-like applications requiring efficient I/O
- Performance-critical file processing

## Scope Boundaries

### In Scope
- File-backed memory mappings (read/write)
- Anonymous (pagefile-backed) mappings
- Named shared memory for IPC
- Byte, integer, and string read/write
- Flush to disk operations
- Windows implementation via Win32 API

### Out of Scope
- Linux/macOS implementation (future)
- Memory-mapped networking
- Automatic resizing
- Memory-mapped queues or higher-level structures

## Success Metrics

- I/O performance > 100MB/s for sequential access
- Zero memory leaks on close
- Reliable IPC between processes
