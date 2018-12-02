#### C++ coding style

Changes to the code should conform to
[Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html).
except for type_aliases where we make use of **snake_case**


Use `clang-tidy` to check your C/C++ changes. To install `clang-tidy` on ubuntu:16.04, do:

```bash
apt-get install -y clang-tidy
```

You can check a C/C++ file by doing:


```bash
clang-format <my_cc_file> --style=google > /tmp/my_cc_file.cc
diff <my_cc_file> /tmp/my_cc_file.cc
```
