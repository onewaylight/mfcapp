# Boost compile
* open visual studio command line 
* run bootstrap.bat
* run b2
* wait long time

run Visual Studio 2017 Native Command line prompt
Download most recent boost library source to local folder.

https://www.boost.org/users/history/version_1_70_0.html

```bjam --toolset=msvc-14.1 --built-type=complete --prefix=d:\Libs\Boost install``` 

**toolset**: Use this to specify the Visual C++ compiler to use. For Visual Studio 2017, this is msvc-14.1. 

You can check out in Visual Studio project property page.
```
Project -> Properties -> Configuration Properties
  General -> General -> Platform Toolset : Visual Studio 2017 (v141)
```

**architecture**: This is the processor architecture. Keep this x86 for both 32-bit and 64-bit builds!

**address-model**: Use this to specify whether you want 32 or 64 bit library to be built.

**-j**: Use this to specify how many cores to use for parallel compilation.

**--prefix**: Will be installed at descripted location.


  
  




# vxl library usage
* need cmake 
* download and install cmake package


# fftw library usage

# Performance Problems
* Process Affinity
* Thread Affinity


