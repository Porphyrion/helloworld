cmake_minimum_required(VERSION 3.2)

project(helloworld VERSION $ENV{TRAVIS_BUILD_NUMBER})

configure_file(version.h.in version.h)

add_executable(helloworld_cli main.cpp)

set_target_properties(helloworld_cli PROPERTIES
	CXX_STANDART 14
	CXX_STANDART_REQUIRED ON
	COMPILE_OPTION -Wpedantic -Wall -Wextra
	)

install(TARGETS helloworld_cli RUNTIME DESTINATION bin)

set(CPACK_GENERATOR DEB)

set(CPACK_PACKEGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKEGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKEGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")

set(CPACK_PACKAGE_CONTACT ivanbasurman88@yandex.ru)

include(CPack)







