# 7S-03: SOLUTIONS - simple_mmap


**Date**: 2026-01-23

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Alternative Solutions Evaluated

### 1. Pure Eiffel File I/O
- **Approach**: Use RAW_FILE with seek/read/write
- **Pros**: No C code, portable
- **Cons**: Inefficient for random access, no IPC
- **Decision**: Rejected for performance reasons

### 2. ISE Memory-Mapped Support
- **Research**: ISE libraries don't provide this
- **Outcome**: Need custom implementation

### 3. External Library Binding
- **Options**: Boost.Interprocess, other C++ libraries
- **Pros**: Mature, cross-platform
- **Cons**: Heavy dependency, complex binding
- **Decision**: Rejected - prefer simple C wrapper

### 4. Custom C Wrapper (Chosen)
- **Approach**: Thin C wrapper around Win32 API
- **Pros**: Minimal code, full control, inline C
- **Cons**: Platform-specific initially
- **Decision**: Implemented

## Architecture Decisions

### Single Class Design
- SIMPLE_MMAP as the only public class
- Encapsulates all mapping functionality
- Multiple creation procedures for different use cases

### Handle-Based Design
- C structure holds mapping state
- Eiffel holds opaque handle pointer
- All operations via handle

### Type-Safe Access
- Typed read/write for bytes, integers, strings
- Array-based bulk operations
- Bounds checking via contracts

## Technology Stack

- Eiffel with inline C externals
- Win32 API (CreateFileMapping, etc.)
- C wrapper library (simple_mmap.h)
