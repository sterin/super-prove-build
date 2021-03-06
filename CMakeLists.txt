cmake_minimum_required(VERSION 3.3.0)

include(CMakeToolsHelper OPTIONAL)

project(super_prove)

include(cmake/pyabc.cmake)

add_subdirectory(abc EXCLUDE_FROM_ALL)

set(ZZ_USE_EXTERNAL_LIBABC TRUE)
add_subdirectory(abc-zz EXCLUDE_FROM_ALL)

add_subdirectory(pywrapper EXCLUDE_FROM_ALL)
add_subdirectory(pyzz EXCLUDE_FROM_ALL)
add_subdirectory(pyabc EXCLUDE_FROM_ALL)

install_python_module(pyzz/pyzz)
install_python_module(pyabc/pyabc)
install_python_module(pyaig/pyaig)
install_python_module(pyliveness)
install_python_module(super_prove)
install_python_requirements(requirements.txt)

install_target(bip.exe DESTINATION bin RENAME bip)
install_target(pyabc.exe DESTINATION bin RENAME abc.exe)

install(PROGRAMS pyabc/scripts/abc.sh RENAME abc DESTINATION bin)
install(FILES super_prove/abc.rc DESTINATION lib/super_prove)

file(GLOB sh_scripts "super_prove/*.sh")
install(PROGRAMS ${sh_scripts} DESTINATION bin)

pyabc_install_support_libraries(pyabc.exe bip.exe)
