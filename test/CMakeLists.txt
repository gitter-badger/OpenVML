set(OpenVML_TESTSRC 
  vml_test.c 
  vml_util.c
  openvml_timer.c
  test_add.c
  test_sub.c
  test_pow.c
  test_exp.c
  test_tanh.c
  test_log10.c
  test_ln.c
  test_log1p.c
  test_floor.c
  )

set(OpenVML_TEST_NAME run_vml_test)

add_executable(${OpenVML_TEST_NAME} ${OpenVML_TESTSRC})

target_link_libraries(${OpenVML_TEST_NAME} ${OpenVML_LIBNAME})
target_link_libraries(${OpenVML_TEST_NAME} ${OpenVML_LIBNAME}_ref)

if(${CMAKE_SYSTEM_NAME} MATCHES "Linux")
  target_link_libraries(${OpenVML_TEST_NAME} rt)
endif()

add_test(${OpenVML_TEST_NAME} ${CMAKE_CURRENT_BINARY_DIR}/${OpenVML_TEST_NAME})


set(OpenVML_MISC_TEST_NAME misc_test)
add_executable(${OpenVML_MISC_TEST_NAME} vml_misc_test.c)
target_link_libraries(${OpenVML_MISC_TEST_NAME} ${OpenVML_LIBNAME})

add_test(${OpenVML_MISC_TEST_NAME} ${CMAKE_CURRENT_BINARY_DIR}/${OpenVML_MISC_TEST_NAME})