string(TOLOWER ${CMAKE_SYSTEM_NAME} PLATFORM_SUFFIX)

add_library(garrysmod_scanning STATIC source/${PLATFORM_SUFFIX}/symbolfinder.cpp)
add_library(gmod::scanning ALIAS garrysmod_scanning)

target_include_directories(garrysmod_scanning PUBLIC include)
target_include_directories(garrysmod_scanning PRIVATE include/scanning)
target_link_libraries(garrysmod_scanning ${CMAKE_DL_LIBS})

# Let everyone know that scanning was included
set(SCANNING_FOUND TRUE CACHE INTERNAL "SCANNING_FOUND")
