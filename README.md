# Obsidian Hiring Dashboard

A web-based application designed to streamline hiring workflows through seamless integration with Obsidian vaults. This dashboard provides a visual Kanban-style interface for managing candidates through different stages of the hiring process while maintaining synchronization with underlying Markdown files.

## Features

- **Visual Pipeline Management**: Kanban-style board with drag-and-drop functionality
- **Obsidian Integration**: Deep integration with Obsidian vaults and Markdown files
- **Real-time Sync**: Bidirectional synchronization between dashboard and files
- **Advanced Search & Filtering**: Multi-dimensional search and filtering capabilities
- **Dual View Modes**: Pipeline view and detailed list view
- **Enhanced Drag-and-Drop**: Drop anywhere in column areas, not just on cards

## Getting Started

1. **Browser Requirements**: Chrome 86+ or Edge 86+ (required for File System Access API)
2. **Open the Dashboard**: Open `Interactive Hiring Dashboard.html` in your browser
3. **Connect to Obsidian**: Select your Obsidian vault directory
4. **Select Hiring Folder**: Choose the folder containing candidate Markdown files

## Documentation

See `Interactive Hiring Dashboard - Documentation.md` for comprehensive usage instructions, setup guide, and technical details.

## File Structure

```
obsidian_hiring_dashboard/
├── Interactive Hiring Dashboard.html    # Main application
├── Interactive Hiring Dashboard - Documentation.md    # Complete documentation
└── README.md                           # This file
```

## Requirements

- **Obsidian**: Installed with a vault containing candidate files
- **Browser**: Chrome or Edge with File System Access API support
- **File Format**: Candidate files should be Markdown with YAML frontmatter

## Pipeline Stages

- 🔥 **Recent Interviews**: Candidates awaiting decision
- 💼 **Offer Stage**: Candidates receiving offers
- ✅ **Hired**: Successfully hired candidates
- ❌ **Not Hired - Negative**: Rejected candidates
- ⏸️ **Not Hired - Previous**: Previous cycle candidates

## Technical Details

- **Client-side Application**: Runs entirely in the browser
- **No Backend Required**: Direct file manipulation without server dependency
- **Real-time Updates**: Immediate synchronization with file system
- **Performance Optimized**: JSON caching for improved loading times

## License

This project is intended for internal use and workflow optimization.

---

*For detailed documentation, troubleshooting, and advanced features, see the complete documentation file.*