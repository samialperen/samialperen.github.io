---
layout: post
title:  "Modern/Contemporary CMake"
author: Alperen
date:   2023-10-30
categories:
  - Software
  - Robotics
---


If you've ever explored blog articles or CMake documentation, you might have encountered the term "contemporary CMake" being frequently referenced. Modern CMake is an approach to configuring CMake that emphasizes the consistent and meticulous use of CMake components.

A CMake component acts as a set of directives detailing how to construct, link with, rely on, and execute a software package. Put simply, a CMake component encapsulates guidelines such as compiler preferences, preprocessor definitions, and dependencies. These directives inform the build system not only on how to compile source files but also on how to utilize the resulting components as dependencies for other libraries.

The significant advantage of modern CMake components lies in their ability to express interdependencies between libraries in a straightforward manner. Suppose componentA relies on componentB within a library known as packageB. In such a scenario, configuring CMake can be as succinct as the following:

```cmake
# Locate the necessary dependency.
find_package(packageB)

# Establish componentA and establish a link to componentB from packageB.
add_library(componentA STATIC componentA.cpp)
target_link_libraries(componentA
    PRIVATE
        packageB::componentB
)
```

The `target_link_libraries` function efficiently manages the setup of componentA to ensure that it links to componentB properly. This involves tasks such as appending the header files of componentB to the search paths for header inclusion when compiling componentA, linking the libraries of componentB to componentA (including all the dependent libraries componentB relies on), and propagating compiler preferences and definitions affecting componentB's public interface to componentA.

This approach is termed "modern" as it replaces previous CMake practices where a software package wasn't defined via a target. In the older CMake paradigm, a package discovered using `find_package` would conventionally define two variables:

- `packageB_INCLUDE_DIRS`: These are the paths to include for locating packageB's header files.
- `packageB_LIBRARIES`: These are the paths to the libraries exported by packageB, which our targets can link to.

This approach had its drawbacks:

- Developers needed to be cautious and accurately employ these variables. Instead of explicitly declaring a dependency, developers had to manually specify which `packageB_INCLUDE_DIRS` files to include and which `packageB_LIBRARIES` libraries to link.
- This system didn't automatically track transitive dependencies. If packageB depended on packageC, the developer of componentA needed to `find_package(packageC)` and manually link to packageC — and in the correct order.

Modern CMake components alleviate these concerns for us.

Regrettably, some vestiges of the older CMake practices persist in the C++ libraries landscape. A few C++ libraries are so widely used that the CMake installer includes scripts for detecting them on the host operating system. Prominent examples include `Boost`, `OpenSSL`, and `CURL`, for which CMake ships with `FindBoost.cmake`, `FindOpenSSL.cmake`, and `FindCURL.cmake` scripts to facilitate detection when using `find_package`.

However, some of these scripts still employ older CMake methodologies. In some instances, they fail to define targets at all, while in others, the targets defined are not in alignment with modern CMake principles. For instance, `FindCURL.cmake` does create a target `CURL::libcurl`, but this target doesn't actively seek out transitive dependencies; developers must find them independently.

<center> 
  <script type='text/javascript' src='https://storage.ko-fi.com/cdn/widget/Widget_2.js'></script><script type='text/javascript' style="text-align:center">kofiwidget2.init('Buy Me a Coffee', '#e08428', 'V7V3IDOGW');kofiwidget2.draw();</script> 
</center>
