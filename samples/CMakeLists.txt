link_libraries(synergy)

add_executable(matrix_mul matrix_mul/matrix_mul.cpp)
add_executable(query_freq query_freq/query_freq.cpp)
add_executable(saxpy saxpy/saxpy.cpp)

get_directory_property(all_targets BUILDSYSTEM_TARGETS)

foreach(target IN LISTS all_targets)
  if(SYNERGY_SYCL_BACKEND STREQUAL hipSYCL)
    add_sycl_to_target(TARGET ${target})
  endif()
endforeach()