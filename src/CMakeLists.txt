project( visualino )
add_definitions ( -Wall )

find_package(Qt5Widgets)
find_package(Qt5WebKitWidgets)
find_package(Qt5SerialPort)

if (APPLE)
	set( MACOSX_BUNDLE_ICON_FILE icons/os_freebsd.icns )
	set(MACOSX_BUNDLE_BUNDLE_NAME visualino)
endif ()

set (CMAKE_AUTOMOC ON)

set ( visualino_SRCS
	main.cpp
	mainwindow.cpp
	settingsdialog.cpp
	settingsstore.cpp
	graphwidget.cpp
	aboutdialog.cpp
	)



qt5_wrap_ui(
	UIS
	mainwindow.ui
	settingsdialog.ui
	aboutdialog.ui
	)

qt5_add_resources(RSCS Resources.qrc)

add_executable (
	visualino
	${visualino_SRCS}
	${UIS}
	${RSCS}
	)

target_link_libraries (
	visualino
	Qt5::Widgets
	Qt5::WebKitWidgets
	Qt5::SerialPort
	)
