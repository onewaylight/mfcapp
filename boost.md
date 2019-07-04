# Boost compile
* Download boost library : https://www.boost.org/users/history/version_1_70_0.html
* open Visual Studio 2017 Native Command Line Prompt
* Extract downloaded boost zip files.
* run bootstrap.bat
* run b2 or bjam command with proper argument 
* wait long time
* use it!

```
>bjam --toolset=msvc-14.1 --built-type=complete --prefix=D:\Libs\Boost install
``` 

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


Visual Studio 2017 Project settting for use Boost library

<pre>
Project -> Properties -> Configuration Properties

	C/C++ -> General -> Additional Include Directories : D:\Libs\Boost\include\boost-1_70
	
	Linker -> General -> Additional Library Directories : D:\libs\Boost\lib 
</pre>  




# vxl library usage
* need cmake 
* download and install cmake package


# fftw library usage
* Download recent file. http:///www.fftw.org
* run CMake and configure for x64
* Modify CMAKE_INSTALL_PREFIX : Install final outputs.

```
Project -> Properties -> Configuration Properties

	Debugging -> Environment : PATH=D:\Libs\fftw\bin;%PATH%

	General -> General -> Platform Toolset : Visual Studio 2017 (v141)

	C/C++ -> General -> Additional Include Directories : d:\Libs\fftw\include
	
	Linker -> General -> Additional Library Directories : d:\Libs\fftw\lib 
	          Input -> Additional Dependencies : fftw3.lib 
```

# Performance Problems
* Process Affinity
* Thread Affinity


