

# **Java `File` Class Documentation**

## **1. Class Declaration**

```java
public class java.io.File implements java.io.Serializable, java.lang.Comparable<java.io.File>
```

The `File` class in Java is a representation of file and directory pathnames. It implements the `Serializable` and `Comparable` interfaces.

## **2. Constants**

- **`public static final char separatorChar`**
  - The system-dependent default name-separator character, such as `/` on Unix and `\` on Windows.
  
- **`public static final String separator`**
  - The system-dependent default name-separator string, such as `/` on Unix and `\` on Windows.

- **`public static final char pathSeparatorChar`**
  - The system-dependent path-separator character used in `PATH` environment variables, typically `:` on Unix and `;` on Windows.

- **`public static final String pathSeparator`**
  - The system-dependent path-separator string, typically `:` on Unix and `;` on Windows.

## **3. Constructors**

### **3.1 Constructors Overview**

1. **`public File(String pathname)`**
   - Creates a new `File` instance by converting the given pathname string into an abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     ```

2. **`public File(String parent, String child)`**
   - Creates a new `File` instance from a parent pathname string and a child pathname string.
   - Example:
     ```java
     File file = new File("C:/Users/User", "example.txt");
     ```

3. **`public File(File parent, String child)`**
   - Creates a new `File` instance from a parent abstract pathname and a child pathname string.
   - Example:
     ```java
     File parentDir = new File("C:/Users/User");
     File file = new File(parentDir, "example.txt");
     ```

4. **`public File(URI uri)`**
   - Creates a new `File` instance by converting the given `file:` URI into an abstract pathname.
   - Example:
     ```java
     URI uri = new URI("file:///C:/example.txt");
     File file = new File(uri);
     ```

## **4. Path Operations**

### **4.1 Path Information**

1. **`public String getName()`**
   - Returns the name of the file or directory denoted by this abstract pathname.
   - Example:
     ```java
     File file = new File("C:/Users/User/example.txt");
     String name = file.getName(); // Output: "example.txt"
     ```

2. **`public String getParent()`**
   - Returns the pathname string of the parent directory, or `null` if the pathname does not name a parent directory.
   - Example:
     ```java
     File file = new File("C:/Users/User/example.txt");
     String parent = file.getParent(); // Output: "C:/Users/User"
     ```

3. **`public File getParentFile()`**
   - Returns the parent abstract pathname, or `null` if the pathname does not name a parent directory.
   - Example:
     ```java
     File file = new File("C:/Users/User/example.txt");
     File parentFile = file.getParentFile(); // Output: File object representing "C:/Users/User"
     ```

4. **`public String getPath()`**
   - Converts this abstract pathname into a pathname string.
   - Example:
     ```java
     File file = new File("C:/Users/User/example.txt");
     String path = file.getPath(); // Output: "C:/Users/User/example.txt"
     ```

5. **`public boolean isAbsolute()`**
   - Tests whether this abstract pathname is absolute.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean isAbsolute = file.isAbsolute(); // Output: false
     ```

6. **`public String getAbsolutePath()`**
   - Returns the absolute pathname string.
   - Example:
     ```java
     File file = new File("example.txt");
     String absolutePath = file.getAbsolutePath(); // Output: "C:/Current/Directory/example.txt"
     ```

7. **`public File getAbsoluteFile()`**
   - Returns the absolute form of this abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     File absoluteFile = file.getAbsoluteFile(); // Output: File object representing "C:/Current/Directory/example.txt"
     ```

8. **`public String getCanonicalPath()` throws IOException**
   - Returns the canonical pathname string, resolving symbolic links and relative paths.
   - Example:
     ```java
     File file = new File("example.txt");
     String canonicalPath = file.getCanonicalPath(); // Output: "C:/Current/Directory/example.txt"
     ```

9. **`public File getCanonicalFile()` throws IOException**
   - Returns the canonical form of this abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     File canonicalFile = file.getCanonicalFile(); // Output: File object representing "C:/Current/Directory/example.txt"
     ```

### **4.2 URL and URI Conversion**

1. **`public URL toURL() throws MalformedURLException`**
   - Converts this abstract pathname into a `file:` URL.
   - Example:
     ```java
     File file = new File("example.txt");
     URL fileUrl = file.toURL(); // Deprecated, use toURI().toURL() instead
     ```

2. **`public URI toURI()`**
   - Constructs a `file:` URI that represents this abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     URI fileUri = file.toURI(); // Output: "file:/C:/Current/Directory/example.txt"
     ```

## **5. File Attribute Operations**

### **5.1 Checking File Attributes**

1. **`public boolean canRead()`**
   - Tests whether the application can read the file denoted by this abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean canRead = file.canRead(); // Output: true or false
     ```

2. **`public boolean canWrite()`**
   - Tests whether the application can modify the file denoted by this abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean canWrite = file.canWrite(); // Output: true or false
     ```

