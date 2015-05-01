project( visualino )
add_definitions ( -Wall )

find_package(Qt5Widgets)
find_package(Qt5WebKitWidgets)
find_package(Qt5SerialPort)
find_package(Qt5LinguistTools)

if (APPLE)
	set(MACOSX_BUNDLE_ICON_FILE icons/os_freebsd.icns )
	set(MACOSX_BUNDLE_BUNDLE_NAME visualino)
endif ()

set (CMAKE_AUTOMOC ON)
set (CMAKE_AUTORCC ON)
set (CMAKE_AUTOUIC ON)

set (
  visualino_SRCS
  main.cpp
  mainwindow.cpp
  settingsdialog.cpp
  settingsstore.cpp
  graphwidget.cpp
  aboutdialog.cpp
)

file(GLOB TRANS "../ts/*.ts")
qt5_add_translation(QM ${TRANS})

add_executable (
  visualino
  Resources.qrc
  mainwindow.ui
  settingsdialog.ui
  aboutdialog.ui
  ${visualino_SRCS}
  ${QM}
)

target_link_libraries (
  visualino
  Qt5::Widgets
  Qt5::WebKitWidgets
  Qt5::SerialPort
)
