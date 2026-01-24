# S01: PROJECT INVENTORY - simple_mmap

**BACKWASH** | Generated: 2026-01-23 | Library: simple_mmap

## Project Structure

```
simple_mmap/
  src/
    simple_mmap.e              # Main facade class
  include/
    simple_mmap.h              # C wrapper header
  testing/
    test_app.e                 # Test application entry
    lib_tests.e                # Test suite
  research/                    # 7S research documents
  specs/                       # Specification documents
  simple_mmap.ecf              # Library ECF configuration
```

## File Counts

| Category | Count |
|----------|-------|
| Source (.e) | 3 |
| C Header (.h) | 1 |
| Configuration (.ecf) | 1 |
| Documentation (.md) | 15+ |

## Dependencies

### simple_* Ecosystem
- (none - self-contained)

### ISE Libraries
- base (ARRAY, MANAGED_POINTER, C_STRING)

### External
- Windows kernel32.dll (memory mapping APIs)

## Build Targets

| Target | Type | Purpose |
|--------|------|---------|
| simple_mmap | library | Reusable library |
| simple_mmap_tests | executable | Test suite |

## Version

Current: 1.0
