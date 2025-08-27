
rock_find_qt4(OPTIONAL)
rock_find_qt5(OPTIONAL)

include(RockQt)

rock_qt_vizkit_plugin(
    TARGETPREFIX sbpl_spline_primitives-viz
    QT4_SUFFIX ""
    MISSINGQTDEPS_NOBUILD
    SOURCES SbplSplineVisualization.cpp
    DEPS sbpl_spline_primitives
    MOC SbplSplineVisualization.hpp
    HEADERS SbplSplineVisualization.hpp)

add_subdirectory(gui)

