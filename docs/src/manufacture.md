# Manufacture

Beluga file is compressed, it is hard to edit, so we provide a database format for editing.

```sql
CREATE TABLE {} (
    id     INTEGER PRIMARY KEY AUTOINCREMENT,
    name   TEXT UNIQUE,
    text   TEXT,
    binary BLOB
)
```

More information in [beluga-builder](https://github.com/youginil/beluga-builder)
