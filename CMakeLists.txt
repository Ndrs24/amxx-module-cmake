cmake_minimum_required(VERSION 3.18)
project(mylib)

set(TARGET_NAME ${PROJECT_NAME})

add_library(${TARGET_NAME} SHARED main.cpp sdk/amxxmodule.cpp)

set(DEP_DIR c:/msdk)
target_include_directories(${TARGET_NAME} PRIVATE
  # https://github.com/alliedmodders/amxmodx.git
  ${DEP_DIR}/amxmodx/public 

  # https://github.com/alliedmodders/hlsdk.git
  ${DEP_DIR}/hlsdk/dlls
  ${DEP_DIR}/hlsdk/public
  ${DEP_DIR}/hlsdk/common
  ${DEP_DIR}/hlsdk/engine

  # https://github.com/alliedmodders/metamod-hl1.git
  ${DEP_DIR}/metamod-hl1/metamod
  sdk
)

set_target_properties(${TARGET_NAME} PROPERTIES PREFIX "")
set_target_properties(${TARGET_NAME} PROPERTIES SUFFIX "_amxx.dll")

# set(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/build/lib)
set(LIBRARY_OUTPUT_PATH "C:/Program Files (x86)/Steam/steamapps/common/Half-Life/cstrike/addons/amxmodx/modules")