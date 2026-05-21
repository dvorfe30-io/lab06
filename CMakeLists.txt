cmake_minimum_required(VERSION 3.10)
project(lab06)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(PRINT_VERSION_MAJOR 1)
set(PRINT_VERSION_MINOR 0)
set(PRINT_VERSION_PATCH 0)
set(PRINT_VERSION_TWEAK "beta")

add_subdirectory(formatter_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(solver_lib)
add_subdirectory(hello_world_application)
add_subdirectory(solver_application)

install(TARGETS formatter formatter_ex solver
	ARCHIVE DESTINATION lib
	LIBRARY DESTINATION lib
	RUNTIME DESTINATION bin)
install(TARGETS solver_application
	RUNTIME DESTINATION bin)
install(DIRECTORY formatter_lib/ formatter_ex_lib/ solver_lib/
	DESTINATION include
	FILES_MATCHING PATTERN "*.h")

set(CPACK_PACKAGE_CONTACT ${GITHUB_EMAIL})
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "dvorfe30-io")
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "solver application")
set(CPACK_PACKAGE_VERSION_MAJOR ${PRINT_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR ${PRINT_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH ${PRINT_VERSION_PATCH})
set(CPACK_PACKAGE_VERSION_TWEAK ${PRINT_VERSION_TWEAK})

include(CPack)