3. **`public boolean exists()`**
   - Tests whether the file or directory denoted by this abstract pathname exists.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean exists = file.exists(); // Output: true or false
     ```

4. **`public boolean isDirectory()`**
   - Tests whether the file denoted by this abstract pathname is a directory.
   - Example:
     ```java
     File dir = new File("C:/Users/User");
     boolean isDir = dir.isDirectory(); // Output: true or false
     ```

5. **`public boolean isFile()`**
   - Tests whether the file denoted by this abstract pathname is a normal file.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean isFile = file.isFile(); // Output: true or false
     ```

6. **`public boolean isHidden()`**
   - Tests whether the file denoted by this abstract pathname is hidden.
   - Example:
     ```java
     File file = new File("hiddenFile.txt");
     boolean isHidden = file.isHidden(); // Output: true or false
     ```

7. **`public long lastModified()`**
   - Returns the time the file was last modified.
   - Example:
     ```java
     File file = new File("example.txt");
     long lastModified = file.lastModified(); // Output: time in milliseconds
     ```

8. **`public long length()`**
   - Returns the length of the file in bytes.
   - Example:
     ```java
     File file = new File("example.txt");
     long length = file.length(); // Output: file size in bytes
     ```

### **5.2 Modifying File Attributes**

1. **`public boolean setLastModified(long time)`**
   - Sets the last modified time of the file or directory.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean success = file.setLastModified(System.currentTimeMillis());
     ```

2. **`public boolean setReadOnly()`**
   - Marks the file or directory as read-only.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean success = file.setReadOnly();
     ```

3. **`public boolean setWritable(boolean writable, boolean ownerOnly)`**
   - Sets the owner's or everybody's write permission.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean success = file.setWritable(true, true);
     ```

4. **`public boolean setWritable(boolean writable)`**
   - Sets the write permission for everybody.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean success = file

.setWritable(true);
     ```

5. **`public boolean setReadable(boolean readable, boolean ownerOnly)`**
   - Sets the owner's or everybody's read permission.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean success = file.setReadable(true, true);
     ```

6. **`public boolean setReadable(boolean readable)`**
   - Sets the read permission for everybody.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean success = file.setReadable(true);
     ```

