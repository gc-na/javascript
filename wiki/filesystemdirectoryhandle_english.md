<!--
Meta Description: # FileSystemDirectoryHandle: Accessing File System Directories in JavaScript ## Synopsis The `FileSystemDirectoryHandle` interface enables web applica...
Meta Keywords: file, directory, user, await, name
-->

# FileSystemDirectoryHandle: Accessing File System Directories in JavaScript

## Synopsis
The `FileSystemDirectoryHandle` interface enables web applications to interact with and manage directories within a user's local file system using the File System Access API, allowing for a more seamless file management experience.

## Documentation

### Purpose
The `FileSystemDirectoryHandle` provides a way for developers to read, write, and manage files and directories in the user's file system. This API allows web applications to create a more native file handling experience, enabling users to open, save, and manipulate files directly from their local directories in a secure manner.

### Usage
To use `FileSystemDirectoryHandle`, a user must first grant permission through a file picker dialog. This is typically initiated by calling `window.showDirectoryPicker()`, which prompts the user to select a directory. Once access is granted, developers can create instances of `FileSystemDirectoryHandle` to perform various operations such as reading files, creating new directories, and deleting files.

### Details
- **Methods**:
  - `getFileHandle(name: string, options?: { create?: boolean })`: Retrieves a `FileSystemFileHandle` for a file in the directory.
  - `getDirectoryHandle(name: string, options?: { create?: boolean })`: Retrieves a `FileSystemDirectoryHandle` for a subdirectory.
  - `removeEntry(name: string, options?: { recursive?: boolean })`: Deletes a file or directory. If the `recursive` option is set to true, it can delete non-empty directories.
  - `queryPermission(options?: PermissionDescriptor): Promise<PermissionStatus>`: Checks the current permission status for the directory.

- **Properties**:
  - `name`: A string that contains the name of the directory.
  - `kind`: A string indicating the kind of handle, which will be "directory".

### Permissions
Accessing the file system requires user interaction and permission. The `FileSystemDirectoryHandle` cannot be accessed without going through the permission granting step.

## Examples

### Example 1: Opening a Directory
```javascript
async function openDirectory() {
    const directoryHandle = await window.showDirectoryPicker();
    console.log('Directory selected:', directoryHandle.name);
}
openDirectory();
```

### Example 2: Reading Files from a Directory
```javascript
async function readFilesFromDirectory() {
    const directoryHandle = await window.showDirectoryPicker();
    for await (const [name, handle] of directoryHandle.entries()) {
        if (handle.kind === 'file') {
            const file = await handle.getFile();
            console.log(`File: ${name}, Size: ${file.size} bytes`);
        }
    }
}
readFilesFromDirectory();
```

### Example 3: Creating a New File in a Directory
```javascript
async function createFileInDirectory() {
    const directoryHandle = await window.showDirectoryPicker();
    const newFileHandle = await directoryHandle.getFileHandle('newFile.txt', { create: true });
    const writable = await newFileHandle.createWritable();
    await writable.write('Hello, World!');
    await writable.close();
    console.log('File created:', newFileHandle.name);
}
createFileInDirectory();
```

## Explanation
- **Common Pitfalls**:
  - Forgetting to request user permission: The API does not allow access to the file system without explicit user action, so ensure that the directory picker is called in response to a user event (like a button click).
  - Handling asynchronous operations: The methods return promises, so asynchronous handling (using `async/await` or `.then()`) is necessary to correctly manage file operations.
  - Not checking if a handle is a file or directory: Always verify the kind of handle when iterating through entries to avoid errors.

- **Gotchas**:
  - The user can change permissions and close the directory picker, which may lead to errors if operations are attempted afterward. Always handle exceptions gracefully.
  - The directory handles are temporary and may not persist across page reloads.

## One Line Summary
`FileSystemDirectoryHandle` provides a secure way to manage directories and files in the user's local file system via the File System Access API in JavaScript.