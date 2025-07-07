# Interactive Hiring Dashboard - Documentation

## Overview

The Interactive Hiring Dashboard is a web-based application designed to streamline hiring workflows through seamless integration with Obsidian vaults. It provides a visual Kanban-style interface for managing candidates through different stages of the hiring process while maintaining synchronization with underlying Markdown files.

## Key Features

### 🎯 Visual Pipeline Management
- **Kanban Board Interface**: Five-column pipeline representing hiring stages
- **Real-time Updates**: Instant visual feedback for all status changes
- **Drag-and-Drop Functionality**: Move candidates between stages with enhanced drop zones covering entire column areas
- **Visual Indicators**: Color-coded stages with emoji icons for quick recognition

### 📊 Dual View Modes
- **Pipeline View**: Primary Kanban board for visual workflow management
- **List View**: Comprehensive table with sortable columns for detailed analysis

### 🔍 Advanced Search & Filtering
- **Global Search**: Search across names, skills, locations, and experience
- **Multi-dimensional Filters**: Region, position, and status filtering
- **Quick Filter Buttons**: Preset filters for common use cases
- **Real-time Results**: Instant filtering as you type

### 🔄 Obsidian Integration
- **Deep Linking**: One-click opening of candidate files in Obsidian
- **Bidirectional Sync**: Changes in dashboard update Markdown files automatically
- **Vault Awareness**: Maintains connection to specific Obsidian vault and folder structure

## Getting Started

### System Requirements
- **Browser**: Chrome or Edge (required for File System Access API)
- **Obsidian**: Installed with a vault containing candidate files
- **File Structure**: Organized hiring folder with individual candidate Markdown files

### Initial Setup

1. **Launch the Dashboard**
   - Open the `Interactive Hiring Dashboard.html` file in Chrome/Edge
   - The dashboard will prompt for initial configuration

2. **Connect to Obsidian Vault**
   - Click "Select Obsidian Vault Directory"
   - Choose the root directory of your Obsidian vault (must contain `.obsidian` folder)
   - The dashboard will validate the vault connection

3. **Select Hiring Folder**
   - Click "Select Hiring Folder"
   - Choose the folder containing your candidate Markdown files
   - The dashboard will scan and process all candidate files

4. **Initial Data Load**
   - The system will parse all Markdown files in the selected folder
   - A `candidates.json` file will be created for performance caching
   - Candidates will appear in the pipeline based on their current status

## Pipeline Stages

### 🔥 Recent Interviews
- **Purpose**: Candidates who have completed recent interviews awaiting decision
- **Status Field**: `Recent Interview - Pending`
- **Typical Actions**: Review notes, move to offer stage or rejection

### 💼 Offer Stage
- **Purpose**: Candidates receiving job offers or in offer negotiation
- **Status Field**: `Offer Stage`
- **Typical Actions**: Coordinate offer details, track acceptance/rejection

### ✅ Hired
- **Purpose**: Successfully hired candidates
- **Status Field**: `Hired`
- **Typical Actions**: Onboarding coordination, archive successful hires

### ❌ Not Hired - Negative
- **Purpose**: Candidates rejected due to negative assessment
- **Status Field**: `Not Hired - Negative`
- **Typical Actions**: Document rejection reasons, maintain for future reference

### ⏸️ Not Hired - Previous
- **Purpose**: Candidates from previous hiring cycles not selected
- **Status Field**: `Not Hired - Previous`
- **Typical Actions**: Consider for future opportunities, maintain talent pool

## User Interface Guide

### Dashboard Header
- **Search Bar**: Global search across all candidate data
- **View Toggle**: Switch between Pipeline and List views
- **Filter Controls**: Region, Position, and Status filters
- **Statistics**: Real-time counters for total candidates and key metrics

### Pipeline View
- **Column Headers**: Show stage name and candidate count
- **Candidate Cards**: Display key information (name, date, region, rating)
- **Drop Zones**: Entire column area accepts dropped cards
- **Visual Feedback**: Drag states and hover effects for better UX

### List View
- **Sortable Columns**: Click headers to sort by any field
- **Full Details**: Complete candidate information in tabular format
- **Action Buttons**: Quick access to common operations
- **Export Options**: CSV export for external analysis

### Candidate Details Modal
- **Complete Profile**: Full candidate information and notes
- **Quick Actions**: Open in Obsidian, change status, schedule follow-up
- **Contact Information**: Email, phone, LinkedIn integration
- **Interview Notes**: Structured feedback and assessment details

## Drag-and-Drop Workflow

### Enhanced Drop Zone Behavior
The dashboard features improved drag-and-drop functionality with the following enhancements:

1. **Full Column Drop Zones**: Entire column area (including headers and empty space) accepts dropped candidates
2. **Visual Feedback**: Columns highlight with green border and dashed outline during drag operations
3. **Smooth Transitions**: Cards show rotation and opacity changes while being dragged
4. **Automatic Updates**: Status changes immediately sync to both UI and Markdown files

### How to Move Candidates

1. **Initiate Drag**: Click and hold any candidate card
2. **Visual Feedback**: Card becomes semi-transparent with rotation effect
3. **Target Column**: Drag anywhere within the target column area
4. **Drop Confirmation**: Release mouse button to complete the move
5. **Automatic Sync**: Status updates in both dashboard and Markdown file

### Status Update Process

When a candidate is moved:
1. **UI Update**: Card immediately appears in new column
2. **Data Update**: In-memory candidate data is updated
3. **File Sync**: Original Markdown file status field is modified
4. **Cache Update**: `candidates.json` is automatically updated
5. **Count Refresh**: Column counts update to reflect changes

