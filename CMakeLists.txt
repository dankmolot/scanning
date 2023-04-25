string(TOLOWER ${CMAKE_SYSTEM_NAME} PLATFORM_SUFFIX)
if(${PLATFORM_SUFFIX} STREQUAL "darwin")
    SET(PLATFORM_SUFFIX "macosx")
endif()

add_library(garrysmod_scanning STATIC EXCLUDE_FROM_ALL source/${PLATFORM_SUFFIX}/symbolfinder.cpp)
add_library(gmod::scanning ALIAS garrysmod_scanning)

target_include_directories(garrysmod_scanning PUBLIC include)
target_include_directories(garrysmod_scanning PRIVATE include/scanning)
target_link_libraries(garrysmod_scanning ${CMAKE_DL_LIBS})
set_target_properties(garrysmod_scanning PROPERTIES FOLDER "garrysmod")

# Let everyone know that scanning was included
set(SCANNING_FOUND TRUE CACHE INTERNAL "SCANNING_FOUND")
