# RFC: Cornell Notes Data Schema

**Status:** Draft  
**Author:** Tony Bierman  
**Created:** 2026-01-06  
**Last Updated:** 2026-01-06

## Abstract

This RFC proposes a standardized data schema for representing Cornell Notes in digital format. The Cornell Notes system, developed by Walter Pauk at Cornell University, divides note-taking into three distinct sections: cue column, notes column, and summary. This schema enables consistent storage, interchange, and manipulation of Cornell Notes across applications and platforms.

## Motivation

Cornell Notes is a widely-used note-taking system, but there is no standardized digital format for representing these notes. This leads to:

- Lack of interoperability between note-taking applications
- Difficulty in migrating notes between platforms
- Inconsistent implementations of the Cornell method
- Limited tooling for analysis and processing of Cornell Notes

A standardized schema would enable:

- Cross-platform compatibility
- Automated analysis and study tools
- Better archival and preservation
- Consistent user experience across applications

## Design Goals

1. **Fidelity**: Accurately represent all components of the Cornell Notes method
2. **Extensibility**: Allow for future enhancements without breaking changes
3. **Simplicity**: Easy to implement and understand
4. **Flexibility**: Support various content types (text, images, code, etc.)
5. **Interoperability**: Compatible with common data formats (JSON, YAML, XML)

## Specification

### Core Schema (v1.0)

#### Cornell Note Document Structure

```json
{
  "version": "1.0",
  "metadata": {
    "id": "string (UUID)",
    "title": "string",
    "subject": "string (optional)",
    "topic": "string (optional)",
    "author": "string (optional)",
    "created": "ISO 8601 datetime",
    "modified": "ISO 8601 datetime",
    "tags": ["string"] (optional)
  },
  "sections": [
    {
      "id": "string (UUID)",
      "cues": [
        {
          "id": "string (UUID)",
          "content": "string or structured content",
          "type": "text|question|keyword|custom",
          "position": "integer (order)",
          "created": "ISO 8601 datetime",
          "modified": "ISO 8601 datetime"
        }
      ],
      "notes": [
        {
          "id": "string (UUID)",
          "content": "string or structured content",
          "type": "text|list|code|image|link|custom",
          "position": "integer (order)",
          "cueLinks": ["string (cue IDs)"] (optional),
          "created": "ISO 8601 datetime",
          "modified": "ISO 8601 datetime"
        }
      ],
      "position": "integer (order)"
    }
  ],
  "summary": {
    "content": "string or structured content",
    "created": "ISO 8601 datetime",
    "modified": "ISO 8601 datetime"
  }
}
```

### Field Definitions

#### Metadata Object

- **version** (required): Schema version for backward compatibility
- **metadata.id** (required): Unique identifier for the note document
- **metadata.title** (required): Title of the Cornell Note
- **metadata.subject** (optional): Academic subject or category
- **metadata.topic** (optional): Specific topic covered
- **metadata.author** (optional): Creator of the notes
- **metadata.created** (required): Timestamp of creation
- **metadata.modified** (required): Timestamp of last modification
- **metadata.tags** (optional): Array of tags for organization

#### Section Object

Cornell Notes can contain multiple sections for organizing different topics within the same note session.

- **id** (required): Unique identifier for the section
- **cues** (required): Array of cue column entries
- **notes** (required): Array of notes column entries
- **position** (required): Order of section in document

#### Cue Object

- **id** (required): Unique identifier
- **content** (required): The cue text or structured content
- **type** (required): Type of cue
  - `text`: General text cue
  - `question`: Question format
  - `keyword`: Key term or concept
  - `custom`: Application-specific type
- **position** (required): Order within cue column
- **created** (required): Creation timestamp
- **modified** (required): Last modification timestamp

#### Note Object

- **id** (required): Unique identifier
- **content** (required): The note content
- **type** (required): Type of content
  - `text`: Plain text
  - `list`: Bulleted or numbered list
  - `code`: Code snippet
  - `image`: Image reference or embedded data
  - `link`: URL or reference
  - `custom`: Application-specific type
- **position** (required): Order within notes column
- **cueLinks** (optional): Array of cue IDs that relate to this note
- **created** (required): Creation timestamp
- **modified** (required): Last modification timestamp

#### Summary Object

- **content** (required): Summary content
- **created** (required): Creation timestamp
- **modified** (required): Last modification timestamp

### Structured Content Format

For rich content beyond plain strings, the `content` field can use structured format:

```json
{
  "format": "markdown|html|plain",
  "data": "string content",
  "attachments": [
    {
      "type": "image|file|audio|video",
      "url": "string (URL or data URI)",
      "metadata": {
        "filename": "string",
        "size": "integer (bytes)",
        "mimeType": "string"
      }
    }
  ]
}
```

## Examples

### Minimal Example

