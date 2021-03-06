# ---
# p3dConvert* additions for .blend conversion for http://p3d.in viewer
# 
# Changes (c) 2014 Nathan Letwory ( nathan@p3d.in )
# ---

#------------------------------------------------------------------------------
#   This file is part of FBT (File Binary Tables).
#   http://gamekit.googlecode.com/
#
#   Copyright (c) 2010 Charlie C & Erwin Coumans.
#
#------------------------------------------------------------------------------
# This software is provided 'as-is', without any express or implied
# warranty. In no event will the authors be held liable for any damages
# arising from the use of this software.
#
# Permission is granted to anyone to use this software for any purpose,
# including commercial applications, and to alter it and redistribute it
# freely, subject to the following restrictions:
#
# 1. The origin of this software must not be misrepresented; you must not
#	claim that you wrote the original software. If you use this software
#	in a product, an acknowledgment in the product documentation would be
#	appreciated but is not required.
# 2. Altered source versions must be plainly marked as such, and must not be
#	misrepresented as being the original software.
# 3. This notice may not be removed or altered from any source distribution.
#------------------------------------------------------------------------------
#include(FlexBison)

set(File_SRC
	fbtFile.cpp
	fbtTables.cpp
	fbtTypes.cpp
	fbtStreams.cpp
	fbtBuilder.cpp
)

set(File_HDR
	fbtFile.h
	fbtTables.h
	fbtBuilder.h
	fbtTypes.h
	fbtConfig.h
	fbtStreams.h
	fbtPlatformHeaders.h
)

# only for updating scanner 
#add_flex(fbtScanner File_HDR fbtScanner.l fbt)
set(fbtScanner Generated/fbtScanner.inl)

include_directories(${P3dConverter_ZLIB_INCLUDE} ${P3dConverter_BINARY_DIR}/zlib)
link_libraries(zlibstatic)

add_library(fbtFile SHARED ${File_SRC} ${File_HDR} ${fbtScanner})
