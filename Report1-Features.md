# Features

# ResponsiveFileManager Features List

## Core Security Features

- Session Verification - Validates user session with "RESPONSIVEfilemanager" token
  Ensures only authenticated users can access the file manager by checking for a specific session token

- Path Traversal Protection - Uses checkRelativePath() to prevent directory escape attacks
  Prevents malicious users from accessing files outside the allowed directory using "../" sequences

- File Extension Validation - Whitelist-based file type checking for uploads
  Only allows specific file types to be uploaded, blocking potentially dangerous executable files

- Input Sanitization - Sanitizes GET/POST parameters to prevent XSS
  Cleans user input to prevent cross-site scripting attacks and other injection vulnerabilities

- Size Quota Management - Enforces maximum total storage limits
  Prevents users from exhausting server disk space by enforcing storage quotas

- Permission Checking - Validates user permissions for various operations
  Ensures users can only perform actions they're authorized for (read, write, execute)

## File Creation & Upload

- Text File Creation (new_file_form)
  - Dynamic filename input with extension dropdown
  - Configurable editable text file extensions
  - Built-in textarea for content input
  Provides a web interface for creating new text files with content, supporting various text formats like .txt, .php, .js, etc.

- Image Upload (save_img)
  - Base64 encoded image processing
  - Automatic image format validation (gif, jpg, jpeg, png, webp)
  - Automatic thumbnail generation (122x91 pixels)
  - Image integrity verification using getimagesize()
  Handles image uploads from web browsers, including drag-and-drop or paste operations, with automatic thumbnail creation for gallery views

## File Operations

- File Preview (get_file with preview sub-action)
  - Text file preview with syntax highlighting
  - Google Docs viewer integration for office documents
  - Code prettification with language detection
  Allows viewing file contents without downloading, with syntax coloring for code files and document preview for office files

- File Editing (get_file with edit sub-action)
  - Text file editing with plain textarea
  - HTML file editing with CKEditor5 integration
  - Configurable editable file extensions
  Enables direct editing of text files through the web interface, with rich text editing for HTML files

- File Copy/Cut (copy_cut)
  - Clipboard-based copy/cut operations
  - Size and file count limits for bulk operations
  - Separate limits for files vs folders
  - Session-based clipboard storage
  Implements familiar copy/paste functionality for files and folders, with safeguards against operations that are too large

## Media Handling

- Media Preview (media_preview)
  - HTML5 audio player with jPlayer
  - HTML5 video player with jPlayer
  - Support for multiple audio formats (mp3, m4a, oga, wav, midi)
  - Support for multiple video formats (mp4, m4v, ogv, flv, webm)
  - Full-screen video playback
  - Volume and playback controls
  Provides built-in media players for audio and video files, eliminating the need to download files just to preview them

## Archive Management

- Archive Extraction (extract)
  - ZIP file extraction with folder structure preservation
  - GZ/TAR archive extraction using PharData
  - Pre-extraction size validation to prevent disk overflow
  - Recursive folder creation during extraction
  - File extension filtering during extraction
  Allows users to extract compressed archives directly on the server, maintaining the original folder structure while enforcing security policies

## File System Navigation

- View Mode Control (view)
  - Multiple view types (list, grid, etc.)
  - Session persistence of view preferences
  Lets users choose how files are displayed (detailed list, thumbnail grid, etc.) and remembers their preference

- File Filtering (filter)
  - Content-type based filtering
  - Optional filter memory across sessions
  Allows users to show only specific types of files (images, documents, etc.) to reduce clutter

- File Sorting (sort)
  - Multiple sort criteria support
  - Ascending/descending order control
  - Session persistence of sort preferences
  Enables sorting files by name, size, date, or type in ascending or descending order

## Permission Management

- File Permissions (chmod)
  - Unix-style permission editing (rwx for user/group/all)
  - Visual checkbox interface for permission setting
  - Recursive permission application options
  - Separate controls for files vs folders
  - Permission validation and error handling
  Provides a user-friendly interface for changing file permissions on Unix/Linux systems, with options to apply changes to entire directory trees

## Storage Backend Support

- Dual Storage Architecture
  - Local filesystem operations
  - FTP server operations with configurable paths
  - Automatic backend detection and switching
  Supports both local server storage and remote FTP servers, seamlessly switching between them based on configuration

- FTP Features
  - Temporary file handling for FTP uploads
  - Binary mode transfers
  - Bulk directory uploads with putAll()
  - FTP-specific path management
  Specialized functionality for managing files on FTP servers, handling the complexities of remote file operations

## Internationalization

- Multi-language Support (get_lang, change_lang)
  - Dynamic language file loading
  - Language selection interface
  - Session-based language persistence
  - Fallback language handling
  Provides the interface in multiple languages, allowing users to select their preferred language with automatic fallback to default language

## Specialized Viewers

- CAD File Preview (cad_preview)
  - ShareCAD.org integration for CAD file viewing
  - Support for various CAD formats
  - Embedded iframe viewer
  Enables viewing of CAD files (engineering drawings) directly in the browser using third-party viewer services

- Google Docs Integration
  - Office document preview via Google Docs Viewer
  - URL encoding for proper document access
  - Embedded iframe display
  Allows preview of Microsoft Office documents (Word, Excel, PowerPoint) using Google's document viewer

## Clipboard Management

- File Clipboard (copy_cut, clear_clipboard)
  - Session-based clipboard storage
  - Copy/cut action tracking
  - Clipboard clearing functionality
  - Multi-file clipboard support
  Maintains a clipboard of copied/cut files during the user's session, similar to desktop file managers

## Error Handling & Responses

- Standardized Response System
  - JSON response format via response() function
  - Error location tracking with AddErrorLocation()
  - Internationalized error messages
  - HTTP status code management
  Provides consistent error reporting and status responses to the frontend, with detailed error tracking for debugging

## File Validation Features

- Image Validation
  - Base64 format validation
  - Image header verification
  - File size validation
  - MIME type checking
  Ensures uploaded images are actually valid image files and not malicious files with image extensions

- Text File Validation
  - Extension whitelist checking
  - Encoding validation
  - Size limit enforcement
  Validates text files to ensure they're safe to edit and preview, preventing issues with binary files or oversized content

## Configuration-Driven Features

- Configurable Limits
  - Maximum file sizes
  - File count limits
  - Copy/cut operation limits
  - Editable file extensions
  - Preview-able file extensions
  Allows administrators to set limits and restrictions based on their server capabilities and security policies

- Feature Toggle System
  - Enable/disable specific features via configuration
  - Permission-based feature access
  - Storage backend selection
  Provides flexibility to enable only needed features and customize the file manager for different use cases

## Session Management

- User State Persistence
  - View preferences storage
  - Language selection persistence
  - Sort/filter preferences
  - Clipboard state management
  - Authentication state tracking
  Remembers user preferences and maintains state across browser sessions for a consistent user experience