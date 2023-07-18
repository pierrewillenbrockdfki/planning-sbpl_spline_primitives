find_package(Boost COMPONENTS system filesystem REQUIRED)

if (ROCK_QT_VERSION_4)
    rock_library(sbpl_viz_gui
        SOURCES
            SbplGui.cpp
        HEADERS
            SbplGui.h
        MOC
            SbplGui.h
        DEPS sbpl_spline_primitives-viz
        DEPS_PKGCONFIG vizkit3d base-types vizkit3d-viz base-viz
    )
endif(ROCK_QT_VERSION_4)

if (ROCK_QT_VERSION_5)
    rock_library(sbpl_viz_gui-qt5
        SOURCES
            SbplGui.cpp
        HEADERS
            SbplGui.h
        MOC5
            SbplGui.h
        DEPS sbpl_spline_primitives-viz-qt5
        DEPS_PKGCONFIG vizkit3d-qt5 base-types vizkit3d-viz-qt5 base-viz-qt5
    )
endif(ROCK_QT_VERSION_5)

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
