cmake_minimum_required(VERSION 3.10)
project(CLIB_OpenEpiCentre VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(CLIB_OpenEpiCentre SHARED
        include/CLIB_OpenEpiCentre.h
        src/CLIB_OpenEpiCentre.cpp
        include/engine/Framework_Server.h
        src/engine/Framework_Server.cpp
        include/engine/Global.h
        src/engine/Global.cpp
        include/structs/Input.h
        src/structs/Input.cpp
        include/structs/Output.h
        src/structs/Output.cpp
        include/structs/Concurrent.h
        src/structs/Concurrent.cpp
        include/structs/User_Input.h
        src/structs/User_Input.cpp
        include/structs/User_Output.h
        src/structs/User_Output.cpp
        include/structs/User_Algorithm.h
        src/structs/User_Algorithm.cpp
        include/structs/praise_sets/Algorithm_praise0.h
        src/structs/praise_sets/Algorithm_praise0.cpp
        include//structs/praise_sets/Input_praise0.h
        src/structs/praise_sets/Input_praise0.cpp
        include/structs/praise_sets/Output_praise0.h
        src/structs/praise_sets/Output_praise0.cpp
        include/engine/Server.h
        src/engine/Server.cpp
        include/engine/Algorithms.h
        src/engine/Algorithms.cpp
        include/engine/Data.h
        src/engine/Data.cpp
        include/engine/Data_Control.h
        include/engine/Execute.h
        src/engine/Execute.cpp
        include/engine/Execute_Control.h
        src/engine/Execute_Control.cpp
        include/CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE/CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE.h
        include/CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE/WriteEnableForThreadsAt_SERVERINPUTRECEIVE_Framework.h
        include/CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE/WriteEnableForThreadsAt_SERVERINPUTRECEIVE_Global.h
        include/CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE/WriteEnableForThreadsAt_SERVERINPUTRECEIVE.h
        include/CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE/WriteEnableForThreadsAt_SERVERINPUTRECEIVE_Control.h
        include/CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND/CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND.h
        include/CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND/WriteEnableForThreadsAt_SERVEROUTPUTSEND_Framework.h
        include/CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND/WriteEnableForThreadsAt_SERVEROUTPUTSEND_Global.h
        include/CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND/WriteEnableForThreadsAt_SERVEROUTPUTSEND.h
        include/CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND/WriteEnableForThreadsAt_SERVEROUTPUTSEND_Control.h
        include/CLIB_LaunchEnableForConcurrentThreadsAt_SERVER/CLIB_LaunchEnableForConcurrentThreadsAt_SERVER.h
        include/CLIB_LaunchEnableForConcurrentThreadsAt_SERVER/LaunchEnableForConcurrentThreadsAt_SERVER_Framework.h
        include/CLIB_LaunchEnableForConcurrentThreadsAt_SERVER/LaunchEnableForConcurrentThreadsAt_SERVER_Global.h
        include/CLIB_LaunchEnableForConcurrentThreadsAt_SERVER/LaunchEnableForConcurrentThreadsAt_SERVER.h
        include/CLIB_LaunchEnableForConcurrentThreadsAt_SERVER/LaunchEnableForConcurrentThreadsAt_SERVER_Control.h
)
find_library(CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE_LIB_PATH
        NAMES CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE
        PATHS ${CMAKE_CURRENT_SOURCE_DIR}/libs/CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE
        NO_DEFAULT_PATH
)
target_link_libraries(CLIB_OpenEpiCentre PRIVATE
        ${CLIB_WriteEnableForThreadsAt_SERVERINPUTRECEIVE_LIB_PATH}
)

find_library(CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND_LIB_PATH
        NAMES CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND          # Name without 'libs' or '.so'
        PATHS ${CMAKE_CURRENT_SOURCE_DIR}/libs/CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND
        NO_DEFAULT_PATH
)
target_link_libraries(CLIB_OpenEpiCentre PRIVATE
        ${CLIB_WriteEnableForThreadsAt_SERVEROUTPUTSEND_LIB_PATH}
)

find_library(CLIB_LaunchEnableForConcurrentThreadsAt_SERVER_LIB_PATH
        NAMES CLIB_LaunchEnableForConcurrentThreadsAt_SERVER          # Name without 'libs' or '.so'
        PATHS ${CMAKE_CURRENT_SOURCE_DIR}/libs/CLIB_LaunchEnableForConcurrentThreadsAt_SERVER
        NO_DEFAULT_PATH
)
target_link_libraries(CLIB_OpenEpiCentre PRIVATE
        ${CLIB_LaunchEnableForConcurrentThreadsAt_SERVER_LIB_PATH}
)

set_target_properties(${PROJECT_NAME} PROPERTIES
    LIBRARY_OUTPUT_DIRECTORY ./libs
)