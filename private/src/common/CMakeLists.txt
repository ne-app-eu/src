# SPDX-License-Identifier: Apache-2.0
# Copyright 2024-2026, Ne.app (amlal@nekernel.org)
# Licensed under the Apache License, Version 2.0 (see LICENSE file)
# Official repository: https://github.com/ne-app-eu/src

if(DEFINED NEANT_SRC_RELEASE_PROFILE)

	message("NeAnt: Running release CommonCore build...")
	
	project(System.CommonCore.dll)
	
	set(CMAKE_SYSTEM_NAME _COMMONCORE)

	set(CMAKE_SHARED_LIBRARY_PREFIX "")
	set(CMAKE_SHARED_LIBRARY_SUFFIX "")

	add_library(System.CommonCore.dll SHARED Config+DDKGuard.c DDKSanityCheck.S)

	target_compile_definitions(System.CommonCore.dll PRIVATE _NDEBUG __NEOSKRNL__)
	target_include_directories(System.CommonCore.dll PUBLIC ../../../public)
	target_include_directories(System.CommonCore.dll PUBLIC ../../../../nekrnl/private/libDDK/)
	target_include_directories(System.CommonCore.dll PUBLIC ../../../../nekrnl/private/libSystem/)
	target_include_directories(System.CommonCore.dll PUBLIC ../../../../nekrnl/private/)

elseif(DEFINED NEANT_SRC_RELEASE_PROFILE)

	message("NeAnt: Running debug CommonCore build...")

	project(System.CommonCore.dll)
	
	set(CMAKE_SYSTEM_NAME _COMMONCORE)

	set(CMAKE_SHARED_LIBRARY_PREFIX "")
	set(CMAKE_SHARED_LIBRARY_SUFFIX "")

	add_library(System.CommonCore.dll SHARED Config+DDKGuard.c DDKSanityCheck.S)

	target_compile_definitions(System.CommonCore.dll PRIVATE _DEBUG __NEOSKRNL__)
	target_include_directories(System.CommonCore.dll PUBLIC ../../../public)
	target_include_directories(System.CommonCore.dll PUBLIC ../../../../nekrnl/private/libSystem/)
	target_include_directories(System.CommonCore.dll PUBLIC ../../../../nekrnl/private/libDDK/)
	target_include_directories(System.CommonCore.dll PUBLIC ../../../../nekrnl/private/)

endif()
