##############################
PROJECT( vanishingPoint )
##############################
cmake_minimum_required (VERSION 2.6)

# Packages
find_package( OpenCV REQUIRED )

OPTION ( ENABLE_LMFIT "Enable usage of lmfit library" OFF)
IF( ENABLE_LMFIT )
	add_definitions( -DUSE_LMFIT )
ENDIF( ENABLE_LMFIT )

# Includes
include_directories(	
	${OPENCV_INCLUDE_DIR}
	${PROJECT_BINARY_DIR}
)

set(SOURCE_FILES 
	main.cpp
	MSAC.cpp
	MSAC.h
	errorNIETO.h
	errorNIETO.cpp
)

IF( ENABLE_LMFIT )
set( SOURCE_FILES 
	${SOURCE_FILES} 
	lmmin.h
	lmmin.cpp
)
ENDIF( ENABLE_LMFIT )


# Add executable and target link libraries
ADD_EXECUTABLE( vanishingPoint ${SOURCE_FILES})
TARGET_LINK_LIBRARIES( vanishingPoint ${OpenCV_LIBS})


