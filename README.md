# python-c-mixing

Examples of mixing Python and C.

[\[中文講解\] 如Py似C：Python 與 C 的共生法則](https://pyliaorachel.github.io/blog/tech/python/2018/01/26/python-c-mixing.html)

## Python call C

###### Basic

```bash
$ cd python-call-c/basic

# Build module, generates *.so in the same directory
$ python3 setup.py build_ext --inplace

# Run
$ python3 main.py
```

###### ctypes

```bash
$ cd python-call-c/ctypes

# Build shared library *.so
$ gcc -shared -fPIC speedup_performance.c -o speedup_performance.so

# Run
$ python3 main.py
```

###### SWIG

```bash
# Install (macOS with homebrew)
$ brew install swig
```

```bash
$ cd python-call-c/swig

# Build python module with keyword arguments
# Generates *.py, *_wrap.c
$ swig -python -keyword speedup_performance.i

# Build shared object file *.so
$ python3 setup.py build_ext --inplace

# Run
$ python3 main.py

```

## C call Python

###### Basic

```bash
$ cd c-call-python/basic

# Build executable file (python3)
$ gcc $(python3-config --cflags --ldflags) main.c -o main

# Run
$ ./main
```

###### Cython

```bash
# Install
$ pip3 install Cython
```

```bash
$ cd c-call-python/cython

# Build module, generates *.so, *.c, *.h in the same directory
$ python3 setup.py build_ext --inplace

# Build executable file (python3)
$ gcc $(python3-config --cflags --ldflags) main.c speedup_dev_and_performance.c -o main

# Run
$ ./main
```
