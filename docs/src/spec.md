# Specification

## Concepts

### Entry

Entry is a word/phrase definition written by HTML.

- if the definition is `@@@link={another_entry_name}`, it means redirect to another entry
- resource url is `/@resource?name={resource_name}`
- `<a href="entry://{entry_name}">` entry link
- `<a href="sound://{resource_name}">` click to play sound, you can also use audio element with resource url

### Resource

Images, audios in entry are called resources

### Token

If entry is a phrase, you can split it into some words, every single word is a token. This is for searching phrases by word. It is not required.

## Dictionary Files

Dictionary is a directory which contains some files.

> - [x] means required

- [x] English `(a dictionary named English, it is also a directory)`
  - [x] index.bel `(the file consists of entries)`
  - [ ] index.beld `(resource file, such as images, audios)`
  - [ ] index.{flag}.beld `(take a flag in case you have more resource files)`
  - [ ] index.css `(the default style file)`
  - [ ] index.js `(the default javascript file)`
  - [ ] ... `(other files if you need)`

## Entry/Resource File Structure

Entry file and resource file have the same structure: **Metadata** and **two B+ Trees**, one for entries/resources, another for token index. The token tree is no need for resource file, so resource file has an empty token index tree.

### Parsing

| Bytes             | Description                           |
| ----------------- | ------------------------------------- |
| 2                 | `spec` the beluga file format version |
| 4                 | `metadata_length`                     |
| `metadata_length` | `Metadata` JSON string                |
| -24 + 8           | entry/resource root node offset       |
| -16 + 4           | entry/resource root node size         |
| -12 + 8           | token root node offset                |
| -4 + 4            | token root node size                  |

### Parsing Node

> Node is compressed by Deflate algorithm

| Bytes | Description                  |
| ----- | ---------------------------- |
| 1     | `is_leaf_node`               |
| 4     | `entry_num` loop for entries |

### Parsing Entry/Resource

| Bytes               | Description                                |
| ------------------- | ------------------------------------------ |
| 4                   | `key_length`                               |
| `key_length`        | `key` is utf8 string                       |
| 4 `is_leaf == true` | `value_length`                             |
| `value_length`      | string for entry, binary data for resource |
