# Interface libraries to set common defines and includes, avoid duplication later
add_library(g_wwcommon INTERFACE)

target_link_libraries(g_wwcommon INTERFACE
    core_config
    core_utility
    core_wwcommon
    d3d8lib
    milesstub
    stlport
)

target_include_directories(g_wwcommon INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}
    WW3D2
)

add_subdirectory(WWAudio)
add_subdirectory(WW3D2)
add_subdirectory(WWDownload)

# Helpful interface to bundle the ww modules together.
add_library(g_wwvegas INTERFACE)

target_include_directories(g_wwvegas INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}
    WW3D2
)

target_link_libraries(g_wwvegas INTERFACE
    core_wwvegas
    g_ww3d2
    g_wwdownload
)