```json
{
  "version": "1.0",
  "metadata": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "title": "Introduction to Photosynthesis",
    "created": "2026-01-06T10:30:00Z",
    "modified": "2026-01-06T10:30:00Z"
  },
  "sections": [
    {
      "id": "550e8400-e29b-41d4-a716-446655440001",
      "cues": [
        {
          "id": "550e8400-e29b-41d4-a716-446655440002",
          "content": "What is photosynthesis?",
          "type": "question",
          "position": 0,
          "created": "2026-01-06T10:30:00Z",
          "modified": "2026-01-06T10:30:00Z"
        }
      ],
      "notes": [
        {
          "id": "550e8400-e29b-41d4-a716-446655440003",
          "content": "Process by which plants convert light energy into chemical energy. Occurs in chloroplasts using chlorophyll.",
          "type": "text",
          "position": 0,
          "cueLinks": ["550e8400-e29b-41d4-a716-446655440002"],
          "created": "2026-01-06T10:30:00Z",
          "modified": "2026-01-06T10:30:00Z"
        }
      ],
      "position": 0
    }
  ],
  "summary": {
    "content": "Photosynthesis is the fundamental process that allows plants to convert sunlight into usable energy, supporting most life on Earth.",
    "created": "2026-01-06T10:35:00Z",
    "modified": "2026-01-06T10:35:00Z"
  }
}
```

### Rich Content Example

```json
{
  "version": "1.0",
  "metadata": {
    "id": "660e8400-e29b-41d4-a716-446655440000",
    "title": "Python List Comprehensions",
    "subject": "Computer Science",
    "topic": "Python Programming",
    "created": "2026-01-06T14:00:00Z",
    "modified": "2026-01-06T14:30:00Z",
    "tags": ["python", "programming", "data-structures"]
  },
  "sections": [
    {
      "id": "660e8400-e29b-41d4-a716-446655440001",
      "cues": [
        {
          "id": "660e8400-e29b-41d4-a716-446655440002",
          "content": "Basic syntax",
          "type": "keyword",
          "position": 0,
          "created": "2026-01-06T14:00:00Z",
          "modified": "2026-01-06T14:00:00Z"
        }
      ],
      "notes": [
        {
          "id": "660e8400-e29b-41d4-a716-446655440003",
          "content": {
            "format": "markdown",
            "data": "List comprehensions provide concise syntax:\n\n```python\nsquares = [x**2 for x in range(10)]\n```"
          },
          "type": "code",
          "position": 0,
          "cueLinks": ["660e8400-e29b-41d4-a716-446655440002"],
          "created": "2026-01-06T14:00:00Z",
          "modified": "2026-01-06T14:00:00Z"
        }
      ],
      "position": 0
    }
  ],
  "summary": {
    "content": "List comprehensions are a Pythonic way to create lists using a compact syntax, making code more readable and efficient.",
    "created": "2026-01-06T14:30:00Z",
    "modified": "2026-01-06T14:30:00Z"
  }
}
```

## Rationale

### Why JSON as Primary Format?

- **Ubiquity**: JSON parsers exist for virtually every programming language
- **Human-readable**: Easy to inspect and debug
- **Tooling**: Extensive ecosystem of validators, editors, and transformers
- **Web-friendly**: Native JavaScript support for web applications

### Design Decisions

**Multiple Sections**: While traditional Cornell Notes use a single page, digital notes benefit from the ability to organize multiple related sections within one document.

**UUID Identifiers**: Using UUIDs instead of sequential IDs allows for:
- Distributed creation without coordination
- Merging notes from multiple sources
- Stable references across systems

**Type Fields**: Explicit type fields enable applications to:
- Render content appropriately
- Validate content structure
- Provide type-specific features (syntax highlighting, image rendering, etc.)

**CueLinks**: The `cueLinks` array creates explicit relationships between notes and cues, enabling:
- Better navigation
- Study tools that quiz based on cue-note relationships
- Analytics on note-taking patterns

**Timestamps**: Separate created/modified timestamps enable:
- Version history tracking
- Temporal analysis of note-taking
- Conflict resolution in collaborative environments

## Implementation Guidelines

### Validation

Implementations SHOULD validate documents against the schema and reject invalid documents with clear error messages.

### Backward Compatibility

Future schema versions MUST maintain backward compatibility by:
- Not removing required fields
- Not changing field semantics
- Adding new fields as optional
- Incrementing the version number

### File Extensions

Recommended file extensions:
- `.cornell.json` - JSON format
- `.cornell.yaml` - YAML format
- `.cornell.xml` - XML format

### MIME Types

Proposed MIME type: `application/vnd.cornell-notes+json`

## Security Considerations

1. **Content Sanitization**: Applications MUST sanitize HTML/Markdown content to prevent XSS attacks
2. **File Size Limits**: Implementations SHOULD enforce reasonable size limits
3. **Image Data**: When using data URIs for images, validate format and size
4. **User Privacy**: Metadata fields like author should be optional and users should control what's included

