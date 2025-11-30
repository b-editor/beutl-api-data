# Beutl API Data

This repository contains auto-generated API documentation data for [Beutl](https://github.com/b-editor/beutl).

## Structure

```
api/
├── toc.yml              # Table of Contents
├── Beutl.yml            # Namespace definitions
├── Beutl.CoreObject.yml # Type definitions
└── ...                  # ~843 YML files
```

## Usage

This repository is intended to be used as a Git submodule in [beutl-web-docs](https://github.com/b-editor/beutl-web-docs):

```bash
git submodule add https://github.com/b-editor/beutl-api-data.git src/data/api-reference
```

## Auto-Update

API documentation is automatically updated when:

1. A new release is published in [b-editor/beutl](https://github.com/b-editor/beutl)
2. The release workflow triggers this repository's update workflow
3. DocFX generates new YML metadata from the latest DLLs
4. Changes are committed and pushed to this repository

### Manual Update

You can manually trigger an update via GitHub Actions:

1. Go to Actions tab
2. Select "Update API Documentation" workflow
3. Click "Run workflow"
4. Optionally specify a Beutl ref (tag/branch)

## File Format

YML files follow the [DocFX ManagedReference schema](https://dotnet.github.io/docfx/spec/metadata_format_spec.html).

### Example

```yaml
### YamlMime:ManagedReference
items:
- uid: Beutl.CoreObject
  commentId: T:Beutl.CoreObject
  id: CoreObject
  parent: Beutl
  name: CoreObject
  nameWithType: CoreObject
  fullName: Beutl.CoreObject
  type: Class
  syntax:
    content: 'public abstract class CoreObject : ICoreObject'
  inheritance:
  - System.Object
```

## License

This data is generated from [Beutl](https://github.com/b-editor/beutl) source code and follows the same license.
