- [CMake使用MSVC时链接MT多线程静态库](#cmake使用msvc时链接mt多线程静态库)
  - [通过CXX FLAGS](#通过cxx-flags)
  - [通过target\_compile\_option指定单个target](#通过target_compile_option指定单个target)
  - [通过CMAKE\_MSVC\_RUNTIME\_LIBRARY](#通过cmake_msvc_runtime_library)

# CMake使用MSVC时链接MT多线程静态库

不做任何配置时，MSVC默认使用MD编译

例如，代码中使用`printf`，则会在编译产物中引入符号

|   Symbol   |            Which DLL             |
| :--------: | :------------------------------: |
|    puts    | api-ms-win-crt-stdio-\|1-1-0.dll |
| _set_fmode | api-ms-win-crt-stdio-\|1-1-0.dll |
| _p_commode | api-ms-win-crt-stdio-\|1-1-0.dll |

使用MT编译后，产物将不依赖VCRUNTIME和crt-runtime，而是直接依赖Kernel32中的函数。

## 通过CXX FLAGS

CXX FLAGS用来构造编译时编译器的命令行参数，该修改是全局的，如果没有被提前传入/MD，则该修改必然成功：

```CMake
if(MSVC)
    set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")
endif()
```

## 通过target_compile_option指定单个target

直接修改CXX FLAGS影响是全局的，为了控制在单个target中

```CMake
if(MSVC)
    target_compile_options(MyProject PRIVATE
        $<$<CONFIG:Release>:/MT>
        $<$<CONFIG:Debug>:/MTd>
    )
endif()
```

## 通过CMAKE_MSVC_RUNTIME_LIBRARY

- CMAKE最低版本需求3.15
- 必须要在project或者enable_lanuage之前，设置policy CMP0091为NEW才能生效

```CMake
cmake_policy(SET CMP0091 TRUE)

project(XXX)

if(MSVC)
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()
```
