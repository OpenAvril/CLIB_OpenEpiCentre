cmake_minimum_required(VERSION 3.10)
project(CLIB_OpenEpiCentre VERSION 1.0)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add shared library
add_library(CLIB_OpenEpiCentre SHARED
        include/CLIB_OpenEpiCentre.h
        src/CLIB_OpenEpiCentre.cpp
        include/engine/structs/Input.h
        src/engine/structs/Input.cpp
        include/engine/structs/Input_Control.h
        src/engine/structs/Input_Control.cpp
        include/engine/structs/Output.h
        src/engine/structs/Output.cpp
        include/engine/structs/Output_Control.h
        src/engine/structs/Output_Control.cpp
        include/engine/structs/Concurrent.h
        src/engine/structs/Concurrent.cpp
        include/engine/structs/Concurrent_Control.h
        src/engine/structs/Concurrent_Control.cpp
        include/engine/structs/User_Input.h
        src/engine/structs/User_Input.cpp
        include/engine/structs/User_Output.h
        src/engine/structs/User_Output.cpp
        include/engine/structs/User_Alogorithm.h
        src/engine/structs/User_Alogorithm.cpp
        include/engine/structs/praise_sets/Algorithm_praise0.h
        src/engine/structs/praise_sets/Algorithm_praise0.cpp
        include/engine/structs/praise_sets/Algorithm_praise1.h
        src/engine/structs/praise_sets/Algorithm_praise1.cpp
        include/engine/structs/praise_sets/Algorithm_praise2.h
        src/engine/structs/praise_sets/Algorithm_praise2.cpp
        include/engine/structs/praise_sets/Algorithm_praise3.h
        src/engine/structs/praise_sets/Algorithm_praise3.cpp
        include/engine/structs/praise_sets/Input_praise0.h
        src/engine/structs/praise_sets/Input_praise0.cpp
        include/engine/structs/praise_sets/Input_praise1.h
        src/engine/structs/praise_sets/Input_praise1.cpp
        include/engine/structs/praise_sets/Input_praise2.h
        src/engine/structs/praise_sets/Input_praise2.cpp
        include/engine/structs/praise_sets/Input_praise3.h
        src/engine/structs/praise_sets/Input_praise3.cpp
        include/engine/structs/praise_sets/Output_praise0.h
        src/engine/structs/praise_sets/Output_praise0.cpp
        include/engine/structs/praise_sets/Output_praise1.h
        src/engine/structs/praise_sets/Output_praise1.cpp
        include/engine/structs/praise_sets/Output_praise2.h
        src/engine/structs/praise_sets/Output_praise2.cpp
        include/engine/structs/praise_sets/Output_praise3.h
        src/engine/structs/praise_sets/Output_praise3.cpp
        include/engine/Framework_Server.h
        src/engine/Framework_Server.cpp
        include/engine/Global.h
        src/engine/Global.cpp
        include/engine/Server.h
        src/engine/Server.cpp
        include/engine/Algorithms.h
        src/engine.Algorithms.cpp
        include/engine/Data.h
        src/engine/Data.cpp
        include/engine/Data_Control.h
        src/engine/Data_Control.cpp
        include/engine/Execute.h
        src/engine/Execute.cpp
        include/engine/Execute_Control.h
        src/engine/Execute_Control.cpp
        include/CLIB_WriteQueForThreadsAt_SERVERINPUTRECIEVE/CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE.h
        include/CLIB_WriteQueForThreadsAt_SERVERINPUTRECIEVE/WriteEnableForThreadsAt_SERVERINPUTRECEIVE_Framework.h
        include/CLIB_WriteQueForThreadsAt_SERVERINPUTRECIEVE/WriteEnableForThreadsAt_SERVERINPUTRECEIVE_Global.h
        include/CLIB_WriteQueForThreadsAt_SERVERINPUTRECIEVE/WriteEnableForThreadsAt_SERVERINPUTRECEIVE.h
        include/CLIB_WriteQueForThreadsAt_SERVERINPUTRECIEVE/WriteEnableForThreadsAt_SERVERINPUTRECEIVE_Control.h

)
target_include_directories(CLIB_OpenEpiCentre PUBLIC include)

add_library(CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE SHARED IMPORTED)
set_target_properties(CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE PROPERTIES
        IMPORTED_LOCATION "CLIB_LaunchEnableForConcurrentThreadsAt_SERVER.so"
)
target_include_directories(CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE INTERFACE "/include/CLIB_WriteQueForThreadsAt_SERVERINPUTRECIEVE")

add_library(CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND SHARED IMPORTED)
set_target_properties(CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND PROPERTIES
        IMPORTED_LOCATION "CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND.so"
)
target_include_directories(CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND INTERFACE "/include/CLIB_WriteQueForThreadsAt_SERVEROUTPUTSEND")

add_library(CLIB_LaunchEnableForConcurrentThreadsAt_SERVER SHARED IMPORTED)
set_target_properties(CLIB_LaunchEnableForConcurrentThreadsAt_SERVER PROPERTIES
        IMPORTED_LOCATION "CLIB_LaunchEnableForConcurrentThreadsAt_SERVER.so"
)
target_include_directories(CLIB_LaunchEnableForConcurrentThreadsAt_SERVER INTERFACE "/include/CLIB_LaunchEnableForConcurrentThreadsAt_SERVER")

# Define include directories for public headers
target_link_libraries(CLIB_OpenEpiCentre PRIVATE CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE)
target_link_libraries(CLIB_OpenEpiCentre PRIVATE CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND)
target_link_libraries(CLIB_OpenEpiCentre PRIVATE CLIB_LaunchEnableForConcurrentThreadsAt_SERVER)
