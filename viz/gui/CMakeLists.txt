find_package(Boost COMPONENTS system filesystem REQUIRED)

rock_qt_library(
    TARGETPREFIX sbpl_viz_gui
    QT4_SUFFIX ""
    SOURCES
        SbplGui.cpp
    HEADERS
        SbplGui.h
    MOC
        SbplGui.h
    DEPS_QT sbpl_spline_primitives-viz
    DEPS_PKGCONFIG base-types
    DEPS_PKGCONFIG_QT vizkit3d vizkit3d-viz base-viz
)

if (ROCK_QT_VERSION_4)
    rock_executable(sbpl_spline_viz_bin
        SOURCES
            main.cpp
        DEPS sbpl_viz_gui)

    target_link_libraries(sbpl_spline_viz_bin ${Boost_SYSTEM_LIBRARY} ${Boost_FILESYSTEM_LIBRARY})

    if (ROCK_QT_VERSION_5)
        rock_executable(sbpl_spline_viz-qt5_bin
            SOURCES
                main.cpp
            DEPS sbpl_viz_gui-qt5)

        target_link_libraries(sbpl_spline_viz-qt5_bin ${Boost_SYSTEM_LIBRARY} ${Boost_FILESYSTEM_LIBRARY})
    endif()
elseif (ROCK_QT_VERSION_5)
    rock_executable(sbpl_spline_viz_bin
        SOURCES
            main.cpp
        DEPS sbpl_viz_gui-qt5)

    target_link_libraries(sbpl_spline_viz_bin ${Boost_SYSTEM_LIBRARY} ${Boost_FILESYSTEM_LIBRARY})
endif()
