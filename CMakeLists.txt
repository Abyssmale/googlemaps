cmake_minimum_required(VERSION 3.16)

project(qtgeoservices_googlemaps LANGUAGES CXX)

# Enable automoc and plugin compilation
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

# Define plugin target
add_library(qtgeoservices_googlemaps MODULE)

# Set output directories (optional)
set_target_properties(qtgeoservices_googlemaps PROPERTIES
    LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/plugins/geoservices
)



# Define sources
target_sources(qtgeoservices_googlemaps PRIVATE
    qgeoserviceproviderplugingooglemaps.cpp
    qgeocodingmanagerenginegooglemaps.cpp
    qgeocodereplygooglemaps.cpp
    qgeoroutingmanagerenginegooglemaps.cpp
    qgeoroutereplygooglemaps.cpp
    qplacemanagerenginegooglemaps.cpp
    qplacesearchreplygooglemaps.cpp
    qplacecategoriesreplygooglemaps.cpp
    qgeomapreplygooglemaps.cpp
    qgeotiledmapgooglemaps.cpp
    qgeotiledmappingmanagerenginegooglemaps.cpp
    qgeotilefetchergooglemaps.cpp
    qplacesearchsuggestionreplyimpl.cpp
    qgeoerror_messages.cpp

    qgeoserviceproviderplugingooglemaps.h
    qgeocodingmanagerenginegooglemaps.h
    qgeocodereplygooglemaps.h
    qgeoroutingmanagerenginegooglemaps.h
    qgeoroutereplygooglemaps.h
    qplacemanagerenginegooglemaps.h
    qplacesearchreplygooglemaps.h
    qplacecategoriesreplygooglemaps.h
    qgeomapreplygooglemaps.h
    qgeotiledmapgooglemaps.h
    qgeotiledmappingmanagerenginegooglemaps.h
    qgeotilefetchergooglemaps.h
    qplacesearchsuggestionreplyimpl.h
    qgeoerror_messages.h
)

# Include directories
target_include_directories(qtgeoservices_googlemaps PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/..
)

# Required Qt modules
find_package(Qt6 REQUIRED COMPONENTS
    Core
    Network
    Positioning
    Location
)

# Optional private modules (if available)
find_package(Qt6 REQUIRED COMPONENTS
    PositioningPrivate
    LocationPrivate
)

# Link Qt libraries
target_link_libraries(qtgeoservices_googlemaps PRIVATE
    Qt6::Core
    Qt6::Network
    Qt6::Positioning
    Qt6::Location
    Qt6::PositioningPrivate
    Qt6::LocationPrivate
)

# Plugin installation path
install(TARGETS qtgeoservices_googlemaps
    LIBRARY DESTINATION ${QT6_INSTALL_PLUGINS}/geoservices
)
