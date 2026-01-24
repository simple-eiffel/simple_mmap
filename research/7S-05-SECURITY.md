# 7S-05: SECURITY - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Security Model

### Trust Boundary
- Low-level system access library
- Operates with process permissions
- Shared memory visible to other processes

### Threat Assessment

| Threat | Risk | Mitigation |
|--------|------|------------|
| Unauthorized file access | Medium | OS file permissions |
| Shared memory snooping | High | Use for trusted IPC only |
| Buffer overflow | Medium | Bounds checking in contracts |
| Resource exhaustion | Low | OS limits on mappings |
| Race conditions | Medium | SCOOP for coordination |

## Access Control

### File Mappings
- Subject to file system permissions
- Read-only or read-write based on creation
- Cannot escalate beyond file permissions

### Shared Memory
- Accessible to any process knowing the name
- **WARNING**: No built-in access control
- Use only for trusted inter-process communication

### Anonymous Mappings
- Private to creating process
- No security concerns

## Input Validation

### Path Validation
- Converted to C string safely
- File existence checked by OS
- Invalid paths fail gracefully

### Offset Validation
```eiffel
require
  valid_offset: a_offset >= 0 and a_offset < size
```

### Size Validation
```eiffel
require
  in_bounds: a_offset + a_count <= size
```

## Resource Management

### Handle Lifecycle
- Create: Allocates C structure and mapping
- Use: Read/write operations
- Close: Releases all resources
- **Critical**: Always close to avoid leaks

### Error Handling
- last_error provides error messages
- Invalid handle detection
- Graceful degradation on failures

## Recommendations

1. **Use for trusted data only** - Shared memory has no encryption
2. **Always close mappings** - Prevent resource leaks
3. **Validate offsets** - Contracts enforce bounds
4. **Consider encryption** - For sensitive shared data
