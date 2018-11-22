# FYAML Specification

version 0.1.2 - 2018-11-21


1. An FYAML implementation operates on the contents of a given directory.
2. An FYAML implementation returns a single YAML string based on the names and contents of the directories and files inside the given directory, though the name of the given directory is irrelevant to the final return value.
3. FYAML always ignores all directories and files that start with `.` ("dot"). 
4. All directory names are considered the names of keys in maps at the level of their parent directory.
5. For files that end in `.yml` or `.yaml`, the name of the files, exclusive of its extension, are considered keys in the map under their parent directory except when the file name starts with `@` or if the file is at the root of the input directory.
6. File names starting with `@` are collapsed as the direct child contents of they map key produced by their parent directory. The name of the file after `@` is irrelevant. Only one file starting with `@` should be allowed per directory.