7. **`public boolean setExecutable(boolean executable, boolean ownerOnly)`**
   - Sets the owner's or everybody's execute permission.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean success = file.setExecutable(true, true);
     ```

8. **`public boolean setExecutable(boolean executable)`**
   - Sets the execute permission for everybody.
   - Example:
     ```java
     File file = new File("example.txt");
     boolean success = file.setExecutable(true);
     ```

9. **`public boolean canExecute()`**
   - Tests whether the application can execute the file.
   - Example:
     ```java
     File file = new File("example.bat");
     boolean canExecute = file.canExecute(); // Output: true or false
     ```

## **6. Directory Operations**

### **6.1 Creating and Deleting Files/Directories**

1. **`public boolean createNewFile() throws IOException`**
   - Atomically creates a new, empty file if it does not already exist.
   - Example:
     ```java
     File file = new File("newFile.txt");
     boolean created = file.createNewFile(); // Output: true if the file was created, false if it already exists
     ```

2. **`public boolean delete()`**
   - Deletes the file or directory denoted by this abstract pathname.
   - Example:
     ```java
     File file = new File("newFile.txt");
     boolean deleted = file.delete(); // Output: true if the file or directory was deleted, false otherwise
     ```

3. **`public void deleteOnExit()`**
   - Requests that the file or directory be deleted when the virtual machine terminates.
   - Example:
     ```java
     File file = new File("tempFile.txt");
     file.deleteOnExit();
     ```

4. **`public boolean mkdir()`**
   - Creates the directory named by this abstract pathname.
   - Example:
     ```java
     File dir = new File("newDir");
     boolean created = dir.mkdir(); // Output: true if the directory was created, false otherwise
     ```

5. **`public boolean mkdirs()`**
   - Creates the directory named by this abstract pathname, including any necessary but nonexistent parent directories.
   - Example:
     ```java
     File dirs = new File("parentDir/newDir");
     boolean created = dirs.mkdirs(); // Output: true if the directories were created, false otherwise
     ```

6. **`public boolean renameTo(File dest)`**
   - Renames the file or directory denoted by this abstract pathname.
   - Example:
     ```java
     File oldFile = new File("oldName.txt");
     File newFile = new File("newName.txt");
     boolean renamed = oldFile.renameTo(newFile); // Output: true if the renaming succeeded, false otherwise
     ```

### **6.2 Listing Directory Contents**

1. **`public String[] list()`**
   - Returns an array of strings naming the files and directories in the directory.
   - Example:
     ```java
     File dir = new File("C:/Users/User");
     String[] files = dir.list(); // Output: Array of file/directory names
     ```

2. **`public String[] list(FilenameFilter filter)`**
   - Returns an array of strings naming the files and directories in the directory that satisfy the specified filter.
   - Example:
     ```java
     File dir = new File("C:/Users/User");
     String[] files = dir.list(new FilenameFilter() {
         public boolean accept(File dir, String name) {
             return name.endsWith(".txt");
         }
     }); // Output: Array of .txt file names
     ```

3. **`public File[] listFiles()`**
   - Returns an array of abstract pathnames denoting the files in the directory.
   - Example:
     ```java
     File dir = new File("C:/Users/User");
     File[] files = dir.listFiles(); // Output: Array of File objects
     ```

4. **`public File[] listFiles(FilenameFilter filter)`**
   - Returns an array of abstract pathnames denoting the files and directories in the directory that satisfy the specified filter.
   - Example:
     ```java
     File dir = new File("C:/Users/User");
     File[] files = dir.listFiles(new FilenameFilter() {
         public boolean accept(File dir, String name) {
             return name.endsWith(".txt");
         }
     }); // Output: Array of File objects representing .txt files
     ```

5. **`public File[] listFiles(FileFilter filter)`**
   - Returns an array of abstract pathnames denoting the files and directories in the directory that satisfy the specified filter.
   - Example:
     ```java
     File dir = new File("C:/Users/User");
     File[] files = dir.listFiles(new FileFilter() {
         public boolean accept(File file) {
             return file.isDirectory();
         }
     }); // Output: Array of File objects representing directories
     ```

## **7. File System Operations**

### **7.1 File System Information**

1. **`public static File[] listRoots()`**
   - Lists the available filesystem roots.
   - Example:
     ```java
     File[] roots = File.listRoots(); // Output: Array of File objects representing roots (e.g., C:/, D:/)
     ```

2. **`public long getTotalSpace()`**
   - Returns the size of the partition named by this abstract pathname.
   - Example:
     ```java
     File root = new File("C:/");
     long totalSpace = root.getTotalSpace(); // Output: total space in bytes
     ```

3. **`public long getFreeSpace()`**
   - Returns the number of unallocated bytes in the partition named by this abstract pathname.
   - Example:
     ```java
     File root = new File("C:/");
     long freeSpace = root.getFreeSpace(); // Output: free space in bytes
     ```

4. **`public long getUsableSpace()`**
   - Returns the number of bytes available to this virtual machine on the partition named by this abstract pathname.
   - Example:
     ```java
     File root = new File("C:/");
     long usableSpace = root.getUsableSpace(); // Output: usable space in bytes
     ```

### **7.2 Temporary File Creation**

1. **`public static File createTempFile(String prefix, String suffix, File directory) throws IOException`**
   - Creates an empty file in the specified directory, using the given prefix and suffix to generate its name.
   - Example:
     ```java
     File tempFile = File.createTempFile("temp", ".txt", new File("C:/Temp"));
     ```

2. **`public static File createTempFile(String prefix, String suffix) throws IOException`**
   - Creates an empty file in the default temporary-file directory, using the given prefix and suffix to generate its name.
   - Example:
     ```java
     File tempFile = File.createTempFile("temp", ".txt");
     ```

## **8. Comparison and Equality**

### **8.1 Comparing Files**

1. **`public int compareTo(File pathname)`**
   - Compares two abstract pathnames lexicographically.
   - Example:
     ```java
     File file1 = new File("a.txt");
     File file2 = new File("b.txt");
     int result = file1.compareTo(file2); // Output: negative if file1 < file2, zero if equal, positive if file1 > file2
     ```

2. **`public boolean equals(Object obj)`**
   - Tests this abstract pathname for equality with the given object.
   - Example:
     ```java
     File file1 = new File("example.txt");
     File file2 = new File("example.txt");
     boolean isEqual = file1.equals(file2); // Output: true or false
     ```

3. **`public int hashCode()`**
   - Returns a hash code for this abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     int hash = file.hashCode();
     ```

4. **`public String toString()`**
   - Returns the pathname string of this abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     String path = file.toString(); // Output: "example.txt"
     ```

### **8.2 Path Conversion**

1. **`public Path toPath()`**
   - Returns a `Path` object constructed from this abstract pathname.
   - Example:
     ```java
     File file = new File("example.txt");
     Path path = file.toPath();
     ```

## **9. Static Initialization Block**

- **`static {}`**
  - The static initialization block is used to initialize static variables or execute static code when the class is loaded.
  - Example:
    ```java
    static {
        separatorChar = '/';
        separator = "/";
        // Additional static initialization
    }
    ```

---

This document provides a comprehensive

 overview of the `File` class in Java, covering constructors, path operations, file attributes, directory operations, and more, with detailed examples for each method. This should serve as a valuable reference for understanding and using the `File` class in Java applications.