## Data Management

### File Structure Requirements

Candidate Markdown files should follow this structure:

```markdown
---
Status: Recent Interview - Pending
Date: 2024-01-15
Position: Senior Software Engineer
Region: EMEA
Rating: 4.5
Location: London, UK
Email: candidate@example.com
Phone: +44 123 456 7890
LinkedIn: https://linkedin.com/in/candidate
---

# Candidate Name

## Intro notes
[Interview notes and first impressions]

## Qualities
[Key skills and attributes]

## Additional Information
[Any other relevant details]
```

### Supported Data Fields

**Required Fields:**
- `Status`: Current pipeline stage
- `Date`: Interview or last contact date
- `Position`: Role being considered for
- `Region`: Geographic region (EMEA, APAC, Americas)

**Optional Fields:**
- `Rating`: Numerical assessment score
- `Location`: Specific city/country
- `Email`: Contact email address
- `Phone`: Contact phone number
- `LinkedIn`: LinkedIn profile URL

### File Processing Rules

1. **Inclusion**: All `.md` files in the selected folder
2. **Exclusion**: Files containing "template" or starting with "_"
3. **Parsing**: Extracts YAML frontmatter and specific content sections
4. **Caching**: Creates `candidates.json` for improved performance
5. **Sync**: Maintains bidirectional synchronization between dashboard and files

## Advanced Features

### Search Capabilities
- **Name Search**: Partial matching on candidate names
- **Content Search**: Searches within intro notes and qualities sections
- **Skills Search**: Identifies relevant technical and soft skills
- **Location Search**: Matches city, country, and region information
- **Experience Search**: Searches for years of experience and seniority levels

### Filter Combinations
- **Multiple Regions**: Select multiple geographic regions simultaneously
- **Position Types**: Filter by specific roles or position categories
- **Status Combinations**: View multiple pipeline stages together
- **Quick Filters**: Predefined combinations for common scenarios

### Export Options
- **CSV Export**: Export filtered candidate data for external analysis
- **Data Fields**: Includes all candidate information and calculated fields
- **Filtered Results**: Export respects current search and filter settings

## Technical Implementation

### Architecture Overview
- **Client-Side Application**: Runs entirely in the browser
- **File System Integration**: Uses modern File System Access API
- **No Backend Required**: Direct file manipulation without server dependency
- **Real-time Sync**: Immediate updates to both UI and file system

### Performance Optimizations
- **Caching Strategy**: JSON cache file for quick loading
- **Incremental Updates**: Only updates changed files
- **Efficient Rendering**: Optimized DOM manipulation for smooth interactions
- **Lazy Loading**: On-demand loading of detailed candidate information

### Browser Compatibility
- **Required**: Chrome 86+ or Edge 86+
- **Feature Dependency**: File System Access API support
- **Fallback**: Graceful degradation for unsupported browsers
- **Mobile**: Limited support due to File System API restrictions

## Troubleshooting

### Common Issues

**Dashboard Won't Load Candidates**
- Verify Chrome/Edge browser usage
- Check that vault contains `.obsidian` folder
- Ensure candidate files have proper YAML frontmatter
- Confirm folder permissions allow file access

**Drag-and-Drop Not Working**
- Refresh the browser page
- Verify JavaScript is enabled
- Check for browser console errors
- Ensure files aren't write-protected

**Obsidian Links Not Opening**
- Confirm Obsidian is installed and running
- Check that vault path is correctly configured
- Verify Obsidian URI protocol is registered
- Test with a simple obsidian:// link manually

**File Sync Issues**
- Check file write permissions
- Verify `candidates.json` is being created
- Look for file conflicts or locks
- Ensure vault folder is accessible

### Performance Considerations
- **Large Datasets**: Performance may degrade with 500+ candidates
- **File Size**: Very large Markdown files may slow parsing
- **Network Drives**: Local storage recommended for best performance
- **Browser Memory**: Close other tabs if experiencing slowdowns

## Best Practices

### File Organization
- **Consistent Naming**: Use clear, consistent file naming conventions
- **Complete Metadata**: Always include required YAML fields
- **Regular Cleanup**: Archive old candidates to maintain performance
- **Backup Strategy**: Regular backups of candidate files and vault

### Workflow Optimization
- **Regular Reviews**: Schedule regular pipeline reviews
- **Status Hygiene**: Keep candidate statuses current and accurate
- **Search Efficiency**: Use specific search terms for faster results
- **Filter Presets**: Create saved filter combinations for common scenarios

### Data Quality
- **Standardized Regions**: Use consistent region naming (EMEA, APAC, Americas)
- **Position Clarity**: Use clear, specific position titles
- **Rating Consistency**: Maintain consistent rating scales and criteria
- **Contact Information**: Keep contact details current and complete

## Support and Maintenance

### Regular Maintenance
- **Cache Refresh**: Occasionally delete `candidates.json` to rebuild cache
- **File Validation**: Review candidate files for proper formatting
- **Browser Updates**: Keep Chrome/Edge updated for latest features
- **Backup Verification**: Regularly test backup and restore procedures

### Future Enhancements
- **Additional Views**: Timeline, calendar, and analytics views
- **Advanced Filtering**: Custom filter combinations and saved searches
- **Integration Options**: Extended Obsidian plugin integration
- **Mobile Support**: Progressive web app capabilities

---

*Last Updated: 2024-01-15*
*Version: 1.0*
*Compatible with: Chrome 86+, Edge 86+*