## Future Extensions

### Potential v2.0 Features

- **Collaboration**: Fields for multiple authors, comments, suggestions
- **Study Metadata**: Spaced repetition scheduling, difficulty ratings
- **Linking**: References between different Cornell Note documents
- **Templates**: Predefined structures for specific note-taking scenarios
- **Accessibility**: ARIA labels and alternative text requirements
- **Encryption**: Optional field-level or document-level encryption

## References

1. Pauk, W., & Owens, R. J. Q. (2013). *How to Study in College* (11th ed.)
2. JSON Schema Specification: https://json-schema.org/
3. ISO 8601 DateTime Format: https://www.iso.org/iso-8601-date-and-time-format.html
4. UUID Specification (RFC 4122): https://tools.ietf.org/html/rfc4122

## Appendix A: JSON Schema Definition

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$id": "https://example.com/cornell-notes-schema-v1.0.json",
  "title": "Cornell Notes Schema",
  "description": "Schema for Cornell Notes digital format",
  "type": "object",
  "required": ["version", "metadata", "sections", "summary"],
  "properties": {
    "version": {
      "type": "string",
      "pattern": "^[0-9]+\\.[0-9]+$"
    },
    "metadata": {
      "type": "object",
      "required": ["id", "title", "created", "modified"],
      "properties": {
        "id": {
          "type": "string",
          "format": "uuid"
        },
        "title": {
          "type": "string",
          "minLength": 1
        },
        "subject": {
          "type": "string"
        },
        "topic": {
          "type": "string"
        },
        "author": {
          "type": "string"
        },
        "created": {
          "type": "string",
          "format": "date-time"
        },
        "modified": {
          "type": "string",
          "format": "date-time"
        },
        "tags": {
          "type": "array",
          "items": {
            "type": "string"
          }
        }
      }
    },
    "sections": {
      "type": "array",
      "minItems": 1,
      "items": {
        "type": "object",
        "required": ["id", "cues", "notes", "position"],
        "properties": {
          "id": {
            "type": "string",
            "format": "uuid"
          },
          "cues": {
            "type": "array",
            "items": {
              "type": "object",
              "required": ["id", "content", "type", "position", "created", "modified"],
              "properties": {
                "id": {
                  "type": "string",
                  "format": "uuid"
                },
                "content": {
                  "oneOf": [
                    {"type": "string"},
                    {"type": "object"}
                  ]
                },
                "type": {
                  "type": "string",
                  "enum": ["text", "question", "keyword", "custom"]
                },
                "position": {
                  "type": "integer",
                  "minimum": 0
                },
                "created": {
                  "type": "string",
                  "format": "date-time"
                },
                "modified": {
                  "type": "string",
                  "format": "date-time"
                }
              }
            }
          },
          "notes": {
            "type": "array",
            "items": {
              "type": "object",
              "required": ["id", "content", "type", "position", "created", "modified"],
              "properties": {
                "id": {
                  "type": "string",
                  "format": "uuid"
                },
                "content": {
                  "oneOf": [
                    {"type": "string"},
                    {"type": "object"}
                  ]
                },
                "type": {
                  "type": "string",
                  "enum": ["text", "list", "code", "image", "link", "custom"]
                },
                "position": {
                  "type": "integer",
                  "minimum": 0
                },
                "cueLinks": {
                  "type": "array",
                  "items": {
                    "type": "string",
                    "format": "uuid"
                  }
                },
                "created": {
                  "type": "string",
                  "format": "date-time"
                },
                "modified": {
                  "type": "string",
                  "format": "date-time"
                }
              }
            }
          },
          "position": {
            "type": "integer",
            "minimum": 0
          }
        }
      }
    },
    "summary": {
      "type": "object",
      "required": ["content", "created", "modified"],
      "properties": {
        "content": {
          "oneOf": [
            {"type": "string"},
            {"type": "object"}
          ]
        },
        "created": {
          "type": "string",
          "format": "date-time"
        },
        "modified": {
          "type": "string",
          "format": "date-time"
        }
      }
    }
  }
}
```

## Appendix B: Conversion Guidelines

### From Traditional Cornell Notes

When digitizing paper Cornell Notes:
1. Create one section per page
2. Preserve the original order of cues and notes
3. Use `position` fields to maintain visual relationships
4. Include page numbers or dates in metadata

### To Other Formats

**Markdown Export:**
```markdown
# [Title]

## Section 1

### Cues
- [Cue 1]
- [Cue 2]

### Notes
[Notes content]

## Summary
[Summary content]
```

**PDF Export:** Maintain traditional two-column layout with summary at bottom

## Changelog

- **v1.0** (2026-01-06): Initial specification

---

**Status**: This RFC is open for community feedback and revision.