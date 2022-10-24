# Pathlib - Cheatsheet

An object oriented way to deal with filesystem paths in Python, more convenient than using `os.path.join()` etc.

### Imports
```python
from pathlib import Path
```
### Constructing paths
```python
>>> Path('folder') / 'subfolder' / 'file.txt'     
>>> Path('folder').joinpath('subfolder').joinpath('file.txt')
# PosixPath('/folder/subfolder/file.txt')
```

### Properties of `Path()`
```python
>>> p = Path('folder') / 'subfolder' / 'file.txt'
>>> p                   # PosixPath('folder/subfolder/file.txt')
>>> p.parent            # 
>>> p.name              # 'file.txt'
>>> p.suffix            # '.txt'
>>> p.drive             # '' (more useful on windows?)

```

### Accessing parts of paths
```python
>>> p = Path('folder') / 'subfolder' / 'file.txt'
>>> p               # PosixPath('folder/subfolder/file.txt')
>>> p.parent        # PosixPath('folder/subfolder')
>>> p.name          # 'file.txt'
>>> p.suffix        # '.txt'
>>> p.drive         # '' (more useful on windows: 'D:')

>>> a = p.absolute()
>>> a               # PosixPath('/workspaces/project_folder/folder/subfolder/file.txt')
>>> a.parent        # PosixPath('/workspaces/project_folder/folder/subfolder')
```

# Parts
```python
>>> p = Path('folder') / 'subfolder' / 'file.txt'
>>> a = p.absolute()
>>> print(a)
#  '/workspaces/project_folder/folder/subfolder/file.txt'
#   └──────────────── a.parent ───────────────┘
#                                     a.name -> └──────┘
#                                     a.stem -> └──┘
#                                   a.suffix -----> └──┘
```

### Methods of `Path()`
```python
>>> p = Path('folder') / 'subfolder' / 'file.txt'
>>> p               # PosixPath('folder/subfolder/file.txt')
>>> p.absolute()    # PosixPath('/workspaces/project_folder/folder/subfolder/file.txt')
>>> p.is_file()     # True
>>> p.is_dir()      # False
```

### Other handy snippets
```python
>>> Path.cwd()      # PosixPath('/workspaces/project_folder')

```

# Changing file extensions
```python
>>> Path('file.txt').with_suffix('.jpg')    # PosixPath('file.jpg')
>>> Path('file.txt').stem + '.jpg'          # PosixPath('file.jpg')
```
