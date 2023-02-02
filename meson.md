# Meson scripts 

## GLAD

Dependencies
```
pip install glad
```


meson.build
```
project(
    'glad', 'c',
    version: '0.1.0'
)

python = import('python').find_installation(modules: 'glad')

run_command(
    python, '-m', 'glad',
    '--api', 'gl:core=4.3',
    '--out-path', '.',
    check: true
)

include = include_directories('include')
glad_lib = library(
    'glad',
    sources: 'src/gl.c',
    include_directories: include
)

glad_dep = declare_dependency(
    link_with: glad_lib,
    include_directories: include
)
```

## miniaudio

```
run_command(
    'curl', '--create-dirs',
    '-o', 'include/miniaudio.h',
    'https://raw.githubusercontent.com/mackron/miniaudio/master/miniaudio.h',
    check: true
)
```