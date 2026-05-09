cmake_minimum_required(VERSION 3.16)

project(bsatk LANGUAGES CXX)

include(CMakePackageConfigHelpers)
include(GNUInstallDirs)

add_subdirectory(src)

configure_package_config_file(${CMAKE_CURRENT_SOURCE_DIR}/cmake/config.cmake.in
  "${CMAKE_CURRENT_BINARY_DIR}/mo2-bsatk-config.cmake"
  INSTALL_DESTINATION "${CMAKE_INSTALL_LIBDIR}/cmake/mo2-bsatk"
  NO_SET_AND_CHECK_MACRO
  NO_CHECK_REQUIRED_COMPONENTS_MACRO
)

include(${CMAKE_CURRENT_SOURCE_DIR}/Version.cmake)
set(BSATK_VERSION
  ${BSATK_MAJOR_VERSION}.${BSATK_MINOR_VERSION}.${BSATK_PATCH_VERSION})

write_basic_package_version_file(
  "${CMAKE_CURRENT_BINARY_DIR}/mo2-bsatk-config-version.cmake"
  VERSION "${BSATK_VERSION}"
  COMPATIBILITY AnyNewerVersion
)

install(FILES
  ${CMAKE_CURRENT_BINARY_DIR}/mo2-bsatk-config.cmake
  ${CMAKE_CURRENT_BINARY_DIR}/mo2-bsatk-config-version.cmake
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/mo2-bsatk
)
