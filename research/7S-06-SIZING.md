# 7S-06: SIZING - simple_mmap


**Date**: 2026-01-23

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Codebase Metrics

### Source Files
- **Total Classes**: 3
- **Main Source**: 1 class in src/
- **Testing**: 2 classes in testing/
- **C Header**: 1 file (simple_mmap.h)

### Lines of Code
- SIMPLE_MMAP: ~400 LOC Eiffel
- simple_mmap.h: ~300 LOC C
- **Total**: ~700 LOC

### Complexity Assessment

| Component | Complexity | Rationale |
|-----------|------------|-----------|
| SIMPLE_MMAP | Medium | Many C externals |
| C Wrapper | Medium | Win32 API handling |
| Tests | Low | Basic validation |

## Performance Characteristics

### Memory Usage
- Minimal Eiffel overhead
- Mapping size = file/region size
- Managed by OS virtual memory

### I/O Performance
- **Sequential**: Near memory speed (GB/s)
- **Random Access**: Much faster than seek+read
- **Write-back**: Async unless flushed

### Scalability
- Supports files > 4GB (64-bit)
- Multiple mappings per process
- OS limits apply

## Build Metrics

- Compile time: ~5 seconds
- C compilation: Inline (no separate step)
- Dependencies: base only

## Feature Count

| Category | Count |
|----------|-------|
| Creation procedures | 4 |
| Read operations | 4 |
| Write operations | 4 |
| Status queries | 5 |
| Operations | 2 |

## Maintenance Burden

- Platform-specific C code
- Future: Add POSIX implementation
- Low complexity overall
