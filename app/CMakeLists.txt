cmake_minimum_required(VERSION 3.4.1)

add_library( lgdeffective-bitmap
             SHARED
             src/main/cpp/lgdeffective-bitmap.c )


include_directories( src/main/cpp/jpeg/
                     )

add_library(lgdjpegbither SHARED IMPORTED)
set_target_properties(lgdjpegbither
  PROPERTIES IMPORTED_LOCATION
  ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI}/liblgdjpegbither.so)


find_library( log-lib
              log )

find_library( jnigraphics-lib jnigraphics )

target_link_libraries( lgdeffective-bitmap
                       lgdjpegbither
                       ${log-lib}
                       ${jnigraphics-lib})