project(lxqt-config-input)
# newer cmake is required for CMAKE_AUTOMOC Qt support
cmake_minimum_required(VERSION 2.8.6)

find_package(Qt4 REQUIRED QtCore QtGui) # Qt
find_package(X11 REQUIRED) # X11

# add src subdirectory
add_subdirectory(src)

# install a desktop entry file
configure_file(data/lxqt-config-input.desktop.in lxqt-config-input.desktop @ONLY)
install(
  FILES ${CMAKE_CURRENT_BINARY_DIR}/lxqt-config-input.desktop
  DESTINATION share/applications
)

# building tarball with CPack -------------------------------------------------
# To create a source distribution, type:
# make package_source
include (InstallRequiredSystemLibraries)
set (CPACK_RESOURCE_FILE_LICENSE "${CMAKE_CURRENT_SOURCE_DIR}/COPYING")
set (CPACK_RESOURCE_FILE_README "${CMAKE_CURRENT_SOURCE_DIR}/README")
set (CPACK_PACKAGE_VENDOR "")
set (CPACK_PACKAGE_VERSION_MAJOR "0")
set (CPACK_PACKAGE_VERSION_MINOR "1")
set (CPACK_PACKAGE_VERSION_PATCH "0")
set (CPACK_GENERATOR TBZ2)
set (CPACK_SOURCE_GENERATOR TBZ2)
set (CPACK_SOURCE_IGNORE_FILES /build/;.gitignore;.*~;.git;.kdev4;temp)
include (CPack)
