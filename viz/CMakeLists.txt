
rock_find_qt4(OPTIONAL)
rock_find_qt5(OPTIONAL)

if (ROCK_QT_VERSION_4)
rock_vizkit_plugin(sbpl_spline_primitives-viz
    SbplSplineVisualization.cpp
    DEPS sbpl_spline_primitives
    MOC SbplSplineVisualization.hpp
    HEADERS SbplSplineVisualization.hpp)
endif()

if (ROCK_QT_VERSION_5)
rock_vizkit_plugin_qt5(sbpl_spline_primitives-viz-qt5
    SbplSplineVisualization.cpp
    DEPS sbpl_spline_primitives
    MOC5 SbplSplineVisualization.hpp
    HEADERS SbplSplineVisualization.hpp)
endif()
    
add_subdirectory(gui)    

