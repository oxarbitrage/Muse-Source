
# for each subdirectory containing a CMakeLists.txt, add that subdirectory

file( GLOB children RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} * )
foreach( child ${children} )
   if( IS_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/${child}" )
      if( EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/${child}/CMakeLists.txt" )
         add_subdirectory( "${child}" )
         set( ENV{MUSE_EXTERNAL_PLUGINS} $ENV{MUSE_EXTERNAL_PLUGINS} ${child} )
      endif()
   endif()
endforeach()

# add_subdirectory( hello_api )
# add_subdirectory( hello_arguments )
# add_subdirectory( hello_objects )