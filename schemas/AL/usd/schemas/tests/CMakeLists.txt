IF(DEFINED NO_TESTS AND NO_TESTS)
  message("Skipping test building.")
  return()
ENDIF()

find_package(GTest REQUIRED)

enable_testing()

add_executable(testMayaSchemas
    main.cpp
    testMayaSchemas.cpp
    )

target_include_directories(testMayaSchemas
    PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/../../../../../schemas
    ${GTEST_INCLUDE_DIRS}
    )

target_link_libraries(testMayaSchemas
    ${SCHEMAS_PACKAGE}
    ${GTEST_LIBRARIES}
    )

install(TARGETS testMayaSchemas DESTINATION bin)

add_test(TestAdditionalSchemas testMayaSchemas)
