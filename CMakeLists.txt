cmake_minimum_required(VERSION 2.6)

project(libFraunhoferAAC)

file(GLOB srcs
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

add_library(libFraunhoferAAC
	${srcs}
)

target_include_directories(libFraunhoferAAC PUBLIC
	libAACdec/include
	libAACenc/include
	libPCMutils/include
	libFDK/include
	libSYS/include
	libMpegTPDec/include
	libMpegTPEnc/include
	libSBRdec/include
	libSBRenc/include
)
