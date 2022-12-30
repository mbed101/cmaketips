# cmaketips

## To always use latest c++ standard 
### msvc compiler
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /O2 /EHsc /std:c++latest /Zc:__cplusplus -D_WIN32_WINNT=0x0601")
