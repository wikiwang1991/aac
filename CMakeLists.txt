cmake_minimum_required(VERSION 2.6)

project(fdk-aac)

file(GLOB SOURCES
	libAACdec/src/*.cpp
	libAACenc/src/*.cpp
	libPCMutils/src/*.cpp
	libFDK/src/*.cpp
	libSYS/src/*.cpp
	libMpegTPDec/src/*.cpp
	libMpegTPEnc/src/*.cpp
	libSBRdec/src/*.cpp
	libSBRenc/src/*.cpp
)

file(GLOB PUBLIC_HEADERS
  libAACdec/include/*.h
	libAACenc/include/*.h
  libSYS/include/*.h
)

file(GLOB PRIVATE_HEADERS
  libPCMutils/include/*.h
	libFDK/include/*.h
	libMpegTPDec/include/*.h
	libMpegTPEnc/include/*.h
	libSBRdec/include/*.h
	libSBRenc/include/*.h
)

add_library(fdk-aac
	${SOURCES} ${PUBLIC_HEADERS} ${PRIVATE_HEADERS}
)

if (MSVC)
  add_definitions(-D__linux__)
endif ()

target_include_directories(fdk-aac
PUBLIC
	libAACdec/include
	libAACenc/include
	libSYS/include
PRIVATE
	libPCMutils/include
	libFDK/include
	libMpegTPDec/include
	libMpegTPEnc/include
	libSBRdec/include
	libSBRenc/include
)

set_target_properties(fdk-aac PROPERTIES PUBLIC_HEADER "${PUBLIC_HEADERS}")

install(TARGETS fdk-aac
  ARCHIVE DESTINATION lib
  PUBLIC_HEADER DESTINATION include/fdk-aac
)
